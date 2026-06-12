---
title: "Can't run Linux Mugen!"
date: 2010-02-14
forum: Gaming &amp; Leisure
---

### Post by jahgamer189x on 2010-02-14
I downloaded it to my desktop and extracted it and typed ./mugen in terminal but it came up with:
bash: ./mugen: Permission denied
Help please!?

---

### Post by themusicalduck on 2010-02-14
Try ```
sudo chmod +x mugen
``` while you are still in the same directory the binary is in.

---

### Post by jahgamer189x on 2010-02-14
When I type that and press enter it asks for my password which I type and then nothing happens.

---

### Post by themusicalduck on 2010-02-14
Did you try running it again with ./mugen? That command just changes the permissions on the file and allows it to be run as an executable.

---

### Post by jahgamer189x on 2010-02-14
Yep, that doesn't work either.

---

### Post by themusicalduck on 2010-02-14
Ok, just locate the folder on your desktop using the file browser. Right click on the binary and select properties. On the permissions tab, see if "Allow executing file as a program" is checked.

Also, check that your username is listed as the owner and the group and that you at least have read access.

---

### Post by jahgamer189x on 2010-02-14
Allow executing of a program was and is checked and I am listed as the owner and I have read access.

---

### Post by themusicalduck on 2010-02-14
When you tried to run it again did you get the same permissions error?

I found the same program and downloaded it. I can run it without any problems with permissions. Just double clicking the binary will make it run or running it from the terminal.

It's possible the download is corrupted, so you could try downloading a new copy. Otherwise there might be a wider problem with permissions somewhere, but I can't really help with that.

---

### Post by jahgamer189x on 2010-02-14
I didn't get the permissions error, but still nothing happened. Also, the binary file wont even open or do anything when I double click it. BTW, I got my Linux Mugen from randomselect.piiym-net.com/

The one on Mugenation doesn't work because once I extract it, another tar file is produced which provides an error when extracted.

Winmugen and the latest version of Wine doesn't work either!

I guess you could say I'm just having a load of bad luck! :P
Thanks for all of your help anyway!

---

### Post by themusicalduck on 2010-02-14
I had that problem with the file producing another tar as well! But using this command on the file allowed it to extract properly - ```
tar jxvf LinuxMugen.tar.bz2.bz2
``` (Or replace LinuxMugen.tar.bz2.bz2 with whatever the file name is)

If you can get it to extract then that copy might work better.

---

### Post by jahgamer189x on 2010-02-15
Entering that doesn't work it says:
tar: LinuxMugen.tar.bz2.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

When the file is called 'LinuxMugen.tar.bz2.bz2'

EDIT: Wait, I pointed the terminal to where the tar file was located and it extracted correctly. It produced a mugen folder in the home folder. I tried to run it but again nothing happened. It didn't matter if I double clicked it or ran it by using the terminal. It still didn't do anything. And yes the allow executing of file thing was checked.

---

### Post by jahgamer189x on 2010-02-16
Apologies for the double post but it now works just by double clicking on it! I went to sleep last night (obviously) so the computer was completely shut down. I turned it on again this morning and just thought I'd try it. Turns out it worked perfectly! Thanks for all of your help anyway, but it works now so yay!

---

