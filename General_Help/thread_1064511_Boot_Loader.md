---
title: "Boot Loader"
date: 2009-02-08
forum: General Help
---

### Post by unplugged23 on 2009-02-08
Hey there,

 Just installed some slackware linux (backtrack) which changed the systems default boot loader to lilo.the only problem with this is that, lilo is only displaying the backtrack OS. I tried editing the .conf file but i got errors like "the first sector does not contain a boot image" when trying to set it to also load the ubuntu partition. is there any way to switch back and forth between boot loaders, or to install ubuntu to the lilo bootloader, or backtrack to the grub loader. keep in mind that there is no way for me to access ubuntu now to change settings.

---

### Post by oldos2er on 2009-02-08
You can use an Ubuntu LiveCD or Super Grub Disk to restore grub.

---

### Post by Le-Dart on 2009-02-09
If you can boot into Slackware, there's a guide setting up Lilo for dual/multi boot.Patrick Volkerding, the man behind Slackware,  provides excellent documentation with Slackware. 

Or you can go to the Slackbook website.
[http://www.slackbook.org/html/index.html](http://www.slackbook.org/html/index.html)
[http://www.slackbook.org/html/booting.html](http://www.slackbook.org/html/booting.html)

There's also an excellent Slackware forum at Linux Questions

[http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

That's one of the main things about Slacky, you have to set stuff up yourself. But you will learn an awful lot. I did. Don't give up, it's worth it!
Good luck

---

### Post by unplugged23 on 2009-02-09
> **oldos2er said:**
> You can use an Ubuntu LiveCD or Super Grub Disk to restore grub.
 I don't want to restore grub, because grub refuses to recognize backtrack. do you configure grub the same way you do lilo?

---

### Post by unplugged23 on 2009-02-09
> **Le-Dart said:**
> If you can boot into Slackware, there's a guide setting up Lilo for dual/multi boot.Patrick Volkerding, the man behind Slackware,  provides excellent documentation with Slackware. 

Or you can go to the Slackbook website.
[http://www.slackbook.org/html/index.html](http://www.slackbook.org/html/index.html)
[http://www.slackbook.org/html/booting.html](http://www.slackbook.org/html/booting.html)

There's also an excellent Slackware forum at Linux Questions

[http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

That's one of the main things about Slacky, you have to set stuff up yourself. But you will learn an awful lot. I did. Don't give up, it's worth it!
Good luck

Thank you! Very Helpful! [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by Ptero-4 on 2009-02-09
you can try to reinstall backtrack´s lilo telling it to install itself in your backtrack root partition, boot off the ubuntu liveCD, restore grub and finally from within ubuntu add this
```

title         Backtrack
root          (hdX,Y)
chainloader   +1

```
to your /boot/grub/menu.lst file, and type
```
sudo update-grub
```
to make grub see the new entry.
P.D: You need to put your backtrack´s root partition number where I placed (hdX,Y). Note however that grub´s notation is one digit less than the normal linux drive notation, so if the partition is /dev/sda1 in grub it´s hd0,0. If it´s /dev/sda4 it will be hd0,3. /dev/sdc2 is hd2,1 and so on.

---

### Post by unplugged23 on 2009-02-10
> **Ptero-4 said:**
> you can try to reinstall backtrack´s lilo telling it to install itself in your backtrack root partition, boot off the ubuntu liveCD, restore grub and finally from within ubuntu add this
```

title         Backtrack
root          (hdX,Y)
chainloader   +1

```
to your /boot/grub/menu.lst file, and type
```
sudo update-grub
```
to make grub see the new entry.
P.D: You need to put your backtrack´s root partition number where I placed (hdX,Y). Note however that grub´s notation is one digit less than the normal linux drive notation, so if the partition is /dev/sda1 in grub it´s hd0,0. If it´s /dev/sda4 it will be hd0,3. /dev/sdc2 is hd2,1 and so on.

I'm on the live cd now, I just dont know how to restore grub. Could someone please be a little more specific?

EDIT: I'm looking at the boot folder on the HDD containing the ubuntu partition, and can see the grub files, but im not quite sure what to do from here to restore grub. Would just formatting my hard drives and reinstalling be easier?

EDIT 2: I popped open a terminal and typed "sudo grubconfig" to no avail. after that i tried "sudo grub" and got somewhere. i tried typing restore but got error 27: unrecognised command. what command should i use?

EDIT 3: Hit tab and got a list of command, i tried typing "install /dev/hda1" and "install /dev/hda0" both times i got error 12: invalid device  requested

---

### Post by oldos2er on 2009-02-10
"I'm on the live cd now, I just dont know how to restore grub. Could someone please be a little more specific?"

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by unplugged23 on 2009-02-10
Eh, I got bored and just went ahead and did a fresh install, them from here i can follow the help in an above post on how to add the other OS to my grub menu. Thanks for the help!

---

### Post by unplugged23 on 2009-02-10
> **Ptero-4 said:**
> you can try to reinstall backtrack´s lilo telling it to install itself in your backtrack root partition, boot off the ubuntu liveCD, restore grub and finally from within ubuntu add this
```

title         Backtrack
root          (hdX,Y)
chainloader   +1

```
to your /boot/grub/menu.lst file, and type
```
sudo update-grub
```
to make grub see the new entry.
P.D: You need to put your backtrack´s root partition number where I placed (hdX,Y). Note however that grub´s notation is one digit less than the normal linux drive notation, so if the partition is /dev/sda1 in grub it´s hd0,0. If it´s /dev/sda4 it will be hd0,3. /dev/sdc2 is hd2,1 and so on.

Ok, im confused. Am i supposed to run the 
```

title         Backtrack
root          (hdX,Y)
chainloader   +1

```
from terminal? because when i do, i cant make it passed the first string without getting the error "bash: title: command not found" but if i need to start by making changes in my /boot/grub/menu.lst file and then updating, im also having a problem because the only 2 things in my boot folder are "map" and "vmlinuz" So what should i do from here?

---

### Post by unplugged23 on 2009-02-10
Just wanted to bump the post, because I feel like maybe the topic of the post has change a little, but I'm not sure if I want to open another thread that would be very similar to this one. There is nothing in my /boot/grub directory except for 2 things. Something named "map" and another named "vmlinuz" The system still boots without a problem but I need to edit the /boot/grub/menu.lst file. I'm a little confused as to why there's nothing there. I did just do a fresh install by the way, for anyone that's read through the post up to here. Could this have anything to do with it? Does anyone have a solution? Thanks again for all your support!

---

### Post by unplugged23 on 2009-02-10
Bump :(

---

### Post by unplugged23 on 2009-02-11
Bump

---

### Post by Ptero-4 on 2009-02-12
unplugged. There SHOULD be a file called menu.lst inside a folder called grub inside the /boot folder. This file is what tells grub what entries are in the boot menu, which one is the default one and how long to wait before booting the default entry among other things related to the boot menu. The lines
```

title         Backtrack
root          (hdX,Y)
chainloader   +1

```
have to be added AT THE END of the menu.lst file (those three lines add an entry to the boot menu which when selected directs grub to boot backtrack). And then FROM THE TERMINAL you type ```
sudo update-grub
``` to get it to recognize the changes made to the menu.lst file.

---

