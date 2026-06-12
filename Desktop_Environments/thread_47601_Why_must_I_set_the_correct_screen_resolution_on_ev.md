---
title: "Why must I set the correct screen resolution on every startup?"
date: 2005-07-09
forum: Desktop Environments
---

### Post by jon_gunnar on 2005-07-09
I want to have 1024x768 at 85Hz but Ubuntu insist on 1280x1024 at 60Hz.

I manually change this via System/Preferences/Screen Resolution and it looks good until nest start, then its back to the same. It is very irritating, and it has been this way on two separate machines for me.
One of them with a Geforce 3TI card and the other one with a Asus 6600GT pci-express card.

NVIDIA driver installed on both and running very well. But I would like to be able to keep the resolution I prefer and want.

Anyone able to help out with this.

---

### Post by mohaham on 2005-07-09
you can force this by adding  xres=1024x768 in the boot options
in /boot/grub/menu.lst  file
like this...

title Ubuntu
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5  xres=1024x768
initrd (hd0,4)/boot/initrd.2.6.10
savedefault

---

### Post by jon_gunnar on 2005-07-10
[QUOTE=mohaham]you can force this by adding  xres=1024x768 in the boot options
in /boot/grub/menu.lst  file
like this...

title Ubuntu
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5  xres=1024x768
initrd (hd0,4)/boot/initrd.2.6.10
savedefault[/QUOTE]
Thank's a lot for the suggestion. I will try this, and hopefully it solves this matter.

---

### Post by jon_gunnar on 2005-07-10
[QUOTE=mohaham]you can force this by adding  xres=1024x768 in the boot options
in /boot/grub/menu.lst  file
like this...

title Ubuntu
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5  xres=1024x768
initrd (hd0,4)/boot/initrd.2.6.10
savedefault[/QUOTE]
Well, then I have tried this but the sorry state is the same. As fast as gnome loads the resolution is set to 1280x1024x60Hz  ](*,)

---

### Post by molvistan on 2005-07-10
do the following:

Click the applications menu, select Configuration Editor from the System Tools menu.

Now go to the following key (location):

/desktop/gnome/screen/default/0/

In the right pane you should see a key called 'resolution', double click this and enter your preferred resolution in the value box.

restart

You should find that everytime u login your preferred resolution is in use.

Have a nice day!

---

### Post by jon_gunnar on 2005-07-10
[QUOTE=molvistan]do the following:

Click the applications menu, select Configuration Editor from the System Tools menu.

Now go to the following key (location):

/desktop/gnome/screen/default/0/

In the right pane you should see a key called 'resolution', double click this and enter your preferred resolution in the value box.

restart

You should find that everytime u login your preferred resolution is in use.

Have a nice day![/QUOTE]

Thanks for the tip. But I don't have this key that all.
What I got is screen/ubuntu/0 
And the correct values is present there. And this problem have been in effect on two separate machines now. Very strange.

---

### Post by molvistan on 2005-07-10
try creating it, because i have the ubuntu key aswell as the default key, the ubuntu key is for the login screen and the default key is used after logging in (well this is  what happens on my computer).

Also check the V and H refresh rates in the xorg.conf file.

---

### Post by jon_gunnar on 2005-07-11
[QUOTE=molvistan]try creating it, because i have the ubuntu key aswell as the default key, the ubuntu key is for the login screen and the default key is used after logging in (well this is  what happens on my computer).

Also check the V and H refresh rates in the xorg.conf file.[/QUOTE]
Problem solved  :grin: 
I tried to remove the tick mark for 
"Make default for this computer (ubuntu) only"
And that did the job. The default key you mentioned were created, and the resolution suddenly were correct.
Thanks a lot for your'e help on this one.

---

### Post by pointym5 on 2007-01-17
> **molvistan said:**
> do the following:

Click the applications menu, select Configuration Editor from the System Tools menu.

Have a nice day!

What "System Tools" menu?  There isn't one in Edgy.

Running gconf-editor manually (i.e., from a terminal) works, but then there's no key - there's not even gnome/screen.

---

### Post by imagerodeo on 2007-04-21
Here's how to turn on the Configuration Editor in Feisty; may work in Edgy:

* right click on Applications menu
* select Edit Menus
* check the box next to Configuration Editor
* close the window

Now it'll appear as Applications > System Tools > Configuration Editor.

---

### Post by Ulsak on 2008-01-07
Thanks alot ! A simple and useful tip. You guys rock!:guitar:

---

