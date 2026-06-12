---
title: "Gmone gone black only ksysguard (Alt-CTRL-DEL is set) works. HELP"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Neobuntu on 2006-07-16
What happend? I do not recall doing anything stupid. All of a sudden; at Gnome start, I see the ubuntu themed Gnome splash and it says metacity and panel (I think) but I get a black screen, no controls, no "task bar", nothing I can easily find works but the CTRL-ALT-DEL combo (I had long since set to bring up ksysgguard.)

I install kubuntu-desktop from text and I'm up with KDE (Which I may like better) but why is there so much trouble with Gnome?

I tried an update to see if any fix was afoot, but I'm already upgraded. Yep, just rechecked.

I don't even know where to start. 

Is anyone else having this problem? I did a search on Gnome here and found nothing looking relevant. 

Advice needed.

---

### Post by [S|G] on 2006-07-16
I've had similar problems with KDE before and it turned out to be an issue with permissions on some configuration files (I don't know why they changed, though). You could try this:
```

sudo chown YourUser /home/YourUser -R
sudo chmod u+rw /home/YourUser -R

```
Then try to boot into gnome again.

---

### Post by Neobuntu on 2006-07-16
That was an excellent suggestion, it simply did not work.

I am also experiencing the loss of the last (bottom) row of text in the CLI so it's quite maddening. It asks for password but I can't see that and have to do the commands over and again blind.

It was tricky getting back here via KDM and wasn't planning on having both Gnome and KDE on this machine (to keep it simple.) I'm suggesting a total newbie would go home crying at this point. :)

This is major bad mojo; priorty One type stuff, IMHO.

Why would the Gnome background and panel not show up? Obviously X is fine and other Gnome components seem to have loaded.

---

### Post by aysiu on 2006-07-16
When you're in KDE, open up Konqueror.

Go to your /home/neobuntu folder and press **Alt-V** and then **H** to show hidden files.

Then rename these folders to something else (for example, *.gnome* to *.gnome.old* or *.gnome.backup*):

.gnome
.gnome2
.gconf
.gconfd
.metacity
.nautilus

Then log out and log back in again to Gnome.

---

### Post by Neobuntu on 2006-07-16
OK that worked! You just can't beat Ubuntu support.

Thank you all!

Now, my menus are a little more clutered due to my choice of adding KDE to work around this problem.

Also, what the heck caused this? I'm not in the habit of failing to define the problem. That's dangerous.

Of course, all my panel setting (and other things I'm sure) are gone. I can deal with it, but it's a waste of time.

What's going on with the Gnome files? Why did they suddenly become toast? I've seen no evidence of hard drive error. Is this related to unkempt upgrades; because if it is, we need to track it down and kill it (make a fix for all.)

Anyone else have this lately? Ever?

Thank you again for a working solution post haste.
:-k

---

### Post by aysiu on 2006-07-16
No idea what might have caused it.

---

