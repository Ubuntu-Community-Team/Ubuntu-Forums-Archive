---
title: "print to email"
date: 2009-02-17
forum: General Help
---

### Post by nrune on 2009-02-17
Need some help. 

I work at a hospital that has this stupid windows program  that is so crippled it is sad.


what i need is a box to receive a printed page and convert it into an email format.

all the pagers can receive email and display text.  the problem is getting a box to receive the print text and then email.

can anyone help me?

mike

my nurses would be greatful!

---

### Post by nrune on 2009-02-17
Okay now that I have slept on this idea, it occurs to me that this could be done in three steps. 

1. Cups recieves print text and saves a file instead of printing to paper. 

2. A program, not sure which one, converts the file into an email format removing extra text not needed.

3. Load the file as an email and then send via smtp.

Can cups do this automatically? 

Any ideas appreciated.

Mike

---

### Post by Macchi on 2009-11-09
I am working on a similar solution using CUPS-PDF. In the simplest form there is a ugly workaround: I create a PDF-printer, publish it. Then I create a share on the PDF catalog whre the pdf-files are created. In the next phase I am adding postprocessing on the /etc/cups/cups-pdf.conf to email the files. It will be ready within two minutes or maybe two weeks :-).
Regards,
/Macchi

---

