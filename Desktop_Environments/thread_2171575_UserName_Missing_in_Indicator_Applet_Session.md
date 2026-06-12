---
title: "User/Name Missing in Indicator Applet Session"
date: 2013-08-31
forum: Desktop Environments
---

### Post by BarryD9545 on 2013-08-31
Hey all-

Running 13.04 Gnome Fallback.

When I first add Indicator Applet Session to my panel, it only shows the icon for the drop down menu, not the User/Name.
If I move the applet from one panel to another, the User/Name appears.
A LogOut or Reboot makes it vanish again, and I need to move the applet from one panel to another to make the name show again.

Any Help?

Thanks!

---

### Post by ibjsb4 on 2013-08-31
Ok, weird

I think what your talking about is the 'user menu' thats in the indicator-applet and part of indicator-applet-complete.

Try reinstalling the indicator-applet [in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#In_Gnome").

```
sudo apt-get install --reinstall indicator-applet
```

If that doesn't work, see if it will reset in terminal without moving it.

```
killall gnome-panel
```

---

### Post by Frogs Hair on 2013-08-31
Show real name in panel can be toggled on and off in the dconf editor under apps > indicator session .

---

### Post by d-cosner on 2013-08-31
Show real name in panel can be toggled on and off in the dconf editor under apps > indicator session . 

Hey, thanks for this little gem! Now I have Unity in 12.04 looking nicer and more like the current version. The panel looks much cleaner now and I saw no reason to have my full name displayed. Anyway, thanks a lot for the tip.

---

### Post by BarryD9545 on 2013-08-31
> **ibjsb4 said:**
> Ok, weird

I think what your talking about is the 'user menu' thats in the indicator-applet and part of indicator-applet-complete.

Try reinstalling the indicator-applet [in terminal]("https://help.ubuntu.com/community/UsingTheTerminal#In_Gnome").

```
sudo apt-get install --reinstall indicator-applet
```

If that doesn't work, see if it will reset in terminal without moving it.

```
killall gnome-panel
```

No, it's not the indicator-applet-_complete_, this is the indicator-applet-_session_,
I'm using it instead of the complete (I like the clock elsewhere).

I did try the re-install but it didn't make a difference..

Here are images so you can see which applet I'm referring to, and with/without the name.

On initial add or after
restart/relogin:
      [ATTACH=CONFIG]245882[/ATTACH]

After moving the applet to
another panel and back again:
      [ATTACH=CONFIG]245881[/ATTACH]

I've seen the toggle in dconf, but I'm of the unfounded belief that if the show-real-name-on panel toggle is off,
that it should always show the user name, and not just after I move it between panels, eh?

---

### Post by ibjsb4 on 2013-08-31
I installed session just to see if I could duplicate your problem.  Couldn't do it, works ok for me.  Did you try reinstalling indicator-applet-session? 

On mine you will notice I have an extra icon to the right of name (host).  I have seen dumb things work before :)  Place another icon/launcher to the right of your session, see what happens.

[ATTACH=CONFIG]245883[/ATTACH]

---

### Post by BarryD9545 on 2013-08-31
> **ibjsb4 said:**
> I installed session just to see if I could duplicate your problem.  Couldn't do it, works ok for me.  Did you try reinstalling indicator-applet-session? 

On mine you will notice I have an extra icon to the right of name (host).  I have seen dumb things work before :)  Place another icon/launcher to the right of your session, see what happens.

[ATTACH=CONFIG]245883[/ATTACH]

You have the applet called (in the Add Panel) User Menu. I'm referring to Indicator Applet Session.
The call out next to your username is the tell. Mine has a power gear.
But I did try the "icon to the right" trick...no luck.

I did try the re-install on my applet (session), I didn't make that clear above.

it's the little things that make me crazy. <sigh>

---

### Post by ibjsb4 on 2013-08-31
> **BarryD9545 said:**
> You have the applet called (in the Add Panel) User Menu. I'm referring to Indicator Applet Session.
The call out next to your username is the tell. Mine has a power gear.

Yes, i do understand.  The one in red next to my user menu is the 12.04 version of Indicator Applet Session, which like I said, works ok.  Unlike yours :(  I am out of ideas, if I think of anything else I will post back.  Good luck

[ATTACH=CONFIG]245886[/ATTACH]

---

### Post by BarryD9545 on 2013-09-01
I have 12.10.5. 

That must be why yours (which doesn't look red on my side)  has a man icon, and mine has a gear...eh?

Thanks for trying, though.

---

