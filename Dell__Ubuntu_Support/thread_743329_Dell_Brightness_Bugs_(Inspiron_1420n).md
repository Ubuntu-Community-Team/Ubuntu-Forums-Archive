---
title: "Dell Brightness Bugs (Inspiron 1420n)"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by aidave on 2008-04-02
Brightness
- The brightness feature doesn't behave properly
- It will constantly turn extremely dim, even when "dim" is unchecked in power management. 
- Starts on 1 brightness with battery
- Adjusts to 1 brightness when going into Power Management applet (why? cant see anything that way)
- BIOS brightness set to 8
- Goes to 1 brightness on battery, after a minute idle, does not come back with mouse movement, without manual adjustment

---

### Post by aidave on 2008-04-02
Well I noticed a quirk in the Power Management applet, that was the sliders are not the same for Plug and Battery.  One is inverted!  Thats wierd, but ok.  Im just going to max out the brightness at all times to avoid these issues.

Is there any way to adjust the time to dim?

---

### Post by drsaamah on 2008-04-04
This isn't exactly a Dell problem.  The only issue with the Dell is that the new models (for whatever reason) is that the brightness controls are no longer purely hardware controlled... they work in conjunction with the OS (which is why you get the brightness control applet everytime you Fn+up or Fn+down).
So the issue is that the new Gnome has an option for brightness control enabled by default.  Here's the fix:
Type into a terminal:
```
saam@euler:~$ sudo gconf-editor
```
It will prompt you for your password, so type that in.  You will get the gnome-configuration-editor.  On the left side of the window it has a variety of categories.  From this list select "apps" -> "gnome-power-manager" -> "backlight".
Now on the menu on the right, UNselect the options titled "idle_dim_ac" and "idle_dim_battery".  The "enabled" option is to keep the dim levels different for battery and AC power, so its usually helpful, but you can uncheck that if you want.
Now just close the editor window, and everything should be working fine!!  I'm subscribing to the thread, so let me know if there are any other questions!!

---

### Post by aidave on 2008-04-09
Thanks, that helped.

I have another puzzler.  Now that I am using Hardy Beta (because it works with suspend/resume), there is a glitch with the brightness.

When I pressed Fn-BrightUp or Fn-BrightDown, it will jump basically between 3 modes: lowest dim, medium dim, highest dim.  Except I can see it skipping dim levels to get to that medium dim.  It also doesnt go to the same medium dim based on coming up from low, or down from high.  

Is there a setting for "how much" dim to move by when pressing these keys?

---

### Post by danf_1979 on 2008-04-10
I want to know the same thing as aidave. Anyone?

---

### Post by afunix on 2008-04-11
I have the same issue with Dell Inspirion 1520 and KUbuntu Hardy.
And we're not alone: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/207473](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/207473)
Maintainers just ignore us for now.

---

### Post by drsaamah on 2008-04-11
This might just be a beta thing.  I remember that same exact thing happenning when I was running Hardy.  Unfortunately I can't play around it with it right now, because I reverted to Gutsy since my wireless was too sporadic on Hardy and I can't afford that during the school quarter.  I'm sure this will be fixed within the next week or so.

---

### Post by afunix on 2008-04-11
I've solved problem by putting "blacklist video" in /etc/modprobe.d/blacklist

---

### Post by aidave on 2008-04-11
> **afunix said:**
> I've solved problem by putting "blacklist video" in /etc/modprobe.d/blacklist

Can you explain this a bit more please?

What are the side effects of blacklisting video?

edit: I dunno what it does, but I tried it, and it does work!  thanks

---

### Post by bull8042 on 2008-04-16
Well, I can confirm that adding "blacklist video" to /etc/modprobe.d/blacklist does in fact work for my Dell E1505 running Gutsy!
I can control my brightness with the function keys again.
Thanks for the insight.  :guitar:

---

### Post by canadianbaptist on 2008-04-28
> **bull8042 said:**
> Well, I can confirm that adding "blacklist video" to /etc/modprobe.d/blacklist does in fact work for my Dell E1505 running Gutsy!
I can control my brightness with the function keys again.
Thanks for the insight.  :guitar:

Can you tell me which "blacklist" file to put this in? There are a few files with blacklist.... and one with just "blacklist" Can you tell me the one you are to put it in? THanks

---

### Post by jdeslip on 2008-05-11
This worked for me to.  Just add a new line with 'blacklist video' to the file suggested above.  

Has anyone noticed any concequences of this?  I noticed that gnome now seems to ignore the values I set gconf-editor and simply goes directly to the lowest brightness when I unplug the ac on my dell 1420n.

---

### Post by darkwoofe on 2008-05-14
Didn't help with the brightness controls on my Dell Inspiron 1501, but it didn make it so that suspend works now and hibernate almost works. I keep getting an error that says there isn't enought memory when I try to hibernate, but it takes me back to the main screen and has me sign in again.

---

### Post by Orion2000za on 2008-05-21
> **darkwoofe said:**
> Didn't help with the brightness controls on my Dell Inspiron 1501, but it didn make it so that suspend works now and hibernate almost works. I keep getting an error that says there isn't enought memory when I try to hibernate, but it takes me back to the main screen and has me sign in again.

If your swap is not twice the size of RAM then hibernate will not work, could that be the problem?

---

### Post by darkwoofe on 2008-05-21
That seems to be it. Thanks for pointing this out to me Orion!

---

