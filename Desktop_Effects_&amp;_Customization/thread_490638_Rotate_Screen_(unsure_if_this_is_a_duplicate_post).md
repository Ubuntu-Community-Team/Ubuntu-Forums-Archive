---
title: "Rotate Screen (unsure if this is a duplicate post)"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by DishBreak on 2007-07-02
Apologies if i'm double-posting.

I'm a convert from Windows XP Pro, now using Ubuntu. I have a 20" Samsung SyncMaster 204b connected to DVI with a Radeon 9250. 

My main question is how to rotate a screen between portrait and landscape position. I was able to do it with a utility called MagicRotation in XP. What are my options in Ubuntu?

Thanks in advance.

---

### Post by Mr Greencastle on 2007-07-02
If you go to System >> Preferences >> Screen Resolution
You should see an option to change the screens rotation.

Hope that helps!

Mr Green

---

### Post by DishBreak on 2007-07-03
The rotation box is knocked out for me. Is there any way I can use a driver to rotate the screen?

---

### Post by sistoviejo on 2007-12-21
> **DishBreak said:**
> The rotation box is knocked out for me. Is there any way I can use a driver to rotate the screen?

Try this:

xrandr -o normal
xrandr -o left
xrandr -o right
xrandr -o inverted

It should take effect as soon as you enter it.
No restarting needed.

---

### Post by revolutio on 2008-01-24
> **sistoviejo said:**
> Try this:

xrandr -o normal
xrandr -o left
xrandr -o right
xrandr -o inverted

It should take effect as soon as you enter it.
No restarting needed.
This is a bit of thread necromancy but I have the same monitor and the same concern which is that I'd like to have a utility like MagicRotation.  There is no option even present for rotating in an of the system preferences.  In my case I have a Radeon 9800 pro.

When I tried to rotate the screen left using those commands (what is needed to use my monitor vertically) nothing happened.  The verbose output was this:

```
 SZ:    Pixels          Physical       Refresh
*0   1600 x 1200   ( 408mm x 306mm )  *60  
 1   1280 x 1024   ( 408mm x 306mm )   75   60  
 2   1280 x 960    ( 408mm x 306mm )   60  
 3   1152 x 864    ( 408mm x 306mm )   75  
 4   1024 x 768    ( 408mm x 306mm )   75   70   60  
 5    832 x 624    ( 408mm x 306mm )   75  
 6    800 x 600    ( 408mm x 306mm )   72   75   60   56  
 7    640 x 480    ( 408mm x 306mm )   75   73   67   60  
 8    720 x 400    ( 408mm x 306mm )   70  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
Setting size to 0, rotation to left
Setting reflection on neither axis
```

---

### Post by miceagol on 2008-01-27
I'd like to have this function too. A must when you have a 24 inch monitor. :) When I tried the command suggested above, I got this:
```
username@localhost:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```
What does it mean? Do I have to do some xorg.conf editing to get the Rotation setting in the Screen Resolution dialog to work?

Graphics card: nVidia GeForce 8800 GTS
Monitor: Dell 2407WFP

---

### Post by meastp on 2008-01-29
> **miceagol said:**
> I'd like to have this function too. A must when you have a 24 inch monitor. :) When I tried the command suggested above, I got this:
```
username@localhost:~$ xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```


+1  Nvida Quadro 140M / Gutsy

---

### Post by revolutio on 2008-02-01
Anyone have any ideas on this?  I'd really like to be able to actually use this feature of my monitor.

---

### Post by Hilko on 2008-02-15
I have the same problem and get the same error after typing $xrandr -o -right
I really hope someone can help us..

---

