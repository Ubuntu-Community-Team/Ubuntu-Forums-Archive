---
title: "Cannot get boot-splash to work"
date: 2006-06-13
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-13
Hello!

I've been trying to install a boot-splash screen and it seems that no matter what I do, it will not work!

I download the image from 'gnome-look.org'>'splash screens.'

They are usually not the correct size (640*480) and not in the '.xpm' format.

So using 'The Gimp', I scale them down and save them as '.xpm.'

THEN I open a terminal and 'gzip' the one that I want to try and move it into the

/boot/grub/images folder that I created.  I then pull up my /boot/grub/menu.lst

and edit the splash image in and after saving, I reboot and Nothing!

  Device Boot      Start         End      Blocks   Id  System
**/dev/hda1   *           1        4717    37889271    7  HPFS/NTFS**
/dev/hda2            4718        8633    31455270   83  Linux
/dev/hda3            8634        8876     1951897+  82  Linux swap / Solaris
/dev/hda4            8877       14946    48757275   83  Linux

'hda1' is where 'grub' is installed and 'ubuntu' is on 'hda4' and in charge of 'MBR.'

So I cant figure out why it's not working!

Any Ideas are welcome!

---

### Post by zxee on 2006-06-13
Have you taken a look at this how to? [http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image](http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image)
I'm wondering if ubuntu's grub  needs something extra to do this since there is no splash screen by default. I use the grub in my slack install to boot the rest of my distros so I haven't personally needed to fiddle with ubuntu's grub.

---

### Post by randell6564 on 2006-06-13
[QUOTE=zxee]Have you taken a look at this how to? [http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image](http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image)
I'm wondering if ubuntu's grub  needs something extra to do this since there is no splash screen by default. I use the grub in my slack install to boot the rest of my distros so I haven't personally needed to fiddle with ubuntu's grub.[/QUOTE]

Thank you, I'll try the link!

I read somwhere that it might have something to do with the 'Kernel.'  I'll keep trying!

---

### Post by randell6564 on 2006-06-13
Thank you 'zxee' the link that you provided worked!

Now i KNOW that 'Beggars cant be Choosers' but I want to figure out how to install the splash of MY CHOICE!

I guess I could try my old method and incorporate the commands from your link.

I'll keep ya informed!

---

### Post by keke21 on 2006-06-13
[QUOTE=randell6564]Thank you 'zxee' the link that you provided worked!

Now i KNOW that 'Beggars cant be Choosers' but I want to figure out how to install the splash of MY CHOICE!

I guess I could try my old method and incorporate the commands from your link.

I'll keep ya informed![/QUOTE]
First, are we allowed to post files on these forums? If so, I'll gladly turn whatever image you have into your new GRUB boot splash. If you've already followed the link and gotten the default splash to work, getting a new image won't be any problem at all.

If not, get your favorite image, scale it, change it to 14 colors, and save it as ubuntu.xpm. Put said ubuntu.xpm into a ubuntu.xpm.gz and replace the old one in /boot/grub/images with your new one.

---

### Post by randell6564 on 2006-06-13
[QUOTE=keke21]First, are we allowed to post files on these forums? If so, I'll gladly turn whatever image you have into your new GRUB boot splash. If you've already followed the link and gotten the default splash to work, getting a new image won't be any problem at all.

If not, get your favorite image, scale it, change it to 14 colors, and save it as ubuntu.xpm. Put said ubuntu.xpm into a ubuntu.xpm.gz and replace the old one in /boot/grub/images with your new one.[/QUOTE]

Thanks I'll try that!
Although, I DO try and get images that are pretty dull where color is concerned.

Not sure how to change them to 14 colors.      ?

---

### Post by keke21 on 2006-06-13
[QUOTE=randell6564]Thanks I'll try that!
Although, I DO try and get images that are pretty dull where color is concerned.

Not sure how to change them to 14 colors.      ?[/QUOTE]
Image > Mode > Indexed...

Just let it choose the colors (default) unless you really want to play with it yourself.

[Here's mine.](http://img158.imageshack.us/img158/1576/ubuntulogo9ml.png)

---

### Post by randell6564 on 2006-06-14
Thanks My Friend!

Im on it! I'll keep ya posted!

---

