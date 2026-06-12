---
title: "Adobe only PDF file???"
date: 2009-02-22
forum: General Help
---

### Post by Olnex on 2009-02-22
Hello, when I was doing my research project, I googled to find a PDF file:

[http://www.aonix.com/pdf/j2sej2meemb_e.pdf]("http://www.aonix.com/pdf/j2sej2meemb_e.pdf")

when I opened it using evince, it shows a big block in every page that the file can be only opened by Adboe Reader, but when I used mouse to select the text, the text underneath the block is visible, although this is annoying, but later the file closed automatically, I'm not sure if it closes itself or there is some compatibility problem.

Do I really need to install adobe reader to read the file? I don't like having several applications for the same task.

---

### Post by stalkingwolf on 2009-02-22
you might have to install adobe.  I have never had this problem,
but maybe im lucky.

It is available in Synaptic.

---

### Post by ju2wheels on 2009-02-22
Seems like its an Adobe specific pdf thats password protected:

```

pdftk j2sej2meemb_e.pdf cat output real.pdf
Error: Failed to open PDF file: 
   j2sej2meemb_e.pdf
   OWNER PASSWORD REQUIRED, but not given (or incorrect)
Errors encountered.  No output created.

```

---

### Post by kaibob on 2009-02-22
> **Olnex said:**
> Do I really need to install adobe reader to read the file? I don't like having several applications for the same task.

I downloaded the PDF document in question, and it is as you describe. I don't have a good solution, but one that might be tried as a last resort is to use the pdftotext command-line utility. This converts the PDF document to plain text, but the text document is readable and does retain the tables in a usable format.

```
pdftotext -layout j2sej2meemb_e.pdf output.txt
```

Pdftotext is part of the poppler-utils. If it's not already on your computer, it's a small install with synaptic.

If you run into PDF documents like this often, installing Adobe Reader may be your best option. Or, perhaps another forum member will have a better solution.  

I have included a screenshot of the first page of the document just for informational purposes.

---

