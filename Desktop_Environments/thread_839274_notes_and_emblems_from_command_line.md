---
title: "notes and emblems from command line"
date: 2008-06-24
forum: Desktop Environments
---

### Post by Mtuxland on 2008-06-24
Hi folks,
I was wondering to know if there is a way to add emblems and notes to a file from the command line interface.

With notes and emblems I mean the tags you can see right clicking on a file and clicking on "properties".

I know it's nautilus feature and that the notes are stored in a xml file in the .nautilus folder, but I'm unable to read/write those informations from bash.

Any ideas?

Thanks,
Marco

---

### Post by CalderCoalson on 2008-09-12
Emblem information is stored in the ~/.nautilus/metafiles directory.  Each directory containing files or folders with custom emblems gets its own file where
```
/path/to/directory/in/question
```
takes the form
```
file:%2Fpath%2Fto%2Fdirectory%2Fin%2Fquestion.xml
```
in other words, add 'file' to the beginning, and .xml to the end and then replace all forward slashes with '%2F' and you have the file name.

A typical file will look something like this, (I spaced it for ease of reading):
```
<?xml version="1.0"?>
<directory>
<file name=".stuff" timestamp="1220922624"/>
<file name="src" timestamp="1221256781">
        <keyword name="package"/>
</file>
<file name="Developer" timestamp="1221256989">
        <keyword name="distinguished"/>
</file>
</directory>
```

Now, notice that both folders within my home folder that has a custom emblem, (Developer and src), receives a <file> tag.  Inside that take, there is a <keyword> tag for each emblem applied to the file or folder.

I hope that helps a little...

---

### Post by corentin.barbu on 2011-11-02
Sorry for awaking the zombie, [CalderCoalson]("http://ubuntuforums.org/member.php?u=600089") gave an interesting answer but I have the same question and don't find files I have "noted" in this folder. Anywhere else I should search?

---

