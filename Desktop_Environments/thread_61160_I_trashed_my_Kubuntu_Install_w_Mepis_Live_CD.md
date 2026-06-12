---
title: "I trashed my Kubuntu Install w/ Mepis Live CD"
date: 2005-08-30
forum: Desktop Environments
---

### Post by Cliff76 on 2005-08-30
Hello all. I'm new to Kubuntu and currently trying both Kubuntu and Mepis. I config'ed my Dell Optiplex which multi-boots WinXP, Mepis, and Kubuntu. (At least it used to multi-boot Kubuntu!) I got myself into a predicament where Kubuntu no longer boots. I did this stupidly. What happened was this. I was swapping my HD from a temp PC back to my original and I needed to reset my XF86Config file for Mepis to boot. So I inserted the MEpis live CD and booted with options that rendered my mouse useless. I then proceeded to work the MepisOS center with my keyboard. In the process, I made a mistake and asked MEpis to rewrite the XF86Config file to the wrong partition (my Kubuntu partition). It did so without pause and ever since then I am no longer able to boot into Kubuntu. Is there a way to restore bootability without re-installing? Help!

Cliff

---

### Post by Elv13 on 2005-08-30
with the mepis/ubuntu live cd, go to etc/X11 or the xorg folder and look for ~xorg.conf, if you find it, remove the~ and overwrite the other file

---

### Post by arnoct on 2005-08-30
Either that, or you could boot into kubuntu, and after x doesn't boot you run:

sudo dpkg-reconfigure xserver-xorg

Answer the questions it asks you and it'll generate a new conf file for you.

---

### Post by Cliff76 on 2005-08-31
I looked into the /etc/X11 folder and I didn't see an old ~xorg.cong. I did see xorg.conf as well as a XF86Config file which I deleted. I'm going to try rebooting now and see if that fixes anything. I'm also wondering if this has anything to do with Grub. I don't know enough to be sure but I did replace Ubuntu's Grub loader with the Grub loader in Mepis which is appears to be a slightly different version of Grub. I'm going to change the grub settings a little too to see if that helps. For what it's worth, I installed Kubuntu about a month ago after using Mepis for about a 1/2 year. I played with it briefly only to return back to Mepis for unrelated reasons. Now I want to try out Kubuntu again.

---

### Post by Cliff76 on 2005-08-31
Ok, I just tried rebooting into Kubuntu and it's a no-go. More info: When I choose Kubuntu from my Mepis grub menu it instantly jumps to a grub menu that looks like it did When I was using Kubuntu's version of Grub. I can't get to anything other than a Grub bash-like command line so I don't think I can run the dpkg-reconfigure xserver-org command. At this point I'm not sure what's wrong. Could it be just a matter of reinstalling a standard version of Grub? Like I said earlier, I'm using the Mepis augmented version of Grub that has the Mepis logo though I could try a standard Grub to see if that works. I used the Mepis Grub because it has graphics though I don't know enough to know if it was even necessary or preferrable to replace the std with the special Grub version. Please help.

---

### Post by tonysathre on 2005-08-31
try reinstalling grub with the ubuntu install cd

---

### Post by az on 2005-08-31
Yeah.  Chroot into your ubuntu partition and type
sudo grub-install /dev/hda (assuming that you boot from /dev/hda)


(If Ubuntu is on /dev/hdb4, for example, do
chroot /dev/hdb4
from a root terminal, or the installer cd)

---

### Post by Cliff76 on 2005-09-02
Sorry it took so long to reply. I just tried what you two suggested and it's not working. I tried reinstalling Grub using the install CD and it looks like it want me to run thru the partition manager first. If I bypass the formatting of my Kubuntu partition and just try to install Grub it gives errors saying an install step was skipped. So then I try the chroot thing (bear in mind I've never used chroot before and I'm not sure what it does though I have an idea). After I chroot (while booted and logged into my Mepis OS) I have this on the command line:

```
root@ccc:/ # grub-install /dev/sda
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
The file /boot/grub/stage1 not read correctly.
``` 

I'm banging my head against the wall on this!  ](*,)  Help!

---

### Post by oghanchi on 2005-09-02
Type **sudo** before the command  :)

---

### Post by az on 2005-09-02
Duh!  My mistake!

You must mount the filesystem first, then chroot into it!

sudo mount /dev/sda1 /mnt #(I assume it is sda1, and not sda2 sda3 or something)
sudo chroot /mnt
sudo grub-install /dev/sda

---

### Post by Cliff76 on 2005-09-06
[QUOTE=azz]Duh!  My mistake!

You must mount the filesystem first, then chroot into it!

sudo mount /dev/sda1 /mnt #(I assume it is sda1, and not sda2 sda3 or something)
sudo chroot /mnt
sudo grub-install /dev/sda[/QUOTE]
 azz,

Yeah I figured out that I had to mount before I chroot. I tried both with and without sudo and I get the same error:

root@ccc:/ # grub-install /dev/sda
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
The file /boot/grub/stage1 not read correctly.
root@ccc:/ # sudo grub-install /dev/sda
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
The file /boot/grub/stage1 not read correctly.

What gives? Am I doing something wrong?

---

### Post by Cliff76 on 2005-09-07
[QUOTE=Cliff76]azz,

Yeah I figured out that I had to mount before I chroot. I tried both with and without sudo and I get the same error:

root@ccc:/ # grub-install /dev/sda
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
The file /boot/grub/stage1 not read correctly.
root@ccc:/ # sudo grub-install /dev/sda
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
/sbin/grub-install: line 477: /dev/null: Permission denied
/sbin/grub-install: line 479: /dev/null: Permission denied
The file /boot/grub/stage1 not read correctly.

What gives? Am I doing something wrong?[/QUOTE]
 Is there no fixing this?

---

### Post by gusenise on 2005-09-27
I am having the same problem!!!
I had to boot from the Live CD, and now I cant mount with write privileges!!

Please help!
What should I do???

Thankss
[http://ubuntuforums.org/images/smilies/icon_cool.gif](http://ubuntuforums.org/images/smilies/icon_cool.gif)

---

