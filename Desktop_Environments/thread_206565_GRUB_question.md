---
title: "GRUB question"
date: 2006-06-30
forum: Desktop Environments
---

### Post by xenomorph99 on 2006-06-30
Hi,

I had Ubuntu installed but decided to install Xubuntu on a 'spare' partition on the same HDD just to try some speed comparisons for some games running under Wine.

Now, Xubuntu has obviously changed the GRUB bootloader menu to put itself as the default boot option. If I want to remove Xubuntu, and put GRUB back to booting Ubuntu as default, how do I do that?

I've had a look at some GRUB into and it talks about changing the menu file. But, if I remove Xubuntu from the partition, presumably, that will remove the GRUB menu file also and it won't know what to do unless I point it to the menu file on the Ubuntu partition (I'm guessing here).

Is there any easy solution to this?

Regards,
Xeno

---

### Post by coffeecat on 2006-06-30
[quote=xenomorph99]Is there any easy solution to this?[/quote] 
Yes. You need to reinstall the Grub stage 1 for the installation you want to keep. Boot into the installation to be retained, open a terminal and do 'sudo grub'. You will now get the grub prompt. Now it gets slightly complicated because I don't know which partition Ubuntu is on. If it's hda1, do the following (> = grub prompt):

> root (hd0,0)

> setup (hd0)

> quit

Now close the terminal and reboot. Grub will now work from hda1 but now, of course, you won't be able to boot into Xubuntu because there won't be an entry in the hda1/Ubuntu /boot/grub/menu.lst. That can be edited if you want to change your mind.

If your Ubuntu installation is not on hda1, you can work it out because grub numbers from 0. (hd0,1) = hda2; (hd1,0) = hdb1, and so on. Post back if you are not sure.

Some might advise running 'grub-install' from a terminal. Not advisable. It is unreliable. Even the Grub manual admits this.

**Edit:** If you want a headache :wink: you could have a look at the [Grub Manual](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by xenomorph99 on 2006-06-30
Thanks...

The disk it is on is reported as /dev/hdc but I suppose it's actually hd0 as there is only one hdd in there at present (I removed the other in case grub went off and overwrote my XP bootloader).

The actual partition that Ubuntu resides on is /dev/hdc7 so how do I go about that?

Also, let me really turn things on their head...

What I'd really like to do is to put my existing Ubuntu installation on the partition where XUbuntu is at present (as it is larger).  Is it possible to simply 'copy is across' or is there going to be a load of aggro as it's expecting to be still living on hdc7 ?

Failing that, let's say I wanted to get rid of Xubuntu but mount the ext3 partition that it was on as my /home dir. How do I do that?

Regards,
Xeno

---

### Post by coffeecat on 2006-06-30
> **xenomorph99]The disk it is on is reported as /dev/hdc but I suppose it's actually hd0 as there is only one hdd in there at present[/quote] 
Take care. Depending on your m/board, BIOS and how the various IDE devices are attached, hda may be your optical drive. The non-existent hdb would be the slave channel on that. I've been caught out this way once before. I find it quite disconcerting that a master HDD is designated hdc. :(

[quote=xenomorph99]The actual partition that Ubuntu resides on is /dev/hdc7 so how do I go about that?[/quote] 
That would equate to (hd2,6) grub-speak.  Hence: root (hd2,6)  said:**
> What I'd really like to do is to put my existing Ubuntu installation on the partition where XUbuntu is at present (as it is larger). Is it possible to simply 'copy is across' or is there going to be a load of aggro as it's expecting to be still living on hdc7 ? 
It is possible and I've done something similar more than once. But you have to edit /boot/grub/menu.lst and /etc/fstab before you boot into the moved installation (best with a live CD) otherwise it will throw a severe wobbly. Actually, you'll probably get a kernel panic. There's also the issue of how you copy it. I've used:

```
sudo cp -fpPrv /sourcepartition/* /destinationpartition
``` 
but die-hard Linuxers will say cp is unreliable in this situation and that you should use 'dd'. That takes an age though, and I haven't learnt the syntax for it yet.

Pass. :wink:

[quote=xenomorph99]Failing that, let's say I wanted to get rid of Xubuntu but mount the ext3 partition that it was on as my /home dir. How do I do that?[/quote] 
Copy /home across* and edit /etc/fstab. I'm not sure what you would put in the fstab line, but I'm sure that between us we could find out. :) Or perhaps some other kind soul might chime in.

* **Edit** and you'd need to setup a symlink folder in / to your moved /home.

---

### Post by jtholmes on 2006-06-30
dd if=/dev/h??N of=/dev/h??N bs=5120 

but be careful and know for sure that your  h??N's are correct

As for grub read some tutorials from google. you are in a situation
that is easily corrected, however telling you how to do it is
three pages. if you want to ask me personal questions about
it then email me at
[email]jt@jtholmes.com[/email]

jt

---

