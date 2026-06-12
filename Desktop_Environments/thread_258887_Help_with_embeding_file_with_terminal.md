---
title: "Help with embeding file with terminal"
date: 2006-09-16
forum: Desktop Environments
---

### Post by RedmondCooper on 2006-09-16
Greetings
A certain website was talking about embedding rar archives within jpeg files. They gave a tutorial on how to do this in windows. When I asked if this was possible with linux, a user who claimed to be running redhat stated that it did just change copy to cp. Here is the instruction posted on the site

[IMG]http://img108.imageshack.us/img108/4985/bsrc1158394786316ml2.gif[/IMG]

Anywho I made sure i was in the correct directory first. I'm able to copy regular files.
But when I run the command I get this output

```
:~$ cp /b sup.jpg + funny.rar output.jpg
cp: target `output.jpg' is not a directory

```

I also tried
```
:~$ cp /b sup.jpg + funny.rar output.jpg
cp: target `output.jpg' is not a directory
```

and
```
:~$ cp /b sup.jpg + funny.rar /home/redmond/output.jpg
cp: target `/home/redmond/output.jpg' is not a directory
```


Any thoughts? Am I doing something blindedly stupid? Feel free to laugh first 8-) 

All help is appreciated
Thankyou

---

### Post by daller on 2006-09-16
Why do you want to merge a rar-file with a jpeg image?

---

### Post by ayoli on 2006-09-16
yep strange idea. btw options for cp and other command never start with a / but with a -

---

### Post by RedmondCooper on 2006-09-16
the basic idea is that when you open the merged file when it has .jpg extension it shows as the copied image. But if you change the file to .rar you can extract the archive.  If I were to just change a regular a regular .rar to .jpg I would just get an eror message.

Also because I know I can do it in windows. Hence I want to know I can do it in linux.

---

### Post by RedmondCooper on 2006-09-16
well according to fsref.com/pr/dosxp.shtml
/B Indicates a binary file.

as opposed to bash 
-b, --backup make backup before removal

sooo that help at all?

---

### Post by RedmondCooper on 2006-09-19
Kerbump
[-o<

---

### Post by yashton on 2007-06-15
cat image1.jpg something.rar >> image2.jpg

From wikipedia under RAR.

cat con*cat*enates files. Takes em and smashes em together. As far as I understand the workings of this, the image should be first, as the program reading the image reads the image data at the beginning, then just ignores the end extra. Also works with zip files.

---

