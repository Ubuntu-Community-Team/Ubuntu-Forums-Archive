---
title: "[SOLVED] sound!fail on 1525 after update 3rd time"
date: 2009-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by henrydurham on 2009-01-10
I have a 1525, for the third time the sound does not work after an update. Can anyone help?

---

### Post by c-cube on 2009-01-10
I guess you're talking about Dell Inspiron 1525 with Ubuntu 8.04.1.

I offered this laptop to my father for Christmas.

Yesterday he phoned to me and told me about this issue with sound after an update. The update process installed the 2.6.24-23 kernel.

That's why I told him to boot with the previous kernel (2.6.24-22).
Sound is working fine with this kernel.

So I guess the sound issue has to do with the last kernel for Ubuntu 8.04.1 (it might be due to changes in Ubuntu modules).

---

### Post by henrydurham on 2009-01-10
How do I do that?

---

### Post by usstitan on 2009-01-10
Hi I had this same problem, if you go this site [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade") and go down to the bottom it will give you instructions how to fix this, just have to go into terminal. Remember to change 2.6.24-17-generic too 2.6.24-23-generic.Hope this helps.

---

### Post by c-cube on 2009-01-10
[QUOTE=henrydurham]

How do I do that?[/QUOTE]

When you are booting your Dell Inspiron, there's a countdown lasting 3 seconds.
If you press Esc during this countdown, you'll have access to your Grub menu.
When the Grub menu is being displayed, select the 2.6.24-22-generic kernel with the down arrow key and press Enter to boot with this kernel.

You should now have sound.

If you prefer, you can set your Grub menu so that it is displayed each time you boot, without having to press Esc.

If you want to do that, you have to edit the *menu.lst* file.

Be carefull here, for a bad setting in this file can prevent your laptop from booting.

Open a terminal and type :

*gksudo gedit /boot/grub/menu.lst*

Then look for this section in the menu.lst file :

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

And insert a # character at the beginning of the timeout line, like this :

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		3

It will disable the Grub countdown. Indeed, the timeout line is now "commented" (this is how the fact of inserting a # character in a configuration file is called).

Save the *menu.lst* file and exit. Then reboot and the Grub menu will be displayed without having to press the Esc key.

---

### Post by henrydurham on 2009-01-11
Thank :guitar: you both the problem is now solved!

---

