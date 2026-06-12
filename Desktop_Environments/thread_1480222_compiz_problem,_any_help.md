---
title: "compiz problem, any help ?"
date: 2010-05-11
forum: Desktop Environments
---

### Post by Mr_Yaser on 2010-05-11
i am new in Linux , and i just installed ubuntu 10.04 on my hp pavilion dv6. After installing compiz, i can't see a shortcut for it in System>>Preferences. Anyway, when i try to type compiz in the terminal i grt this outpot.

> compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x4a00081 (Synaptic P); these messages lack timestamps and therefore suck.
Window manager warning: last_focus_time (4936319) is greater than comparison timestamp (4936262).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...any idea how to solve this problem ?
thanx in advance

---

### Post by proggy on 2010-05-11
sudo apt-get install compizconfig-settings-manager
It should now be in Preferences

---

### Post by Mr_Yaser on 2010-05-11
thanx a lot , that work for me
now i can open compiz, but the problem now is, when i activate any compiz function, it want to change any thing, in other words, the compiz functions don't work probably, (((don't work at all)))

i asked about the problem, and i knew that i have to go to appearance >> visual effects & activate it, but when i try to do so, i got an error message says: "Desktop effects could not be enabled"

how can solve this problem ?

---

### Post by proggy on 2010-05-11
You need to get the drivers for your graphics card.
You didn`t mention what card you had .
Some older cards don`t render compiz very well

---

### Post by Mr_Yaser on 2010-05-11
thanx for the replay

my graphic card is an ATI Radeon HD 4650 [ 1GB dedicated ]

anyway, i found in System >> Prefrances >> ATI catalyst control center
but when i try to open it i got this message

 > 
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
any idea ?

---

### Post by proggy on 2010-05-11
Go to System > Administration >Hardware drivers, it will search for suitable drivers if they are available , if so it will ask for your password to install.
Did you reboot after installing your drivers?

---

### Post by Mr_Yaser on 2010-05-11
when i do so, its download and install the drivers for a while, then it's open for me and it's says that my graphic card is activated, but when i try to open >> System >> Prefrances >> ATI catalyst control center, I still get the same message

even after restarting my computer

any idea ?

---

### Post by proggy on 2010-05-11
Try un installing the proprietary drivers and use the open source ones

---

### Post by Mr_Yaser on 2010-05-13
> **proggy said:**
> Try un installing the proprietary drivers and use the open source ones

i tried that solution but it's seams like it didn't work.
my graphic performance became very slow and bad, when i open a DVD or a high definition video it dosent seams life, the picture sticks, while the audio in a very good condition !

any help ?

---

