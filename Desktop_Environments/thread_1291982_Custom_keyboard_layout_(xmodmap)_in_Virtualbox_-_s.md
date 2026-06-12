---
title: "Custom keyboard layout (xmodmap) in Virtualbox - suddenly broken"
date: 2009-10-15
forum: Desktop Environments
---

### Post by Jenda on 2009-10-15
Hi,

I am using a modified dvorak layout, with the help of a .xmodmap file which took years (literally) to make and fine-tune. I use Ubuntu as my main and only OS. However, I recently got a job/deal for which I NEED to run Microsoft Office 2007, and it has proved most convenient to run it in XP in VirtualBox. It has been working perfectly for a few weeks now (and I got a lot of work done thanks to it, too &#12484;)

Occasionally, however, the guest system has started to ignore some of the keys (most that differ from default dvorak, although some have stayed, e.g., the Super modifier), but started working later (either by re-loading the xmodmap file, rebooting either OS or saving&restoring the virtual machine state. Now, however, it has happened again and doesn't seem to want to get better no matter what I do.

I believe it has some connection with XP's own keyboard layout, as it is the keys that the default layout doesn't have that don't work, with the exception of modifiers (which, AFAIK, the windows keyboard setup doesn't change). I also think I might've updated to a newer virtualbox version somewhere in the process.

Any suggestions about how to fix this? Thanks in advance &#12484;

---

### Post by Jenda on 2009-10-15
Hm, reverting .VirtualBox solved the issue. For now, at least.

---

### Post by Jenda on 2009-10-17
OK, it got broken again and this time, reverting .VirtualBox doesn't solve it. Any ideas?

---

### Post by Jenda on 2009-10-17
Bah, rebooting Ubuntu seems to have fixed it now - till next time. So far, it seems totally random.

---

### Post by Jenda on 2009-10-19
Finally solved. Vbox can use Windows XP's layouts (including my custom one) as long as no .xmodmap file is loaded when it starts. As it were, unplugging and plugging my external keyboard unloads any xmodmap files. For my full ranting on the progress of the problem (if anything similar ever happens to anyone), and more about the solution, can be found here: [http://forums.virtualbox.org/viewtopic.php?f=7&t=23419](http://forums.virtualbox.org/viewtopic.php?f=7&t=23419)

---

### Post by dewdrop_world on 2010-10-28
Believe it or not, this did help me!

I use xmodmap to change the positions of modifier keys. That alone is enough to completely screw up virtualbox's keyboard mapping. As you said in the vbox forum thread, reverting to an un-xmodmapped layout and launching vbox works around the issue nicely.

So thanks for posting! You never know who'll need it in the future...

---

### Post by dewdrop_world on 2011-01-28
Even better: VBox 4.0 fixes the issue entirely.


[http://www.virtualbox.org/ticket/2595](http://www.virtualbox.org/ticket/2595)


Downloaded, tried it, it works! xmodmap no longer confuses vbox.


James

---

### Post by MrWareWolf on 2011-09-28
cant type equals sign, also plus and minus symbols are all mapped wrong.. makes it frustrating to try to edit files when you can't even create one-line commands without the proper syntax.. 8(

---

