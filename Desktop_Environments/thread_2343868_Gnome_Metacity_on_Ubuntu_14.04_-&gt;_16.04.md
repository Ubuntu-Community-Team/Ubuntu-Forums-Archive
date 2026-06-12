---
title: "Gnome Metacity on Ubuntu 14.04 -&gt; 16.04"
date: 2016-11-20
forum: Desktop Environments
---

### Post by RogerDavis on 2016-11-20
I have Gnome Metacity installed with Ubuntu 14.04.  I have all the settings just as I want them.  I have another very similar machine with 16.04 and also Gnome Metacity, but the settings are not quite want I want, and I can't get the last items set as there doesn't seem to be any way.  

So the real question - can I transplant the settings from Gnome Metacity on the 14.04 machine to he 16.04 machine?

If so, how?

Thanks!

---

### Post by CantankRus on 2016-11-20
Maybe not if the applications have changed.
Which settings do you mean?

---

### Post by RogerDavis on 2016-11-26
I mean all the desktop settings and colors, and the buttons now at top right.  I want large square, normal color buttons in the apps, not the round ones, and not pumpkin orange.

Thanks!

---

### Post by Frogs Hair on 2016-11-28
Are you using the same themes on both devices ?  16.04 does use a different version of Gnome ,so there are differences.

---

### Post by RogerDavis on 2016-11-29
No, and that is the problem.  I'd like to use ALL the settings from 14.04 on 16.04.  Or maybe even use the 14.04 Metacity on the machine with 16.04.

I have everything I want on the 14.04 machine, I can't get it on the 16.04 machine.

---

### Post by Frogs Hair on 2016-11-29
A screen shot may help to show the differences in the settings you describe. 14.04 uses Gnome 3.14 and 16.04 uses Gnome 3.18. Gnome continues to change/simplify basic applications in each new version.

---

### Post by RogerDavis on 2016-11-30
I'm not at the location of the 16.04 machine right now, but this shot show the major thing I'm trying to duplicate - the window controls at the top right.  These are square, and look like they belong.  On the 16.04 machine they are round and look really out of place.  Yeah, big deal, but it's just plain annoying that I can't fix them.  I think way back when  someone gave me some terminal commands that fixed this one.

I think there were some background and feature colors that I couldn't get adjusted as I really wanted either, but that's been a while.

At one time I updated Ubuntu on this machine to 16.04 (but had to go back after I screwed it up), and Gnome followed along, keeping these settings I have here.  So it makes sense that I should be able to get all this onto the 16.04 machine.

Thanks!

OK, I give up - I can't figure out how to attach this file.  I can get to where it should put it in the window, but all I can get is the name.  No upload happens.
/home/roger/Downloads/Screenshot from 2016-11-29 21:17:01.png
Maybe this will work.
[IMG]/home/roger/Downloads/Screenshot from 2016-11-29 21:17:01.png[/IMG]
Well, guess not...

---

### Post by Frogs Hair on 2016-11-30
Use the paperclip symbol in reply box tools to upload a thumbnail.

---

### Post by RogerDavis on 2016-12-01
That doesn't work.  I can get the selection box, but it won't bring the screen shot into it.  It is a proper file type (png)

Trying jpg - [ATTACH=CONFIG]272479[/ATTACH]

Did that work?  I don't see anything except the above.  OK, now I see it.

---

### Post by Frogs Hair on 2016-12-01
I'm seeing the Adwaita theme in the screen-shot and what you are describing with orange buttons is the Ambiance theme. Go into appearance settings in the control panel make sure you have the Adwaita applied on both devices.

---

### Post by RogerDavis on 2016-12-01
I'm at the "orange button" machine now.  I tried all the theme settings, and all of them have the pumpkin orange button.  Also, the Adwaita gives me a black background I don't like, which is probably why I had selected Ambiance.

Again, this is 16.04 Ubuntu.

I've installed all the preference adjustment apps I can find, but I still can't get what I want.  I'm presuming that this button shape and color is beyond the control of themes?

Is there a "Harry Potter" spell I can enter in Terminal and get the buttons like I want?

Thanks!

---

### Post by Frogs Hair on 2016-12-02
> I'm presuming that this button shape and color is beyond the control of themes? No, it's a feature of the Ambiance and Radiance themes.


This command will change the theme to Adwaita. If Gnome Tweak is installed rather than Unity Tweak be sure the dark theme option isn't checked. 

```
gsettings set org.gnome.desktop.interface gtk-theme adwaita
```

---

### Post by RogerDavis on 2016-12-08
Both are installed.

How do I backtrack if this screws up the display?

Here's another screen shot  showing both the theme and the pumpkin

[ATTACH=CONFIG]272602[/ATTACH]

---

### Post by Frogs Hair on 2016-12-08
You would use the same command with the desired theme name at the end. I tested the command, but haven't used the Flash-back Gnome sessions for a while.

Example: 
```
gsettings set org.gnome.desktop.interface gtk-theme ambiance
```

---

### Post by Frogs Hair on 2016-12-08
It looks like you have the adwaita theme applied, but the the dark theme setting _might_ be applied in the the tweak tool. The Window theme is definitely ambiance or radiance.  

There is another command specifically for the window theme/ title bar section you might try. 
```
gsettings set org.gnome.desktop.wm.preferences theme adwaita 
```

---

