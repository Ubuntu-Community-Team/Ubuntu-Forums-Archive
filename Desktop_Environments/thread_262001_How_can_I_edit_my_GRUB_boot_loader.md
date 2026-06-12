---
title: "How can I edit my GRUB boot loader?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by cobbweb on 2006-09-21
Hello, 
   I just installed Dreamlinux on my machine (one 40gb hd, one 160gb hd). I installed it on my 40gb hd and also the GRUB bootloader. I don't like dream linux as Xubuntu has more support and can be configured to look the same. I tried tying in Grub in the terminal and also looked up the GrubHowTo on the wiki. I am lost on how I can make it so my Dreamlinux partition doesn't show up anymore (will soon be formated) and it automaticly boots into my Xubunut partion. Thanks for any help, 

 Cobbweb

---

### Post by hegenious on 2006-09-21
sudo gedit /boot/grub/menu.lst (make a safety copy first)

remove the lines for Dreamlinux so only the lines for xuxbuntu are left.

adjust the time out to 0 seconds

reboot

xubuntu will boot as default after 0 seconds

---

### Post by FyreBrand on 2006-09-21
The wiki tells you how to edit the grub menu.  There isn't much more to add.  One thing that I noticed is that it tells you to:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
sudo gedit /boot/grub/menu.lst
```I would use **gksudo** to oped gedit and not sudo.  Generally you should use sudo for the terminal and gksudo when authorizing gui apps to run as sudo. I would type the line in like so:```
gksudo gedit /boot/grub/menu.lst
```

Here is the link to the [**[COLOR="Sienna"]Grub-HowTo Change the Default OS[/COLOR]**]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") article.  This will let you have grub default to your xubuntu.

Here is a link to the [**[COLOR="Green"]General Grub HowTo[/COLOR]**]("https://help.ubuntu.com/community/GrubHowto") article.

If you are going to nuke that other partition soon, then why not just do that?  With gparted it only takes a few minutes to make that happen. Then you don't have to fool with the grub menu at all.

I haven't edited the grub menu in a long time, but one thing I remember from several months ago is that everytime you update the kernel grub defaults to that kernel upgrade from the last partition you upgraded.  I'm not sure if this is still true, but something to consider.

---

