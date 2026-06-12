---
title: "screen resolution"
date: 2009-01-17
forum: General Help
---

### Post by zezerbing on 2009-01-17
Hello I,ve been using a small CRT screen but it went bad.Now I have a 20" flat panel. The resulution is way off. it says 640 X 480 and can't change it. I wen't into systems and i con't change it.It should be something like 1280 X 1024. I went into bios and looked around. The menu screen doesn't let me change it. My linux book doesn't go into detail.I thought it would change automatically. thanks

---

### Post by abn91c on 2009-01-17
try sudo dpkg-reconfigure xserver.xorg

---

### Post by blackened on 2009-01-17
I'm going to assume you're using 8.10. If this is true, then reconfiguring xorg via dpkg will do nothing but wipe your xorg.conf file clean. Let's try a manual solution instead:

First, you'll need the hsync and vrefresh ranges for your monitor. These can be gotten from the documentation that was provided with your monitor, or from the internet (Google your make/model). Once you've got those handy open a terminal window:

```
gksudo gedit /etc/X11/xorg.conf
```

Find the "Monitor" section

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync          **30-82**
	VertRefresh        **56-76**
EndSection
```

Replace the bolded ranges with those that apply to your monitor. Save the file and close it.

Restart X with ```
sudo /etc/init.d/gdm restart
```

After logging back in, check System -> Preferences -> Screen Resolution

---

