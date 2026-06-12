---
title: "WBM &amp; GRUB not resetting"
date: 2011-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xytheron on 2011-02-16
Hey all!
First time poster long time reader here!

Sooo I installed Ubuntu and in turn Grub to make myself a dual boot system between Ubuntu and Windows 7 64bit on a Dell Latitude D830. I realized I didn't like my install and wanted to clean everything out and start over so I uninstalled but now whenever I boot up I am presented with Windows Boot Manager and an option for:
Windows 7
Ubuntu
Grub

I went all bootsect.exe in repair mode on it but I can't get the screen to go away. What can I do to restore the proper bootup procedure before I move forward with a reinstall?

Namaste,
-Ray-

---

### Post by quixote on 2011-02-17
I haven't used Windows in years, so this is all a bit theoretical, but bootrec.exe is supposed to fix the issues you're talking about.  Is that what you used?  I haven't heard of bootsect.exe.  Maybe that's not the right program for the job?

There's a Msoft support page that goes through the various options of bootrec.exe in detail: [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392"). That won't be much help, of course, if that's what you just finished fighting with. :(

---

### Post by xytheron on 2011-02-17
Hey,
I tried your suggestion with boot rec but no luck unfortunately...I can't even figure out what's telling the BIOS that GRUB and UBUNTU are still left...that's probably most frustrating

Namaste,
-Ray-

---

