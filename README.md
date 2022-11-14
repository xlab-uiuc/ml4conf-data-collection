# Kurator

A simple tool to collect data for machine learning models that help you write Kubernetes configurations.

## Setup

1. Install [Docker](https://docs.docker.com/install/)
2. `cp .env.example .env` and fill in the values.
3. Run `unzip -d kurator_backend kurator_backend/community-operators.zip` to unzip the community operators. If you don't run this, the first call to "validate" will take a long time.
4. Run `docker compose up --build` to start the server.

Data dumps are not stored in this repository. Fetch them from {secret location} and store it as `db/01_data_dump.sql` file. This data will only be loaded if `db/data` is empty. If you're trying to load new data, delete the `db/data` directory and run `docker compose up --build` again.

<!-- This simple app is for collecting data of the form: **(Existing Config, Change Instruction, New Config)**. Since making users enter this data from scratch is too expensive, this app helps in the following ways:

- It allows users to select existing configurations from a list of existing configurations.
- It allows users to edit existing configurations, and the app calls GPT-3 to generate change instructions.
- Since the generated change instructions are not always correct, the app allows users to edit the change instructions.

If a user makes changes to the change instruction, we flag the data sample as "edited" (along with recording the change instruction before the edit). This is useful for training a model with better change instructions.

The app has simple UI:

- There are 3 columns: Existing Config, New Config and Diff for easy visualization of the change.
- There's one row at the bottom for entering the change instruction. This will be automatically filled by GPT-3.
- Finally, one submit button to submit the data sample.
- Users can edit their data points if they want to.

The database schema is as follows:

Table: edit_data_points (stores the data points of the edit task)
- id: Primary key
- user_email: string
- existing_config: The existing configuration
- change_instruction: The change instruction
- new_config: The new configuration
- generated_change_instruction: The change instruction generated by GPT-3
- edited: Whether the change instruction was edited by the user

Table: existing_configs
- id: Primary key
- config: The existing configuration
- tag: The tag for the existing configuration -->
