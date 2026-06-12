---
title: "XGL/Compiz DVD watching"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-12
I have no problems in watching DVDs with XGL/Compiz set up, using totem.  However, I do have a problem in that the screen blanks after 10mins unless I move my mouse.  I previously had tried setting the screen blankin time to 2hours in system>preferences>screensaver, and using the brightside option to 'turn off screensaver' when the mouse is left in the bottom-right corner.  However, I suspect these are having no effect in xgl/compiz as they are not linking into the correct trigger.

So, how can I watch a dvd in xgl/compiz without having to press a button every 10mins?

---

### Post by Mike_N on 2006-07-12
I use VLC Media player and it works just fine...

---

### Post by Lunar_Lamp on 2006-07-12
Well, I'll try with VLC, maybe it's just a totem-dependant thing.

---

### Post by zitch on 2006-07-12
This issue only occurs if you setup Xgl using *Method A: Xgl Session on Login Window* like in [this help page](https://help.ubuntu.com/community/CompositeManager/Xgl).  I ended up setting up Xgl as *Method B: Make Xgl Your Standard Display Server* to avoid this issue with video; I was also using the Compiz manager pretty much exclusively anyways.

---

### Post by Lunar_Lamp on 2006-07-12
Ok, thanks.  That poses several questions:

How easy is it to convert and how do you do it?

How do I, in the future, not use compiz/xgl?  The other day I messed up my gfx card drivers, and xgl/compiz became too slow to use, so I just logged out and used standard gnome to fix it.

Are there any other pros/cons of the two methods, I hadn't realised there were any at all.

---

### Post by zitch on 2006-07-12
> **Lunar_Lamp said:**
> Ok, thanks.  That poses several questions:

How easy is it to convert and how do you do it?

I simply followed the directions for Method B.  I didn't even undo anything to get it to work.  Granted, I'd recommend finding whatever documentation you used and reverse it to undo what you did, boot into standard xorg/gnome, then do Method B, but I didn't even do this and got it working fine.

> How do I, in the future, not use compiz/xgl?  The other day I messed up my gfx card drivers, and xgl/compiz became too slow to use, so I just logged out and used standard gnome to fix it.

Gnome will run on Xgl just fine, from what I've seen.  I *should* be able to start up standard Gnome by disabling the script that runs **gnome-window-decorator** and **compiz** in my startup list (System->Preferences->Sessions->Startup Programs) then log off and log on.  I've never tested this yet.  Might be something I do when I get home this afternoon.

> Are there any other pros/cons of the two methods, I hadn't realised there were any at all.

I'm sure there's others, but I can't think of any at the moment.  The main reason I switched was because of the issue you reported here.  Otherwise, I wasn't having issues.

ADD: Reading that guide also reminded me of another issue using Method A; The **Shutdown** and **Restart** buttons are missing from the Logoff window.  

I also remember having issues of screen corruption when I simply logoff to the login screen with Method A on an ATI card whereas I now have no such issues running using Method B; I have the same problem when switching to a virtual terminal and when shutting down with either method on an ATI card.  This is ATI's fglrx driver issues, though, not a Xgl/compiz problem.

Please remember, Xgl and compiz are essentially best described as in *alpha* development.  New features are being added to it all the time, and stability will be less than ideal.  I'd say it won't be ready for general usage for another 6 months.

---

### Post by Lunar_Lamp on 2006-07-13
I am using a work around for the shutdown option.  I wrote a little bash script that shuts down the pc when I click an icon I made on my desktop.  A little messy perhaps, but it works just nicely.

I was thinking of doing something similar for the dvd watching options - write a bash script that sends a key-press to the active window every 5mins (enter key for example), and running it when I want to watch a dvd.  I'll have to look up how to do it though, as I am new to bash.

---

### Post by Lunar_Lamp on 2006-07-17
Wasn't able to find a way to solve the screen-fade problem, though I'd really appreciate some pointers.

---

### Post by adam.tropics on 2006-07-17
> **Lunar_Lamp said:**
> Wasn't able to find a way to solve the screen-fade problem, though I'd really appreciate some pointers.

Hey, I was wondering if [this howto from compiz.net]("http://www.compiz.net/viewtopic.php?id=1623") might help. It allows you to for example watch a movie, using Totem, in  openbox, whilst running xgl/compiz.See screenie below. I am too tired to sit long enough to see if it solves the screen blank issue, but I can tell you it cuts cpu usage for movies in half. (if you follow the guide, it is simpler to edit the files in gedit than some of the 'cat' commands, and still works fine. It is a little wierd though I warn you having a static...non-wobble window in amongst the mix, takes some getting used to!

---

### Post by Lunar_Lamp on 2006-07-17
I'll look into this - thanks.  A dirty workaround is still a workaround! :)
I'll post back here when I have had chance to test it out (couple of days probably).

---

### Post by Lunar_Lamp on 2006-07-24
Well, I found a very dirty workaround to fix my problem.

I added the following to the end of my xorg.conf:

```
Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

```

This means that it will never blank at all - not just when you are watching a DVD.  As I said, a pretty dirty hack, but one that works nonetheless.

---

