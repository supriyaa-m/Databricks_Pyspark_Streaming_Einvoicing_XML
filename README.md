# Real-Time Streaming E-Invoicing Platform

The project involves building a real-time streaming e-invoicing platform that processes incoming input files to generate XML invoices. The workflow consists of several key stages:

XML Generation: Incoming input files are used to generate XML files, which represent the e-invoices.

Validation: The generated XML files undergo validation against predefined XML Schema Definitions (XSDs). If an XML file does not meet the validation criteria, it is rejected. In such cases:

An email notification is triggered, detailing the reasons for rejection.
The rejected XML data is logged into a reject audit table for record-keeping and further analysis.

Staging: Valid XML files are moved to a staging location for further processing.

Parsing and Loading: The XML files in the staging area are parsed, and their contents are loaded into three distinct tables:

Invoice Data Table: Stores customer-related data.

Invoice VAT Table: Contains VAT (Value Added Tax) details.

Invoice Line Table: Holds line item details, such as individual products or services listed on the invoice.

Archiving: Once the XML files are successfully parsed and loaded into the respective tables, they are archived by moving them to a designated archive location. This step ensures that the processed files are stored securely for future reference or audit purposes.

Aggregation and Loading: The final step involves aggregating the data from the staging tables based on account numbers. The aggregated data is then loaded into two tables:

Total VAT Table: Summarizes the total VAT amounts per account number.

Total Invoice Line Table: Aggregates the total number of line items per account number.

This platform ensures efficient, real-time processing of e-invoices, with robust validation, auditing, and aggregation mechanisms in place. The architecture supports seamless integration with external systems and provides comprehensive reporting and archival capabilities.
