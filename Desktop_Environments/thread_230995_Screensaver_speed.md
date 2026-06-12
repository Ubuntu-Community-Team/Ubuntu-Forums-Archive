---
title: "Screensaver speed?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by CBTF on 2006-08-06
I am a new ubuntu user, so things are still confusing.

I installed easyubuntu and made sure i checked the ATI drivers installation box. They *seem* to be installed.

On reboot, I set a new screensaver, but it seems no matter which saver I apply it runs extremely slow (like 2 fps). 

How can i fix this/ what could be happening?

32 bit dapper drake
AMD Athlon 64 (using 32 bit ubuntu for a reason though)
ATI radeon xpress 200
1 gig ram
200 gig hd

ty for any ideas/suggestions/solutions :)

---

### Post by malacandra on 2006-08-06
Is your /etc/X11/xorg.conf file set to the "fglrx" driver? (not "ati")?

If not, use **sudo gedit /etc/X11/xorg.conf** and find where it says 

driver   "ati" and change it to "fglrx" and save. Then reboot. (or stop the X server and gdm if you know how to do that and then restart them.)

---

### Post by CBTF on 2006-08-06
Awesome thank you for that quick fix. =D>

---

### Post by chadk on 2006-08-06
type fglrxinfo in a terminal and make sure the output doesn't look like mine: 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
That's bad.  You want to see RADEON up there and ATI drivers.

---

### Post by CBTF on 2006-08-07
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


thats what i see.. is there a solution?

---

### Post by buccaneere on 2008-01-05
chucknb@chucknb-desktop:~$ fglrxinfo
bash: fglrxinfo: command not found

chucknb@chucknb-desktop:~$ fglrx info
bash: fglrx: command not found

I want to slow my 'Polyhedra' screensaver's speed.

How?

I found four files with that name. I changed some values in 'speed' (within the already-existing parameters), tried to save, and now stuff is gone.

1) How do I restore them?
2) How do I do the original task - slow the speed?

Thanks...

PS - is the screensaver streamed? Is that why I couldn't modify it?

---

### Post by buccaneere on 2008-01-06
> **buccaneere said:**
> chucknb@chucknb-desktop:~$ fglrxinfo
bash: fglrxinfo: command not found

chucknb@chucknb-desktop:~$ fglrx info
bash: fglrx: command not found

I want to slow my 'Polyhedra' screensaver's speed.

How?

I found four files with that name. I changed some values in 'speed' (within the already-existing parameters), tried to save, and now stuff is gone.

1) How do I restore them?
2) How do I do the original task - slow the speed?

Thanks...

PS - is the screensaver streamed? Is that why I couldn't modify it?

bumpin here........

---

