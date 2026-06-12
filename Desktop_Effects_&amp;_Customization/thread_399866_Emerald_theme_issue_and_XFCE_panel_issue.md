---
title: "Emerald theme issue and XFCE panel issue"
date: 2007-04-02
forum: Desktop Effects &amp; Customization
---

### Post by FuturePilot on 2007-04-02
So I decided to try our the XFCE desktop and I've got Beryl and XGL installed on Edgy. However I have two small but rather annoying issues. The first is that when I try to change the Emerald theme it won't change, it just stays on the one it's already on. I've tried reloading the window manager but it doesn't make a difference. If I log out and then log back in it will change.

The other is that the XFCE panels change to semi transparent when I load Beryl. But when I mouse over them they change back to opaque. Any ideas?

---

### Post by reacocard on 2007-04-02
> **FuturePilot said:**
> The other is that the XFCE panels change to semi transparent when I load Beryl. But when I mouse over them they change back to opaque. Any ideas?

Yeah, I hated that too. The solution is to edit ~/.config/xfce4/panel/panels.xml and set both transparency and activetrans to 0 for each of your panels. Note that you must do this with the xfce panels not running, otherwise they'll overwrite any changes you make when they exit.

---

### Post by FuturePilot on 2007-04-02
All right thanks! That did the trick.:)  Now just to get Emerald to switch themes when I tell it to. Hmmm

---

### Post by garyedwardjohnston on 2007-04-09
I'm interested in this solution too :)

---

### Post by FuturePilot on 2007-04-10
The problem with Emerald seems to be related to using XGL. If I don't use XGL it works fine. But I need XGL or my computer freezes with Beryl.

---

### Post by garyedwardjohnston on 2007-04-10
I've gotten this to work now and I'm not exactly sure what I did but I will try explaining it.

I formatted my system and used Ubuntu Ultimate 1.3.  This made my system reboot when I started Beryl.

Next I installed my Nvidia card through Add/Remove programs (not Automatix, Synaptic, Envy or anything else).  I tried the normal (not legacy) installation and it came with an instruction after installation and I did it also.  (Who knew you should read all of the bits in terminal.  Now I know.

Next I installed Beryl again manually through the terminal as per the Beryl site.  I simply followed the instructions for installation even though it was already installed.

Now it works!

I'm not really a techie so this explanation is not thorough.  I also did not know which part actually made it work, but alas it does.  Sorry for my lack of exactness in this post, I know you are probably looking for it as I was.

Beryl is worth the effort though.

---

