# Chi_Rental_Market_Concentration

This repository holds the code to scrape all of Cook County's property tax records and match them based on their probable owners. 

This code is primarily written in R, thought there are chunks of sql which are used to back-up data to a PostgreSQL database and some chunks of python. This code also uses some large publicly available files, which I've linked to in the code rather than uploading.

Matching the properties is done using the properties' taxpayer name and mailing address. If properties A and B have the same owner, e.g. "ABC Holings", it is reasonable to assume that they are owned by the same company. If properties B and C have their mail sent to the same address, e.g. 1234 Corporate St, it is reasonable to assume they are owned by the same company. If A and B are owned by the same company and B and C are owned by the same company, then it follows that A and C are owned by the same company. Using this apporoach, it is possible to identify large groups of affiliated properties. This code uses the union find algorithm to efficiently map these sets.
