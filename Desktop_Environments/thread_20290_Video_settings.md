---
title: "Video settings"
date: 2005-03-16
forum: Desktop Environments
---

### Post by user_stu on 2005-03-16
My monitor can do 80Hz, but the thing is flickering at 60. How can I change this (cant see any obvious entey in x86config-4 file.

Is there a way to rerun the setup (I must have made a wrong selection during install....?)

---

### Post by Buffalo Soldier on 2005-03-16
Go to the Top Panel. Click on Computer -> System Configuration -> Screen Resolution -> choose refresh rate from drop-down list -> Apply

---

### Post by user_stu on 2005-03-16
[QUOTE=Buffalo Soldier]Go to the Top Panel. Click on Computer -> System Configuration -> Screen Resolution -> choose refresh rate from drop-down list -> Apply[/QUOTE]

Tried that. The trouble is that there are no options for refresh rate (I get a drop down list for resolutions, but not for refresh).

---

### Post by Buffalo Soldier on 2005-03-16
What is the content of your */etc/X11/XF86Config-4* file?

---

### Post by iomicifikko on 2005-03-16
[QUOTE=user_stu]My monitor can do 80Hz, but the thing is flickering at 60. How can I change this (cant see any obvious entey in x86config-4 file.

Is there a way to rerun the setup (I must have made a wrong selection during install....?)[/QUOTE]
 ---> IM A NEWBIE <---

Section "Monitor"
	Identifier	"Compaq"
	HorizSync	31.5-70.0
	VertRefresh	50.0-120.0     <------------------THIS ONE

ps: this is my personal config so your values should be different

then u should be able to change also refresh rate in the graphical window about screen

be careful couse u can damage your monitor using values not allowed

byez

---

### Post by user_stu on 2005-03-26
[QUOTE=iomicifikko]---> IM A NEWBIE <---

Section "Monitor"
	Identifier	"Compaq"
	HorizSync	31.5-70.0
	VertRefresh	50.0-120.0     <------------------THIS ONE

ps: this is my personal config so your values should be different

then u should be able to change also refresh rate in the graphical window about screen

be careful couse u can damage your monitor using values not allowed

byez[/QUOTE]
 Thanks. After I worked out how to edit this config file things seem finw.

---

