---
title: "Ubuntu 23.04 - No shortcut on desktop possible"
date: 2023-06-27
forum: Desktop Environments
---

### Post by jerem0808 on 2023-06-27
Hi all,
I cannot create a shortcut on my desktop. I tried to copy the .desktop under the Desktop folder but nothing happens. As well, it seems that i am missing some settings under Ubuntu Desktop in the settings (see below).
Any ideas? :)
I pasted some screenshot that may help understand more what's happening

thank you for your support

---

### Post by ActionParsnip on 2023-06-27
[https://ubuntuhandbook.org/index.php/2023/04/add-app-shortcut-desktop-ubuntu/](https://ubuntuhandbook.org/index.php/2023/04/add-app-shortcut-desktop-ubuntu/)

---

### Post by jerem0808 on 2023-06-27
I had to install extension manager through flatpak and not snap (kept crashing)
But i don't find add to desktop there (see attached file)
And i don't understand why i need to install this extension isn't something by default in ubuntu?

---

### Post by ActionParsnip on 2023-06-27
> **jerem0808 said:**
> I had to install extension manager through flatpak and not snap (kept crashing)
But i don't find add to desktop there (see attached file)
And i don't understand why i need to install this extension isn't something by default in ubuntu?
Gnome devs think desktop icons are the bad

---

### Post by TheFu on 2023-06-27
Choose a DE that allows use of the desktop in the way you prefer. There are lots of choices.
There may be an addon for Gnome4.x to allow it as well. IDK.

If you don't want a full DE, there are lots of capable WM-only setups that do allow nearly complete control over our GUI systems. Full customization for a personal workstation is a right on Linux. Unfortunately, some projects seem to disagree. Of course, we have the choice to use other software. After all, many people do like having set ways of working dictated. For those, look at the commercial OS vendors. They've been successful, clearly.

---

### Post by jerem0808 on 2023-06-27
Hi all,
thanks for the replies. 
I found the add on "Add to Desktop" enabled it and i added an app to the desktop (libreffice). But still nothing. 
Should it work?
Thanks

---

### Post by #&amp;thj^% on 2023-06-27
> **jerem0808 said:**
> Hi all,
thanks for the replies. 
I found the add on "Add to Desktop" enabled it and i added an app to the desktop (libreffice). But still nothing. 
Should it work?
Thanks
It works you may have to log out and back in again to show or add new short cuts.
```
inxi -S
System:
  Host: voyager-zfs Kernel: 6.2.0-23-generic arch: x86_64 bits: 64
    Desktop: GNOME v: 44.2 Distro: Ubuntu 23.04 (Lunar Lobster)

```

---

### Post by yancek on 2023-06-27
>  And i don't understand why i need to install this extension isn't something by default in ubuntu? 				 			  			 			  			 				 					

The default for the Gnome Nautilus developers for Desktop icons is to NOT allow them.  Their decision so those who want the icons have to find a work around.

The method I describe here works on 20.04 but I don't have 23.04 so I don't know if it will work.  Click on the Nautilus/Files icon on the left panel of your Desktop and in your /home/username directory, open Desktop.  Create a file here with a desktop entry using an example from one of the default icons and save the file.

Right click on the desktop icon you just created and click Properties then click the  Permissions tab and check the box to the left of Allow executing file as a program.

In this same properties window, click the Open With tab and have Default Application show Run Software and click Set as Default tab in lower right. Close window. Right click desktop icon again and you should see an option to Allow Launching, click that.   The lines shown in the [Desktop Entry] need to all be correct.

---

### Post by #&amp;thj^% on 2023-06-27
I'm pretty sure I just confirmed it works on 23.04 See post #7
The OP just needs to logout and back in again.

---

### Post by jerem0808 on 2023-06-28
Hi 
jerem@jerem-XPS-13-9310:~$ inxi -S
System:
  Host: jerem-XPS-13-9310 Kernel: 6.2.0-23-generic arch: x86_64 bits: 64
    Desktop: GNOME v: 44.1 Distro: Ubuntu 23.04 (Lunar Lobster)

but even after log out log in it doesn't work. 
i rebooted the laptop as well.

---

### Post by ActionParsnip on 2023-06-28
Was gonna suggest reboot. Magic reboot fixes all

---

### Post by jerem0808 on 2023-06-28
Ahaha yeah unfortunately already tried this. Maybe i'll try to upgrade Gnome from 44.1 to 44.2

---

### Post by tea for one on 2023-06-28
Would this extension be useful for you?
[https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)
[https://gitlab.com/rastersoft/desktop-icons-ng](https://gitlab.com/rastersoft/desktop-icons-ng)

---

### Post by jerem0808 on 2023-06-28
Thanks for the info i will have a look. But i can close this thread for now. I thought that it was a bug in my distribution :)

---

### Post by #&amp;thj^% on 2023-06-28
> **jerem0808 said:**
> I had to install extension manager through flatpak and not snap (kept crashing)

I installed the .deb:
```
apt policy gnome-shell-extension-manager
gnome-shell-extension-manager:
  Installed: 0.4.0-1
  Candidate: 0.4.0-1
  Version table:
 *** 0.4.0-1 500
        500 http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Also Check if it is in the right spot:
```
cd ~/.local/share/gnome-shell/extensions/ && ls | grep add-to-desktop@tommimon.github.com
add-to-desktop@tommimon.github.com

```
```
&#9492;&#9472;> cd add-to-desktop@tommimon.github.com
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;gnome-shell/extensions/add-to-desktop@tommimon.github.com 
&#9492;&#9472;> ls
extension.js  LICENSE  locale  metadata.json  README.md  shortcutMaker.js

```
I still think I can help you if your still interested....
EDIT: [https://github.com/Tommimon/add-to-desktop](https://github.com/Tommimon/add-to-desktop)

---

