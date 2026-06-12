---
title: "Missing windows controls / Visual Effects issues"
date: 2009-01-25
forum: General Help
---

### Post by TheViLliN on 2009-01-25
Hello all.  I'm having some troubles with my desktop environment and am looking for some direction in resolving my issues.  I been searching high and low to no avail. It seems also a little tricky searching this exact hangup.  



This issue pertains to mostly my visual effects but I even have trouble with no visual effects at all.  

When I boot into my desktop, every time all my windows have no window controls (ie// i can't minimize, maximize and close, or even move the window) I usually get them back by enabling Visual Effects but slowly I've been getting more inconsistency happening.   

When I check System>-Appearances>-Visual Settings it is always on "None" after a reboot. 

BIG KICKER:When I select normal or extra, the system often hangs (sometimes not). My conky stops, my system monitor does not read. Log files don't see to be accessible. Even the terminal has issues.  It loads but I cant input. Usually executing a reboot to see if it will have the same problem next time.. 

Oddly enough. I sometimes get a message "desktop effects could not be enabled". Sometimes the Visual Settings window does not hang but sometimes it might. Sometimes I have the window controls back sometimes not.

My Nvidia driver(177) is active and I have gone threw the Compiz settings many time's. I'm running Gnome, and it is Ubuntu 8.10. 

I'm stumped and this lengthy trouble has been impeding my other tasks.

Anyone who's opinion's could point me in the right direction here would surly have my most appreciated gratitude. ;)

---

### Post by gettinoriginal on 2009-01-26
Can you post your /etc/X11/Xorg.conf file ??

---

### Post by TheViLliN on 2009-01-27
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Thx

---

### Post by gettinoriginal on 2009-01-27
Have you tried typing in terminal:
```
Compiz --replace
```
Everything is fine with your Xorg file, identical to mine.  Do you have Compiz Fusion Icon installed??  Compiz Fusion Icon allows you to switch "Window Manager" and "Window Decorator" to your needs at the time.  And are you using Emerald as your window decorator??  Emerald renders better with compiz.  Both fusion-icon and emerald can be installed either by CL or Synaptic.

---

### Post by TheViLliN on 2009-04-25
Apologies for the lack of updates with the issue.

The problem remained unresolved.  It appeared to be a correlation with the Nvidia driver(180) and some configuration. I don't think the driver was properly being accessed. Unfortunately the any upgrades  to the new or other driver(s) or software reinstall failed in resolving the issue.

My only work around was to reapply the "normal" setting  under the Visual Settings after every time I reloaded X (Gnome).  This did bring back window controls but still gave me the error. And still lacked any visual enhancements. 

The issue has not resurfaced under 9.04.

Thank you.

---

