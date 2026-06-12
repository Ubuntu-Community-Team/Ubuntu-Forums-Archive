---
title: "xfce4 help?"
date: 2006-01-10
forum: General Help
---

### Post by LunarEclipse on 2006-01-10
Hello all,

I just installed Ubuntu two days ago and am using xfce4 (xubuntu-desktop). Now other then standard installs from aptitude & synaptic, I installed Opera using a trusted source that has worked on my other OS installations (Debian). My problem though is my menus dissappear constantly along with my background. I love xfce4, but this problem is driving me mad. Does anyone have an suggestions for me? Thanks for the help.

---

### Post by carlosqueso on 2006-01-10
Try typing ```
sudo killall nautilus
``` in a terminal and see if that helps.  Your xubuntu may be running nautilus, which is mean and takes over your desktop.

---

### Post by Czar on 2006-01-10
[QUOTE=LunarEclipse]My problem though is my menus dissappear constantly along with my background. I love xfce4, but this problem is driving me mad. Does anyone have an suggestions for me? Thanks for the help.[/QUOTE]

I've had the exact same issues with xubuntu-desktop.  xfdesktop is bugged?  One note that seems to be a temp fix is:

```
xfdesktop -reload
```

---

### Post by LunarEclipse on 2006-01-10
[QUOTE=carlosqueso]Try typing ```
sudo killall nautilus
``` in a terminal and see if that helps.  Your xubuntu may be running nautilus, which is mean and takes over your desktop.[/QUOTE]

Thank you carlosqueso, I've tried your suggestion. Unfortunatly, nautilus was not running. Maybe something else running in the background that is causing it to bug up? My best quick fix is to make new sessions, up to three so far :???: .

---

### Post by carlosqueso on 2006-01-10
Hmmmm....is there anything that you do that seems to cause it?

---

### Post by LunarEclipse on 2006-01-10
[QUOTE=carlosqueso]Hmmmm....is there anything that you do that seems to cause it?[/QUOTE]

Unfortunately no, it seems to be pretty sporadic... could it possibly be gnome programs? I use gnome terminal, though I have it open right now, and it's working fine. Btw, I haven't done much to this system yet, other then to get sound working. I have a Compaq Armada, and the BIOS was erased from it before I bought it. Is this common for menus and backgrounds to disappear?

---

### Post by carlosqueso on 2006-01-10
gnome programs shouldn't do that to your desktop since gnome and xfce both use the same framework.   It's definitely weird that they're disappearing like that...the only time I've had that happen is when nautilus is run.  Which file manager do you use?

---

### Post by LunarEclipse on 2006-01-10
I do use nautilus, but as the command I have "--no-desktop --browser" as well. I also have two nautilus windows open right now, and my menu was working, then I opened synaptic installed two programs. After the first install, my menus worked. Now the second install and it's not. LOL, ok, so now I have open Opera, Gnome Terminal, Synaptic, and the two Nautilus browsers. I tried your previous suggestion "sudo killall nautilus", but still no menus. Thanks again for your help.

---

### Post by carlosqueso on 2006-01-10
That's weird...sorry I can't help.

---

### Post by LunarEclipse on 2006-01-10
Ok, cool, thanks for trying. Its much appreciated :D

---

### Post by humanity_to_others on 2006-01-11
[QUOTE=Czar]I've had the exact same issues with xubuntu-desktop.  xfdesktop is bugged?  One note that seems to be a temp fix is:

```
xfdesktop -reload
```[/QUOTE]
this can solve your problem but do this with Alt F2 so closing terminal will not effect

---

### Post by LunarEclipse on 2006-01-11
Awesome, thanks for all the help guys :)

---

### Post by Krigl on 2006-01-15
[QUOTE=Czar]I've had the exact same issues with xubuntu-desktop.  xfdesktop is bugged?  One note that seems to be a temp fix is:

```
xfdesktop -reload
```[/QUOTE]
Thanks a lot, I had the same problem as LunarEclipse - it worked.

---

