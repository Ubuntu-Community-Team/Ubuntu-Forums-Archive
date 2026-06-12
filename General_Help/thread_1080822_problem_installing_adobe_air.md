---
title: "problem installing adobe air"
date: 2009-02-25
forum: General Help
---

### Post by geoffDeGeoffGeoff on 2009-02-25
I downloaded the linux installer for adobe air from [http://get.adobe.com/air/](http://get.adobe.com/air/)

I chmod + x the file

Then run it as sudo.

It just fails silently.  There are loads of reports of people on the web installing this successfully on 8.10 so I dont understand why it doesn't work for me.

Would it write an error message anywhere?  If so where?

Has anybody else had the same problem or does anybody know how to fix it?

Thanks in advance

---

### Post by zeronothing on 2009-02-25
Is this your first time installing Adobe Air? I had problems updating Adobe Air from one version to the next. The problem was, when you actually install Adobe Air, Synaptic keeps track of the install even though it is not a .deb package. so what I had to do is do an uninstall of everything Adobe Air with synaptic to install the newest version of Adobe Air. If I remember all I did to install Adobe Air was give the download file execute privilege. then just double click on the file and when it goes to run it uses the gksudo (I believe) to run the install as superuser.

---

### Post by geoffDeGeoffGeoff on 2009-02-26
this is the first time i have installed it on a reasonably recent fresh install of 8.10.  I had it working on heron but formatted all my drives.

:confused:

---

### Post by kshane on 2009-03-07
I, too, am unable to install Adobe AIR.  

```

~$ sudo sh AdobeAIRInstaller.bin
AdobeAIRInstaller.bin: 1: Syntax error: "(" unexpected

```

Any one know what's wrong?  I'm lost.  I need to install Adobe AIR to run a Twitter app.

Kevin

---

### Post by nyiti on 2009-03-25
I'm also having problems: Adobe AIR 1.5.1 installs all right, but when I try to install any air app, it throws segmentation fault.

No errors or anything. The file browser opens, I select the .air, the installer windows pops up for a moment but instantly segfaults. 

The same results for TweetDeck and Twhirl, so it's not the apps. I guess the AIR installer should be ok as well, the bug may be somewhere in the system settings, env. variables or something?

---

