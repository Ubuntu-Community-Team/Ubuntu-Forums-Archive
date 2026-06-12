---
title: "Pdf -&gt; txt?"
date: 2009-06-02
forum: General Help
---

### Post by jamesbeat on 2009-06-02
I have just invested in a Sony PRS 505 ebook reader.
It's a really nice piece of kit, but unfortunately the PDF functionality is somewhat lacking.

I need a method to convert PDF's into plain text. I know I can do this by opening the PDF file and copying the text into an empty file or whatever, but the problem is that I have a LOT of PDF's!

Is there a way to do a batch conversion so that I can just point it at a folder and convert all of the PDF's within into plain text?

---

### Post by kaibob on 2009-06-02
> **jamesbeat said:**
> ...I need a method to convert PDF's into plain text. I know I can do this by opening the PDF file and copying the text into an empty file or whatever, but the problem is that I have a LOT of PDF's!

Is there a way to do a batch conversion so that I can just point it at a folder and convert all of the PDF's within into plain text?

The pdftotext command-line utility will do what you want. To batch convert all pdf files in a directory, you would probably want to use a shell script. Let us know if you would like help with this.

[http://linuxcommand.org/man_pages/pdftotext1.html](http://linuxcommand.org/man_pages/pdftotext1.html)

---

### Post by jamesbeat on 2009-06-02
Yes please :)
I'm very much a n00b, I'm not even sure what a shell script is...

EDIT: Is it possible to include subdirectories too?

---

### Post by jamesbeat on 2009-06-02
I tried the script here: [http://en.wikipedia.org/wiki/Pdftotext](http://en.wikipedia.org/wiki/Pdftotext)

```
$ for f in *.pdf
> do
>   pdftotext $f
> done

```

but it just seems to launch pdftotext several times without actually doing anything, ie when I check the folder that I execute the scrip in, there are no new text files inside.

---

### Post by kaibob on 2009-06-02
First, you need to verify that pdftotext is installed. To do this, open a terminal window and type pdftotext. You should receive some usage notes. If not, install the poppler-utils, which include the pdftotext utility. Poppler-utils is in the repo's and can be installed with the Synaptic Package Manager.

Next, you need to run a test to see if the converted text document meets your needs. Select a PDF file for this test. Then, open a terminal window, change to the directory that contains the test PDF, and run the following command. You will need to change input.pdf to the name of your test PDF.

```
pdftotext -layout input.pdf output.txt
```

View the resulting text file to see if it meets your needs. If it doesn't, rerun the command without the -layout option. Let us know how this works. 

BTW, the shell script is the easy part of this, and it can be made to work recursively.

---

### Post by stewiefet on 2009-07-11
I'm having the same problem with the shell script.. pdftotext doesn't seem to recognise $f as passing it a valid filename if the filename has spaces.   Any suggestions?

---

### Post by kaibob on 2009-07-11
Try the following in a terminal window. It works fine with file names that contain spaces.

```
for file in *.pdf ; do pdftotext -layout "$file" ; done
```

The earlier shell script did not quote the variable $f.

---

### Post by stewiefet on 2009-07-11
Oh for crying out loud.
 
Obvious Answers : 1  Stewart : 0
 
Thanks Kaibob.

---

### Post by mediax on 2009-07-28
I know this is a bit late, but I find Calibre terrific with my Reader.

I ocnvert most of my files to lrf format, which seems to reflow a lot better.

---

### Post by alphahun on 2009-10-31
> **kaibob said:**
> Try the following in a terminal window. It works fine with file names that contain spaces.

```
for file in *.pdf ; do pdftotext -layout "$file" ; done
```

The earlier shell script did not quote the variable $f.

Your solution is great. Thank you very much kaibob.

---

