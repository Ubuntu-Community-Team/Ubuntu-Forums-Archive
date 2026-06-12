---
title: "Kind of stuck"
date: 2009-04-27
forum: General Help
---

### Post by noname580 on 2009-04-27
Been using ubuntu now for sheesh 6 months or so.  Havent had too many problems, atleast nothing google couldnt  help me fix.  I was doing research on this product name tor and privoxy. Im sure most if not all have heard of it.  I was following the step by step install guide and got stuck.  I know it has nothing to do with the programs themselves because they work-ish.  The problem i am having is in configuring the config file for privoxy.  I open it with text editor by clicking it.  Change what needs to be changed. I go to save it and this pops up "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."  I right click the file and it says that i dont have permission to edit the file.  I am not root.  I am the only one that uses  my computer.  I have the only profile.  I can edit the Users and Groups.  I can only seem to edit any file in the home folder only.  I also tried editing the config file for ushare and cant due to permission.  How do i fix this?  What is the problem? thank you in advance for the help.  Also any other info needed let me know

---

### Post by VCoolio on 2009-04-27
For changing files in the root section you need
gksudo gedit /path/to/file
Btw, I have also installed privoxy but didn't need to change the config. But maybe you want a specific port? Anyway, command above opens gedit with rights to write to file.

---

### Post by Iowan on 2009-04-27
I usually use **sudo nano** from a terminal, but either one could (probably) be run from ALT-F2 (Run Application).

---

