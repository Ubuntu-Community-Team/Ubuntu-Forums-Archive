---
title: "Installing Adobe Reader in Oprea?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by lex on 2006-01-12
I tried to follow the instruction on how to install Adobe Reader form "[COLOR="Magenta"]http://www.opera.com/linux/docs/plugins/install/#acrobat[/COLOR]" but i had no joy. I was able to download the program and find it in a terminal. This is where the trouble starts "[COLOR="Blue"]Enter installation directory for Adobe Reader 7.0.5 [/usr/local/Adobe/Acrobat7.0][/COLOR]". I don't know anything about what directories, let alone which one to put it in.
This is what I have done "[COLOR="Magenta"]lex@ubuntu:~/DOWNLOADS$ tar -xzvf AdobeReader_enu-7.0.5-1.i386.tar.gz
AdobeReader/
AdobeReader/ILINXR.TAR
AdobeReader/COMMON.TAR
AdobeReader/LICREAD.TXT
AdobeReader/INSTALL
AdobeReader/ReadMe.htm
lex@ubuntu:~/DOWNLOADS$ AdobeReader/INSTALL

This installation requires 95 MB of free disk space.

Enter installation directory for Adobe Reader 7.0.5 [/usr/local/Adobe/Acrobat7.0][/COLOR]".

Then I tried this for a directory, " /usr/lib/opera/plug-ins/"[COLOR="Navy"][/COLOR]
This is what happened "[COLOR="Magenta"]Enter installation directory for Adobe Reader 7.0.5 [/usr/local/Adobe/Acrobat7.0] /usr/lib/opera/plug-ins/

Directory "/usr/lib/opera/plug-ins/" does not exist.
Do you want to create it now? [y]  y
mkdir: cannot create directory `/usr/lib/opera/plug-ins': Permission denied

ERROR: Cannot make directory "/usr/lib/opera/plug-ins/".

Enter installation directory for Adobe Reader 7.0.5 [/usr/local/Adobe/Acrobat7.0][/COLOR]"

Can anyone please give me some simple directions.
Thanks
Lex:rolleyes:

---

### Post by Ampersand on 2006-01-12
Try putting 
```
sudo AdobeReader/INSTALL
```

---

### Post by lamego on 2006-01-12
It looks like you are install the full acrobat reader,
if is not very wise to install it to /usr/lib/opera/plug-ins/  .
Install it somewhere else (the default should be ok) and then just copy or link the plugin  .

---

### Post by lex on 2006-01-13
[QUOTE=Ampersand]Try putting 
```
sudo AdobeReader/INSTALL
```[/QUOTE]
Worked a treat thanks.
Lex

---

