---
title: "Can't find this elsewhere, Wine question"
date: 2006-02-08
forum: Desktop Environments
---

### Post by n8ey on 2006-02-08
I have a fully functional Windows 98 install.  I installed Wine and it said that it detected the Windows 98 installation, but it's mapping to the home folder "./wine/drive_c" and not to my mounted Windows drive.

I can't tell if it's using the Windows dlls or the Wine dlls either...

Is getting Windows and Wine together as easy as renaming them drive-folders to "_old" (or something) and creating a new symlink, or is there more to it?

Any help is appreciated, my brain is beginning to ooze outta my ears regarding this puzzle.

---

### Post by dcstar on 2006-02-08
[QUOTE=n8ey]I have a fully functional Windows 98 install.  I installed Wine and it said that it detected the Windows 98 installation, but it's mapping to the home folder "./wine/drive_c" and not to my mounted Windows drive.

I can't tell if it's using the Windows dlls or the Wine dlls either...

Is getting Windows and Wine together as easy as renaming them drive-folders to "_old" (or something) and creating a new symlink, or is there more to it?

Any help is appreciated, my brain is beginning to ooze outta my ears regarding this puzzle.[/QUOTE]
Run winecfg, you should see your real Windows "C" drive listed under another letter (assuming it has been mounted in your /etc/fstab file).

---

### Post by n8ey on 2006-02-08
Okay, I went to the drives section and it showed the two default drives - C:\ and Z:\.

C:\ = ~/.wine/drive_c
Z:\ = /

I couldn't add them.

On a whim, I re-launched it with sudo and it had an auto-detect button.  I ran that and now it shows a mess of drives, with my Windows98 partition as drive E:\

I can't find a way to change the drive letter...

I'll keep digging, but if anyone has any ideas I welcome your input.  (Thank you David.)

---

### Post by n8ey on 2006-02-09
I think I figured my difficulty out.  I've been reading the Wine documentation and I was misled by a passage that said that Wine could use native dlls if Windows 98 was installed.

So I guess my question/difficulty has refined.

I mainly need to have ActiveX in Internet Explorer for work purposes.  I got Internet Explorer 6 installed, but I cannot get the ActiveX controller to install and work.  What are the ways to find the errors and figure out what to copy and where?

---

### Post by n8ey on 2006-02-09
I found it - I just kept an eye on the terminal and found an error about "mfc42.dll" - which in a windows install is located in "C:\Windows\system\".

I copied it from my Windows install into the wine "windows/system" directory and "rebooted" with "wineboot".

Now it works.

---

### Post by outofnicks on 2006-02-09
If you don't mind me hijacking your thread, I have a simple question about Wine:
Do you need a Windows install on another partition or drive to be able to use Wine?
Or is just Wine itself on Linux sufficient to run, for example, Internet Explorer?
Thanks.

---

### Post by n8ey on 2006-02-09
You do not need an install of Windows to run wine.  But it can come in handy for .dll issues like I had.

The weird part of wine is that it doesn't automagically install things like Internet Explorer, it installs the windows kernel, notepad, solitaire - i.e. the bare essentials.

You'll need to install the rest.

I used IE4Linux installation script and Sidenet and it's working fine.  So far.  ;)

---

### Post by outofnicks on 2006-02-09
Appreciate the quick reply :) 
I'm a web developer on a Mac, so will want IE to check out sites--happy to hear I won't need Windows! But may get W98 anyway. Haven't even started yet, still waiting for Ubuntu CDs in the mail--it will be a while :cry:

---

