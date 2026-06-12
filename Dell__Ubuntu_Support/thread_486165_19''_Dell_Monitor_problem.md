---
title: "19'' Dell Monitor problem"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by cje on 2007-06-27
Hi, 
today, I've switched from a 17'' CRT Monitor to a Dell 19'' CRT Monitor.
But, when I turn on ubuntu the screen (not the login screen) has been divided into two screens;
- the upper 2/3 of the screen is the 2/3 of the normal ubuntu screen
- the lower 1/3 of the screen is 1/3 of the upper normal ubuntu screen
So, I see the upper 1/3 of the screen twice, the mid 1/3 of the screen ones, and not the lower 1/3 of the normal ubuntu screen ;)

If I try to change to a higher resolution the screen picture gets normal, but my Dell monitor doesn't seem to like it (the screen is shivering).

Any ideas of what to do?

---

### Post by apel_2804 on 2007-06-27
try to adjust refresh rate

---

### Post by cje on 2007-06-28
Thx for your reply apel_2804
anyway, the Dell monitor has a refresh rate between 50-60Hz. So, I haven't tested outside this range. Do you have any suggestions or experience with that?

---

### Post by apel_2804 on 2007-06-28
75/80 Hz will not harm your monitor

---

### Post by cje on 2007-06-29
for your information; 70Hz went ok.
thanks and regards

---

### Post by cje on 2007-06-30
The problem return when my son started a Java game...... 
So, the situation is
1) the login screen has always been ok
2) the desktop is ok
3) the java game has the same problem as described above. 

I've tried to change the resolution and the refresh rate w/o success.
Any more ideas?

---

### Post by cje on 2007-07-02
Anyone who know a solution?

---

### Post by geirha on 2007-07-02
I suggest you try setting the horizontal sync and vertical refresh rate manually.

You should find those values in the monitor's manual. If you don't have the manual, you might have luck searching with the modelnumber at Dell's site or at [http://monitorworld.com/search_home.html](http://monitorworld.com/search_home.html)

To set the actual values, open a terminal and type: 
```
sudo cp /etc/X11/xorg.conf{,.backup} # A backup just to be sure
sudo gedit /etc/X11/xorg.conf
```
browse down to the "Monitor" section and insert the values for HorizSync and VertRefresh, like in this example of my 19" LCD
```

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    22.0 - 82.0
	VertRefresh  50.0 - 76.0
	Option	    "DPMS"
EndSection
```

The X server needs to restart, so either restart the computer, or log out, and hit CTRL+ALT+Backspace on the login screen (should go black for a while and then come back)

And if X don't like these new values, and won't start, hit CTRL+ALT+F1 to get to a console, copy back the backuped copy and restart the login screen.
```

sudo cp /etc/X11/xorg.conf{.backup,}
sudo /etc/init.d/?dm restart

```

---

