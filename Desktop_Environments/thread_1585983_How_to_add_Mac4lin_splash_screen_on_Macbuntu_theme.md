---
title: "How to add Mac4lin splash screen on Macbuntu theme? [For thsoe who are familiar]"
date: 2010-10-01
forum: Desktop Environments
---

### Post by aisajib on 2010-10-01
Hi! I have installed Macbuntu theme recently and it changed my ubuntu look to snow leopard including the global menu. I used Mac4lin earlier and was satisfied with that. But this macbuntu theme changes the entire look more like mac and it comes bundled with global menu.

See my current desktop environment:

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs708.snc4/62875_1646701129702_1302134464_31802230_7741759_n.jpg[/IMG]

[I](I've recently uninstalled Docky and installed Cairo Dock instead.)

[/I]Now, there's only one thing that Macbuntu is missing. That's the splash screen. By default, you see the ubuntu logo during bootup and shutdown. But mac4lin changes it to a gray background with an apple logo on it; which is awesome. But macbuntu doesn't come with this.

I've gone through mac4lin files. Inside its plymouth folder, there is a folder named "Mac-Bootup" which contains "mac-bootup.plymouth," "mac-booktup.script" and several images (dots, apple logo, etc).

Now the question is, how do I install this plymouth from terminal? I will have to install mac4lin first to get the splash screen, then uninstall it and reinstall the current macbuntu. Which is a long mess as you can see.


Can anybody help me with this, please? I just want to know how to install that mac-bootup.plymouth splash screen.

---

### Post by ankspo71 on 2010-10-01
Hi,
I don't have much experience with mac4lin or macbuntu, but I think this link will help.
[http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04](http://ubuntuguide.net/howto-change-plymouth-themes-initial-splash-screen-in-ubuntu-10-04)

The above link explains how to install plymouth themes (via Ubuntu) and choose between the plymouth themes, but I think all you need to do additionally is you will have to copy the folder named "Mac-Bootup" to /lib/plymouth/themes/

Then run the command to install the theme:
```
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/Mac-Bootup/mac-bootup.plymouth 100
```
Then run the command to choose the theme
```
sudo update-alternatives --config default.plymouth
```
Then run the command:
```
sudo update-initramfs -u
```

And that should work.
Edited: I added an additional important step in the instructions that I found here [http://ubuntuguide.net/install-mac-os-x-boot-up-splash-screen-theme-in-ubuntu-10-04](http://ubuntuguide.net/install-mac-os-x-boot-up-splash-screen-theme-in-ubuntu-10-04)

---

### Post by ankspo71 on 2010-10-01
Hi again,
Here is another link to another mac plymouth theme with instructions that you will find useful. This one has another step in the instructions that tells Ubuntu to include the mentioned theme as an alternative plymouth theme. This is very important step that will make the other advice I gave you work too. I'm going to correct that other reply now.

[http://ubuntuguide.net/install-mac-os-x-boot-up-splash-screen-theme-in-ubuntu-10-04](http://ubuntuguide.net/install-mac-os-x-boot-up-splash-screen-theme-in-ubuntu-10-04)

---

### Post by aisajib on 2010-10-01
Thank you so much ankspo71. I gave up hope to get help from anyone as no one was replying to this thread. 

Your second reply found me a better splash screen. A big bunch of thanks for that. :)

---

