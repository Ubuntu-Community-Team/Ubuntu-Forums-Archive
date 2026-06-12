---
title: "PDF Password cracking."
date: 2009-01-07
forum: General Help
---

### Post by rob2nd9th on 2009-01-07
First - I have bought 4 e-books two are on adode digital no problems, how ever two are not. I have emailed the company but have found all 4 pdf's but they are locked.
have tried pdfcrack and get
   
"The specific version is not supported (EBX_HANDLER - 0)"

Also I have know idead how to use ImageMagick? it shows up at installed on synaptic  but when ran in terminal - bash: imagemagick: command not found

Any help or pointers thanks.

(Ubuntu 8.10)

---

### Post by mcduck on 2009-01-07
If you first use pdf2ps to convert the PDF document to Postscript, and then use ps2pdf to convert it back int PDF the passwords protection should disappear.

For Imagemagick, while the program is called Imagemagick it's actually a collection of separate programs for different purposes, and none of these programs is called "imagemagick". Most common tasks are done using "convert"- or "mogrify"-commands.

[http://www.imagemagick.org/script/command-line-tools.php]("http://www.imagemagick.org/script/command-line-tools.php")
[http://www.imagemagick.org/Usage/]("http://www.imagemagick.org/Usage/")

---

### Post by rob2nd9th on 2009-01-07
> **mcduck said:**
> If you first use pdf2ps to convert the PDF document to Postscript, and then use ps2pdf to convert it back int PDF the passwords protection should disappear.

For Imagemagick, while the program is called Imagemagick it's actually a collection of separate programs for different purposes, and none of these programs is called "imagemagick". Most common tasks are done using "convert"- or "mogrify"-commands.

[http://www.imagemagick.org/script/command-line-tools.php]("http://www.imagemagick.org/script/command-line-tools.php")
[http://www.imagemagick.org/Usage/]("http://www.imagemagick.org/Usage/")

pdf2ps ?? how would I do that. thanks for the imagemagick - tried 

convert /home/*****/*****/A_Storm_of_Swords.pdf A_Storm_of_Swords.odt
   **** This file uses an unknown security handler.
   **** The file was produced by: 
   **** >>>> =<e&#65533;&#65533;&#65533;&#65533;Ux_X&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#963;&#65533;&#65533;&#65533;&#65533;X&#569; <<<<
Error: /undefined in pdf_process_Encrypt
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   --nostringval--   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1156/1684(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:106/127(ro)(G)--   --dict:275/300(ro)(G)--   --dict:18/25(L)--
Current allocation mode is local
GPL Ghostscript 8.63: Unrecoverable error, exit code 1
convert: Postscript delegate failed `/home/rob/Desktop/A_Storm_of_Swords.pdf': No such file or directory.
convert: missing an image filename `A_Storm_of_Swords.odt'.


Is there another way???

Sorry to be a pain - Thanks anyway for the fast reply

---

### Post by donkyhotay on 2009-01-07
Assuming there isn't anything unusual it should be a simple
```
pdf2ps ./input.pdf ./output.ps
```
you might want to also do
```
man pdf2ps
```
for more information on using that program.

---

### Post by PGScooter on 2009-01-07
pdf2ps is a program, so you need to run it from the command line. Try something like ```
 pdf2ps yourpdffile.pdf youroutputfile.ps 
```

If you don't have pdf2ps installed, you have to install it

---

### Post by Slim Odds on 2009-01-07
Come on dudes. If it's password protected pdf2ps is **NOT** going to be able to read it.

---

### Post by rob2nd9th on 2009-01-07
sudo apt-get install pdf2ps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pdf2ps

?? or am I missing something (Sorry still a newbe)

---

### Post by rob2nd9th on 2009-01-09
Sorry to bump this :redface:

---

### Post by stinger30au on 2009-01-09
a quick goole search found this

[http://www.crackpdf.com/](http://www.crackpdf.com/)


should run in wine

---

### Post by donkyhotay on 2009-01-09
> **Slim Odds said:**
> Come on dudes. If it's password protected pdf2ps is **NOT** going to be able to read it.

There are two different types of passwords PDF's can have on them. There are the encryption passwords that prevents you from even reading them, I don't know how to bypass these. Then there are the editing passwords which allow you to read them but prevent you from editing them. These can by bypassed pretty easily by most open source PDF viewers and the passwords themselves can be removed by converting to postscript and back again (per the previous posts). I was under the impression he was having problems with the second type of password but I could be wrong.

---

### Post by Slim Odds on 2009-01-10
> **donkyhotay said:**
> There are two different types of passwords PDF's can have on them. There are the encryption passwords that prevents you from even reading them, I don't know how to bypass these. Then there are the editing passwords which allow you to read them but prevent you from editing them. These can by bypassed pretty easily by most open source PDF viewers and the passwords themselves can be removed by converting to postscript and back again (per the previous posts). I was under the impression he was having problems with the second type of password but I could be wrong.

Understood, I assumed that it was the encrypted variety.

---

### Post by rob2nd9th on 2009-01-14
Sorry for not being clear, I cant open them full stop.

---

