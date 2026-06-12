---
title: "Scribus compatibility with Quark XPress"
date: 2006-06-25
forum: Desktop Environments
---

### Post by october1917 on 2006-06-25
Is there someone, who can surely answer if can i import .qxd and qxt files (created with Quark XPress) with Scribus?

Some people answer YES but more answer NO.
Is there anyone that have done it?

Thank you.

---

### Post by aysiu on 2006-06-25
From [Scribus' website](http://docs.scribus.net/index.php?lang=en&page=faq2): > **Why are there no import filters for Quark, Indesign or other commerical DTP applications?**

There are several reasons why there are no import filters for commercial DTP applications.

   1. DTP file formats are very complex internally - problably the most complex on a PC. Creating import/export filters is a task far more complex than importing a spreadsheet or simpler word processing file formats. An engineer familiar with the internal file format of Pagemaker compared it to a 2m x 3m flow chart diagram with 6 point type. It was not until the arrival of Indesign 2.0 that reliable Pagemaker file import was possible in another DTP application, even though Adobe had the file format specs. Note: Not even Indesign CS can save to Indesign 2.0 format.
   2. The file formats are sometimes protected by patents and are not documented publically.
   3. So, is it unethical/illegal to apply hexedit to an InDesign file to reverse engineer the file format with hexedit or others for the purpose of creating the export/import plugins for Scribus?
      Possibly not, but given its a closed format we would expect to receive a warning from Adobe, as we did from Quark when there was a Quark importer in testing. We do not have the legal resources to challenge large proprietary software companies. Only one developer has been sucessful at reverse engineering Quark's software and it took a long legal case to succeed.
   4. Developer constraints. It is the considered judgement of the development team that efforts to improve Scribus is a more valuable use of time.


---

### Post by october1917 on 2006-06-26
Thank you my friend.

---

