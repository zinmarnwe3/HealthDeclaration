Health Declaration

![image](https://github.com/zinmarnwe3/HealthDeclaration/assets/127071104/665ce7cb-4c37-4355-9bba-ffc1bc1a0199)

```
CREATE TABLE FormTemplate (
    TemplateID INT PRIMARY KEY,
    TemplateName VARCHAR(100),
    -- Additional columns for template details if needed
);
```
```
CREATE TABLE FormField (
    FieldID INT PRIMARY KEY,
    TemplateID INT,
    FieldLabel VARCHAR(100),
    FieldType VARCHAR(50),
    -- Additional columns for field details if needed
    FOREIGN KEY (TemplateID) REFERENCES FormTemplate(TemplateID)
);
```
```
CREATE TABLE FilledForm (
    FormID INT PRIMARY KEY,
    TemplateID INT,
    FilledBy VARCHAR(100),
    FilledDate DATETIME,
    -- Additional columns for form details if needed
    FOREIGN KEY (TemplateID) REFERENCES FormTemplate(TemplateID)
);
```
```
CREATE TABLE FormFieldValue (
    FieldValueID INT PRIMARY KEY,
    FormID INT,
    FieldID INT,
    Value VARCHAR(MAX),
    -- Additional columns for field value details if needed
    FOREIGN KEY (FormID) REFERENCES FilledForm(FormID),
    FOREIGN KEY (FieldID) REFERENCES FormField(FieldID)
);
```
