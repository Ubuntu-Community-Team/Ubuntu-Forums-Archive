---
title: "How can I modify my openoffice.org Word Procesor to?"
date: 2009-06-18
forum: General Help
---

### Post by BSG Fan on 2009-06-18
Hello
a question:
How can I modify my openoffice.org Word Processor to PDF format?

My Ubuntu already is set to save the documents in Microsoft Word 97/2000 (.doc) format.
I need tu upload the files electronically to "PDF"

How can I do that?

another question, although just for curiosity:
How can I reverse from PDF to doc?

---

### Post by hibliss on 2009-06-18
Go to print when you are finished with editing the document and select print to file. You will have the option of selecting PDF. 

As far as PDF back to Word, there are plenty of converters. Sometimes fonts are not recognized, and a lot of text boxes and formatting will be lost in the conversion.

There are PDF editors, like this one -- [http://www.getdeb.net/app.php?name=PDF+Editor]("http://www.getdeb.net/app.php?name=PDF+Editor"), your mileage will vary.

---

### Post by BSG Fan on 2009-06-18
> **hibliss said:**
> Go to print when you are finished with editing the document and select print to file. You will have the option of selecting PDF. 

==========
Hey, HiBliss:
I did it!
Thanks a lot! 

As far as PDF back to Word, there are plenty of converters. Sometimes fonts are not recognized, and a lot of text boxes and formatting will be lost in the conversion.

There are PDF editors, like this one -- [URL="http://www.getdeb.net/app.php?name=PDF+Editor"]http://www.getdeb.net/app.php?name=PDF+Editor[/URL, your mileage will vary.

 u rock.
thanks for ur quick answer
=)

---

### Post by BSG Fan on 2009-06-18
I was long time away from the forum...
How I give "the thanks" here?
I don't see any feature for...
;)

---

### Post by hibliss on 2009-06-18
I think your thanks was plenty for me. Enjoy.

---

### Post by coffeecat on 2009-06-18
You can use print to pdf as hibliss suggests, but OpenOffice has another way as well. In Open Office, simply go to File > Export as PDF.

---

### Post by BSG Fan on 2009-06-18
> **hibliss said:**
> I think your thanks was plenty for me. Enjoy.

Hey, my friend:
The last time I was here there was a blue ribbon in the bottom right of the page.... but I don't find it now; that was what I meant, hehe.

Thanks u again
:)

---

### Post by BSG Fan on 2009-06-18
> **coffeecat said:**
> You can use print to pdf as hibliss suggests, but OpenOffice has another way as well. In Open Office, simply go to File > Export as PDF.

Hello Coffecat:
Thanks a lot for ur answer.
That's the best effective way to save only.

Have a wonderful Ubuntu day
=)
:D

---

### Post by ugm6hr on 2009-06-19
Be aware that the Export to PDF does not work 100% reliably from OO.org.

Specifically, Base forms with query results in them sometimes export without the query results etc.

In this situation, I print from OO.org, selecting the "Print to File" box, and save the file as a .ps file (postscript).

Then, you have to manually (with Terminal) convert to PDF:
```
ps2pdf filename.ps
```

This creates a new file as filename.pdf

The main difference is that this creates a large graphical PDF, rather than one with text, so is often a larger file.

---

### Post by BSG Fan on 2009-06-19
> **ugm6hr said:**
> Be aware that the Export to PDF does not work 100% reliably from OO.org.

Specifically, Base forms with query results in them sometimes export without the query results etc.

In this situation, I print from OO.org, selecting the "Print to File" box, and save the file as a .ps file (postscript).

Then, you have to manually (with Terminal) convert to PDF:
```
ps2pdf filename.ps
```

This creates a new file as filename.pdf

The main difference is that this creates a large graphical PDF, rather than one with text, so is often a larger file.

Hello, ugm6hr:
I am a little confused.  I want the PDF to convert one document to PDF to one office in the government.
The setting sof my openoffice.org Word Processor now are to save in word/Windows.
I am not good in that area of entering codes in the terminal...
when I am supposed to enter that code?
Now, and that's it? or everytime I convert
Lol, I am confused
=)

---

### Post by ugm6hr on 2009-06-19
If you are using OO Writer only, then I think your best option is as detailed above, using the "Export as PDF" menu option.  This has never failed to work for a document created within Writer.

The reason Writer does not offer to save as PDF as a default is because you cannot (easily) go back and edit a PDF once created.

I gave the alternative solution above for people who need to create a PDF from a Writer document created within OO Base (the database program).  The Terminal command given is required to convert 1 file from PS to PDF, so needs to be run for each document you create.  However, **if you only create text documents within Writer, you should not need to use this**. "Export as PDF" remians your best option.

---

### Post by BSG Fan on 2009-06-19
> **ugm6hr said:**
> If you are using OO Writer only, then I think your best option is as detailed above, using the "Export as PDF" menu option.  This has never failed to work for a document created within Writer.

The reason Writer does not offer to save as PDF as a default is because you cannot (easily) go back and edit a PDF once created.

I gave the alternative solution above for people who need to create a PDF from a Writer document created within OO Base (the database program).  The Terminal command given is required to convert 1 file from PS to PDF, so needs to be run for each document you create.  However, **if you only create text documents within Writer, you should not need to use this**. "Export as PDF" remians your best option.

=====

ugm6hr:
Man, you rock!
Thanks for your help.  I now finally understand.
Have a wonderful weekend
=)
:popcorn:

---

### Post by donkyhotay on 2009-06-19
> **BSG Fan said:**
> Hey, my friend:
The last time I was here there was a blue ribbon in the bottom right of the page.... but I don't find it now; that was what I meant, hehe.

Thanks u again
:)

That feature has been temporarily removed due to instabilities with the server. It's hoped it will be added back but for now just post thanks in the thread.

---

### Post by BSG Fan on 2009-06-19
> **donkyhotay said:**
> That feature has been temporarily removed due to instabilities with the server. It's hoped it will be added back but for now just post thanks in the thread.

Ohhh, thanks u for the information
=)):P

---

