---
title: "Kernel upgrade -&gt; Xubuntu Usplash???"
date: 2005-12-23
forum: General Help
---

### Post by akniss on 2005-12-23
I just upgraded my kernel with the update button in the system tray, then rebooted.  My Usplash screen somehow changed from the blue Ubuntu screen that I had put in earlier to a Xubuntu screen???   What the heck???  Everything was fine, no errors, booted up, gave me my normal login screen, and the default session was still Gnome.  Anyone have any ideas on how this happened???

---

### Post by The Warlock on 2005-12-23
Have you installed the xubuntu-desktop package? Because that'll do it.

---

### Post by akniss on 2005-12-23
[QUOTE=The Warlock]Have you installed the xubuntu-desktop package? Because that'll do it.[/QUOTE]

I installed xubuntu-desktop about a month ago, then removed it a couple weeks ago... not sure why it decided to show up now.  I also lost my Windows XP entry in Grub. I had to edit the menu.lst to get it back.

---

### Post by dezier on 2005-12-28
I know this is against the netiquette, but I have the same problem and no further information. The start up logo changed to xubuntu after the last kernel upgrade.

---

### Post by punkr0x on 2005-12-28
See the end of [this thread]("http://www.ubuntuforums.org/showthread.php?t=95451&page=2") for info on how to change your splash screen (update-alternatives).

---

### Post by xurizaemon on 2006-09-14
from the thread linked above ...

ok fixed it. I found some info in one of the threads. this is what you do. Open the terminal and type:
```
sudo update-alternatives --config usplash-artwork.so
```
(this will open a selection box that lets you decide which splash you would prefer 1.default(ubuntu) 2.kubuntu and 3.xubuntu. select one and then press <enter>)
Now enter:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```
(this will build your choice into the initramfs) (enter)

It will take about 10-30 seconds and thats it you are done.
Restart and enjoy!

---

