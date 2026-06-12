---
title: "Intel 3d driver?"
date: 2007-09-02
forum: Dell  Ubuntu Support
---

### Post by garrowolf on 2007-09-02
I'm trying to get compiz to work. I have read that the intel graphics driver that comes with the 1420 doesn't support this. 

Is there an upgrade for it?

If so how do I do it?

---

### Post by angryfirelord on 2007-09-02
Open up a terminal & type:
```
sudo apt-get install xserver-xorg-video-intel
```
Then, type:
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to this section:
```
Section "Device"
	Identifier	"NVIDIA GeForce 6200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

```
Yours may not look the same as mine, but it should still say Section "Device". Next to driver, change whatever it says now to "intel" (with the quotes). It should look something like this:
```
Driver		"intel"
```
Log out and log back in.

---

### Post by garrowolf on 2007-09-02
ok so how do I confirm that it worked?

---

### Post by stmiller on 2007-09-02
type
```

glxinfo

```

into a terminal and it should output 

direct rendering: Yes

as well as a list of extensions.

---

### Post by puuma2 on 2007-09-02
I am having problems too I have just loaded ubuntu on to a acer laptop and loaded intel mobile drivers but picture quality on a film is like someone as turned up the contrast and turned off the color very poor quality.. can u help ?

---

### Post by garrowolf on 2007-09-02
I got the Intel driver loaded and even got compiz working for a bit. Then when I rebooted this evening it locked up and told me that it was "Reloading Postfix Configuration" and wouldn't do anything else. 

I ended up having to reinstall the OS and start over. 

Any idea what was going on?

Is there problems with compiz or the intel driver?

---

