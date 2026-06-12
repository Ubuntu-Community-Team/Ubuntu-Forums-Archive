---
title: "Unable to open zip file..why?"
date: 2009-03-07
forum: General Help
---

### Post by mirkko22 on 2009-03-07
Hi all

I would like open a normal and small zip file located on my admin website..I can download or receive that zip by email...When I try to open using ubuntu i get a error..I have try with 2 different software without success. I have also try using WindowXP (installed on ubuntu via VirtualBox) with same result...If I try to open that zip file from another computer without Ubuntu I can open the archive without problem...

any suggestion ? Why I get this issue ??

thanks in advance

---

### Post by martrn on 2009-03-07
In ubuntu open a terminal and type

```
unzip -t thatzipfile.zip
```

and put the results from that output you get here.

---

### Post by dcstar on 2009-03-07
> **mirkko22 said:**
> Hi all

I would like open a normal and small zip file **located on my admin website**..I can download or receive that zip by email...When I try to open using ubuntu i get a error..I have try with 2 different software without success. I have also try using WindowXP (installed on ubuntu via VirtualBox) with same result...If I try to open that zip file from another computer without Ubuntu I can open the archive without problem...

any suggestion ? Why I get this issue ??

thanks in advance

And perchance did you upload the file using FTP in Ascii mode?

---

### Post by mirkko22 on 2009-03-09
thanks to all...

In fact when trying to open archive in command line I don't get problem (am newbie with linux and command line)..and my file are correctly deflated...I have try to open with default archive software of Ubuntu and also with Xarchiver.,...without success..

Default software tell me the follow error:

warning:  stripped absolute path spec from /
mapname:  conversion of  failed


No the archive are not uploaded...it is a server generated archive of sql database...

cheers

---

### Post by karlr42 on 2009-03-09
What is the name of the file?

---

### Post by mkvnmtr on 2009-03-09
One of the first things I do when I do an install of Ubuntu is go to the package manager and in the search box type in zip and then rar. I go through and install every program that looks like it might help me open and work with these type of files. There are several. Then I never seem to have problems double clicking on a file unless it is password protected. In that case I type in crack and look for a program that will crack passwords on that type of file.

---

