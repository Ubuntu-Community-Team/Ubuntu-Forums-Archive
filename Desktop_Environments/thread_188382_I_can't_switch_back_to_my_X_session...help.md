---
title: "I can't switch back to my X session...help"
date: 2006-06-04
forum: Desktop Environments
---

### Post by ki1022 on 2006-06-04
I recently installed ubuntu and have run into a problem.  When it boots up I graphically login and it works fine.  Then I will press CTRL+ALT+F1(or F2, F3, F4, etc.) and switch ttys.  If I try to switch back to my x session by pressing CTRL+ALT+F7, it doenst work.   The screen flickers like its switching resolutions, but its all black and nothing happens. 

Has anyone else experienced this?:confused:

---

### Post by professor_chaos on 2006-06-04
Yes, and I dont have a solution, but a work around.

You can stop and start gdm (gnome desktop manager) from the commandline by typing ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

or you can start your desktop by typing

```
startx
```

Either of these, is not likely going to take you back to your previous session, but instead start a new one.

---

### Post by Anduu on 2006-06-04
[QUOTE=ki1022]I recently installed ubuntu and have run into a problem.  When it boots up I graphically login and it works fine.  Then I will press CTRL+ALT+F1(or F2, F3, F4, etc.) and switch ttys.  If I try to switch back to my x session by pressing CTRL+ALT+F7, it doenst work.   The screen flickers like its switching resolutions, but its all black and nothing happens. 

Has anyone else experienced this?:confused:[/QUOTE]

Maybe a typo on your part or I am remembering wrong but isnt it supposed to be just [COLOR="Red"]ALT+F7[/COLOR] to return?

---

### Post by shrift on 2006-06-04
[QUOTE=Anduu]Maybe a typo on your part or I am remembering wrong but isnt it supposed to be just [COLOR="Red"]ALT+F7[/COLOR] to return?[/QUOTE]
You are both kind of right. If your in your desktop, you must use ctrl+alt+FX, to switch. But if your in a differenty tty, then just alt+FX works.

---

### Post by ki1022 on 2006-06-04
Either way, they both dont work...

---

### Post by ki1022 on 2006-06-04
*bump* any more ideas...?

---

### Post by arch stanton on 2006-06-04
I'm having the exact same problem..  have been messing around with xorg.conf, as I figured that was the problem, but have accomplished nothing so far (besides not being able to play Enemy Territory any more ;[  )

---

### Post by Corvillus on 2006-06-04
Just out of curiosity, have you tried all the X terminals Ctrl-Alt-(F7,F8,F9,F10,F11,F12)? In some cases I've had X start on a terminal other than the default Ctrl-Alt-F7 one.

---

### Post by ki1022 on 2006-06-05
yeah. tried everything...

I also just wanted to mention that I am using my built-in display adapter from my intel motherboard if that makes a difference.

---

