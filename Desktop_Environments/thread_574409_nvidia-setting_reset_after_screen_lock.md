---
title: "nvidia-setting reset after screen lock"
date: 2007-10-12
forum: Desktop Environments
---

### Post by nowhere@cox.net on 2007-10-12
Hi everyone,

My screen was way too dark. After searching through admin and preferences and not finding any brightness controls, I remembered that I can control it with the nvidia-settings and the set it to load with gnome with load-settings-only flag. Problem is that every time the screensaver locks the screen, when I enter the password and return to the desktop, the nvidia-settings are removed and I need to reload them from the command prompt.

Anyone know why this is and how to fix it?

Thanks!
Eric

---

### Post by nowhere@cox.net on 2007-10-25
Hi everyone!

This is still happening. Every time the screen blanks or screensaver comes on when the desktop comes back it is very very dark. I have to re-run nvidia-settings to reset the gamma each time...

Any ideas?
Eric

---

### Post by sunexplodes on 2007-10-25
Back in my GNOME days, I had the same problem. Sadly, I never found a solution, and I don't believe there is one, short of punching in the "nvidia-settings --load-config-only" line in an Alt+F2 prompt after the screensaver shuts off.

Let me know if you do find a solution, I do play around in Gnome every now and then, and I have a mighty dark monitor.

---

### Post by nowhere@cox.net on 2007-10-29
Well thanks anyway. Right now I have a custom button on a panel to do that very thing. If I figure anything out I will post here again. 


Eric

---

### Post by nowhere@cox.net on 2007-12-01
Just bumping this. 

I still have not found a solution. Is there an alternative to using nvidia-settings? I can't find a way to get my screen light enough without it...

Thanks,
Eric

---

### Post by chrx on 2007-12-08
xscreensaver seems to be ok.

---

### Post by nowhere@cox.net on 2007-12-11
To clarify, what you are saying is that you have nvidia-settings loaded and when you exit from xscreensaver the setting stick? 

For me the settings seem to be cleared every time the screensaver fires off then I return.

Eric

---

### Post by chrx on 2007-12-13
yes. i had the same problem with gnome screensaver.
but i installed xscreensaver instead, and it doesnt reset nvidia-settings for me.

---

### Post by nowhere@cox.net on 2007-12-19
Ok thanks! I will try that one tonight and post the results.

Eric

---

### Post by mannheim on 2007-12-19
Another possibility: have you tried putting a "gamma" line in xorg.conf. It should go in the "Monitor" section. See "man xorg.conf". I don't know if this will work.

---

### Post by mannheim on 2007-12-19
I'll take a guess at why this is happening. When gnome-screensaver kicks in, it first fades the screen to black. Perhaps this is done by adjusting the gamma. After that, gnome-screensaver maybe resets the gamma to "normal", unaware that "normal" might not be the same for all users.

EDIT: This seems to be a known bug, for which a patch exists. See [http://bugzilla.gnome.org/show_bug.cgi?id=342850]("http://bugzilla.gnome.org/show_bug.cgi?id=342850"). It may be that a workaround is to kill gnome-screensaver and then restart it **after** running nvidia-settings. The bug is that gnome-screensaver remembers the value of gamma **at the time that gnome-screensaver is launched**, not at the time that the screensaver is activated.

---

### Post by nowhere@cox.net on 2007-12-31
HEY THANKS!
The Gamma setting in the monitor sections of my xorg.conf file seems to have done the trick. I set it to 2.2, disabled the nvidia-settings in the session dialog in gnome and I get a nice bright screen on reset. Previewing the screensaver does not reset the brightness so now I just need to wait for the screensaver to pop on normally to see but I suspect this is solved!

Thanks for the tip!

Eric

---

### Post by nowhere@cox.net on 2008-01-23
Just a quick update on this issue:

I am no longer using the nvidia-settings to set the gamma, just the gamma options line in xorg.conf and it is a fine work around.

I have however started using Argyll to load my monitor calibration ICC profiles and I have the same problem here. ICC profiles seem to be unloaded when the gnome screensaver is ended.  I have not had time to try the xscreensaver yet. It's very low on the to-do list.

If anyone has a quick work around or fix in the meantime I would LOVE to hear about it!

Cheers!
Eric

---

### Post by TheValk on 2008-01-26
I had the problem of nvidia-settings not sticking.
I put the command nvidia-settings -l,  (this is a small L), into my Sessions Manager and raised the priority from the default 50 to around 20 to get it in early.
Works for me. :)

---

### Post by Nando777 on 2008-02-01
TheValk 

You are a legend, I love when there is a post and there is a bunch of people coming with all this complicated and elaborated solutions to half solve the problem and then someone like you just solves the problem so easily ;-) 

And it's true, most problems have and should have easy solutions. But I don't get why this happens, why setting it to 20 solves the problem?

---

