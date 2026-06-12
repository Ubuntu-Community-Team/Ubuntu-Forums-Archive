---
title: "CompizConfig/Advanced Desktop Effects = UNDO all changed settings to DEFAULTS??"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by FilmAficionado on 2007-11-23
OK so I couldn't resist. I had to try advanced desktop effects.
Now all my settings that were oh so perfect from my default installation of Ubuntu have gone awry. Everything is weird, from the fade in and fade out times to the minimization effects and I've wasted about two hours trying to get it back but I cannot.

How do I RESET so that all my settings are that of an original install? Or do I have to reinstall Ubuntu from scratch (hope not?!)...

Thanks in advance.

BTW, I tried System > Preferences > Advanced Desktop Effects Settings and clicked PREFERENCES > RESET TO DEFAULTS

It does reset things, but they are DEFINITELY not my defaults from before I installed this horrid thing.

Please help!

---

### Post by rainwalker on 2007-11-23
System > Preferences > Appearance
Under the "Visual Effects" tab, you should have 4 options to choose from: None, Normal, Extra, and Custom
If I'm correct, it will be set to "Custom". Change it to "Normal" or "Extra", depending on how fancy you want it. Those are the default configurations.

---

### Post by Forlong on 2007-11-24
> **rainwalker said:**
> System > Preferences > Appearance
Under the "Visual Effects" tab, you should have 4 options to choose from: None, Normal, Extra, and Custom
If I'm correct, it will be set to "Custom". Change it to "Normal" or "Extra", depending on how fancy you want it. Those are the default configurations.
"Normal" is exactly the same as 
> **FilmAficionado said:**
> System > Preferences > Advanced Desktop Effects Settings and clicked PREFERENCES > RESET TO DEFAULTS
And "Extra" does not change the settings (just adds two plugins).

So I'm wondering what default settings FilmAficionado is talking about...

---

### Post by FilmAficionado on 2007-11-24
I sure hope I wasn't imagining things but I am confident that what you guys said (and what I tried myself earlier) as the reset to defaults were not exactly the defaults of a fresh Ubuntu install. I got some advice off of the Craigslist linux forum 

>  Right-click and rename the following folders - you can just add .old or .bad or .dont-like-this to the folder name if you want -

.emerald
.gconf
.gnome
.gnome2
.gnome2_private
.nautilus

7. Log off and back on as yourself. You should see a default Ubuntu desktop now. 

I did all of that, though I could not find .EMERALD anywhere. I logged out, and BAM, my login screen was blank white. I did a hard reset and Ubuntu logged back onto a normal DEFAULT desktop.

(So I hope that since the above worked, all is well? I didn't mess up anything?)

I actually think if I followed your guys' advice of > System > Preferences > Appearance
Under the "Visual Effects" tab, you should have 4 options to choose from: None, Normal, Extra, and Custom
If I'm correct, it will be set to "Custom". Change it to "Normal" or "Extra", depending on how fancy you want it. Those are the default configurations.

THAT too might have worked. Oh well, thanks so much. Sorry if I freaked out. I'll keep this in mind though since I'm sure I'll mess stuff up again.

Thanks again guys!

---

### Post by Forlong on 2007-11-25
Wow, deleting all your configs is really not a proper way to solve something like this.
But hey... If you're happy, I'm happy.
Everybody's happy &#8594; [IMG]http://mitglied.lycos.de/Forlong/smile/knuddel.gif[/IMG]

 :mrgreen:

---

### Post by rainwalker on 2007-11-25
Just FYI, you didn't have an .emerald folder because you're not using Emerald
I agree with Forlong, messing with config files like that definitely isn't a good way to solve things...ugh, take it from me, that .gcomf folder is a tricky little bugger.

---

