---
title: "Desktop Effects.... gone missing! (Feisty Fawn Beta)"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by USAgent on 2007-03-31
New to ubuntu, and linux, and having a great time with it. Yesterday, left my laptop for a co-worker to use for a few hours came back and a certain function seemed to have stop (where I would move the cursor into the upper right corner, and all the open windows would tile and you could select the one you wanted to have focus). I would very much like this function to come back, can anyone help?

Thanks in advance!

---

### Post by Spin Doctor on 2007-03-31
Yeah, I noticed this the other day myself. I think the developers removed that functionality since many users could potentially activate switching screens when wanting to logout or shutdown the system... atleast that is my theory.

Try using ALT + Tab for easy switch of windows. Might not look as fantastic but does the work too.

Can you play DVD's in Totem with desktop effects on?

---

### Post by USAgent on 2007-03-31
I can't really say anything about DVD's or Totem, I haven't tried either yet.

---

### Post by lolocaust on 2007-03-31
Disable compiz from the desktop effects dialog and install beryl from the add/remove app. That way you can configure it so that the scale plugin is re-enabled.

But before that, try pressing F9, that should activate the same thing.

---

### Post by Spin Doctor on 2007-03-31
Just looking through the settings in gconf-editor

You can activate scaling plugin by pressing: **CTRL+ALT+UP ARROWKEY**, and select window with mouse while still holding key combo

---

### Post by Spin Doctor on 2007-03-31
OK... FINAL POST! =)

_** This is the solution:**_

In **Gconf-editor**:

Go to:
**/apps/compiz/plugins/scale/allscreens/options/initiate_all_edge**

Rightclick on the value, and enter TopRight in your case, and voila. It works just like it did before =)

Over and out from Sweden! Always nice to have one less problem to solve =)

---

### Post by Frihet on 2007-05-03
Desktop effects will kill Totem.

---

### Post by Spin Doctor on 2007-05-14
Check this thread for a tip how to get Totem to work with Desktop effects:

[http://ubuntuforums.org/showthread.php?t=425926](http://ubuntuforums.org/showthread.php?t=425926)

---

