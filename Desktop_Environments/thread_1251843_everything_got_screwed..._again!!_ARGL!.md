---
title: "everything got screwed... again!! ARGL!"
date: 2009-08-28
forum: Desktop Environments
---

### Post by jomex on 2009-08-28
when i booted my computer today everything got completely screwed ... again. >:(

all i see is my blank desktop background, Firefox and Skype (the startup applications). there are no menus, panels or window captions. Alt+[F2] doesn't work.

i tried:

dpkg-reconfigure xserver-xorg
dpkg-reconfigure gdm

with the outcome that my resolution is now 800x600... again... grrrr

things i did before the incident:
i ran computer janitor... which hang up every time
manually removed nautilus and glipper, while the last one removed 80MB(???)
i configured some keyboard shortcuts in "Keyboard Shortcuts" and gconf-editor
i rearranged my panels and panel-icons (at this time i was still seeing them)


i'm sorry if i start annoying anybody with my problems already but i'm quite frustrated as this is like the 10th problem since the month i installed Ubuntu which completely messed up everything and i'm already getting tired of fixing these problems.

---

### Post by jomex on 2009-08-29
someone, please help!

---

### Post by TomB19 on 2009-08-29
I can't help with your problem but, if it's any consolation, I'm having the identical issue with kubuntu.  My KDE 4.2 desktop won't start.

I'm using the ATI binary drivers.  Perhaps this is the issue?

Yes...  it can be extremely frustrating.  I'm ready to switch distributions.  Ubuntu was fantastic back in the 8.10 days.  It was bulletproof.  These days it's a crap shot every time you update the system.  It's time for Fedora Core.

---

### Post by juancarlospaco on 2009-08-29
mmm..., why remove nautilus?
try to reinstall the desktop

**sudo apt-get install --reinstall ubuntu-desktop**

*make another redundant user account, just in case, you screwed your configs*

---

### Post by Copernicus1234 on 2009-08-29
Its probably not a good idea to remove system applications like Nautilus without knowing what it will do. :)

---

### Post by jomex on 2009-09-15
Nautilus was too sluggish,... so it got replaced by Thunar

```

sudo apt-get install --reinstall ubuntu-desktop

```
didn't fix it

i completely removed ubuntu-desktop now and installed xubuntu-desktop and LXDE

however the taskbar icons are missing, it's the same issue mentioned here: [url=http://sourceforge.net/tracker/index.php?func=detail&aid=2019094&group_id=180858&atid=894869]
[IMG]http://sourceforge.net/tracker/download.php?group_id=180858&atid=894869&file_id=284850&aid=2019094[/IMG][/url]

if i kill lxpanel and start it in the terminal i get
> 
lxpanel : X error: BadDrawable (invalid Pixmap or Window parameter)
XGetGeometry failed for 1 pixmap


---

