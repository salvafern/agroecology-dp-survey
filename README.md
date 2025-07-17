## Agroecology data package: Survey data

Recommendations for organizing survey data in the Agroecology partnership. Typically, survey data from questionnaires includes a mix of **closed** (structured) and **open** (free-text) questions.

To keep it organized and FAIR-aligned:

- Questions are defined in a separate metadata file and **identified by unique IDs**
- Respondents are **anonymized**, and their basic information is stored in a separate file

```
.
├── respondents.csv        # Anonymized respondent metadata
├── questions.csv          # Metadata about all questions (IDs, text, type)
├── responses.csv          # Structured responses to questions
└── README.md              # Explanation of the structure and contents
```

**`respondents.csv`**

| participant_id | consent | timestamp            |
| -------------- | ------- | -------------------- |
| 001            | yes     | 2025-06-30T10:32:00Z |
| 002            | yes     | 2025-06-30T10:38:12Z |

**`questions.csv`**

| question_id | question_text                            | question_type  | answer_type | options           | cardinality |
| ----------- | ---------------------------------------- | -------------- | ----------- | ----------------- | ----------- |
| Q1          | What is your age?                        | single numeric | integer     | NA                | 1..1        |
| Q2          | What is your gender?                     | single choice  | string      | female;male;other | 1..1        |
| Q3          | How satisfied are you with the platform? | single choice  | integer     | 1;2;3;4;5         | 1..1        |
| Q4          | What would you improve in the platform?  | open text      | string      | NA                | 0..1        |

**`responses.csv`**

| respondent_id | question_id | answer                                  |
| ------------- | ----------- | --------------------------------------- |
| 001           | Q1          | 34                                      |
| 001           | Q2          | female                                  |
| 001           | Q3          | 4                                       |
| 001           | Q4          | I think the platform is user-friendly   |
| 002           | Q1          | 29                                      |
| 002           | Q2          | male                                    |
| 002           | Q3          | 5                                       |
| 002           | Q4          | Needs better support for collaboration. |

### Fields ontology

The fields of this data structure should be aligned to The Survey Ontology, in order to faciliate a later inclusion of these data into a knowledge graph with other open linked data. Some examples are: 

* participant_id = https://w3id.org/survey-ontology#participantId

* timestamp = https://w3id.org/survey-ontology#hasCompletionTimestamp