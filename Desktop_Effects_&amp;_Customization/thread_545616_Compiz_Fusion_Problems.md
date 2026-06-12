---
title: "Compiz Fusion Problems"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by Apothysis on 2007-09-07
I have followed this guide: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

And I have pretty much gotten Compiz Fusion to work perfectly. However, Emerald does not work like it should, I keep getting this same error over and over again when I run emerald --replace, and this error causes major system performance loss (everything laggs basically, but the CPU usage and MEM usage is very low), and I have a problem with some animations. See the attached image for an example. That is what happends when for instance I move a window towards the edge so that it moves into another desktop.

[QUOTE=Emerald Error](emerald:25126): Wnck-WARNING **: Unhandled action type (nil)[/QUOTE]

And, I cannot find my cube effect, that would be the one that lets me pull around the cube and soforth with my mouse. Why doesnt that work?

And, I have yet another problem. My desktop was automatically set to 101. It should be 105. How do I fix this?

---

### Post by spartus4 on 2007-09-07
Go back to the step were you go into System->Preferences->Sessions.  Instead of have one entry for Compiz and one for Emerald, just make one entry for Compiz and enter the command compiz --replace -c emerald &.  I had problems getting things to work by using two different entries.  As for the display corruption,  I am not sure.  Did you follow the instructions on this site [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) .  One more thing,  what ATI Video card are you using?  The reason I ask is because there are two different ways of setting things up.  If you have an X100 series or an X1000 series.  The X100 has a completely different driver setup from the X1000.

---

### Post by Apothysis on 2007-09-08
I've got an X1400. Also, I can't seem to open up my ATI Catalyst Control Center anymore...

Edit: And now I can't even "sudo gedit" files, like "sudo gedit /etc/X11/xorg.conf", the window gets stuck.

---

### Post by Apothysis on 2007-09-08
I got the gedit and control center to work again. I decided to format the whole thing. I followed the same guide, and it works, but I still get that window corruption when I move things to the edge. It also happends when for instance the Compiz Fusion Splash fades out, I see like small boxes covering the areas where the text input was.

To put it simple, whenever an animation from Compiz Fusion is activated so to say, I get the boxes everywhere, it really sucks. Sure, they dissapear when I grab a window and draw it over my whole screen but small boxes are still there on some places.

And I still have a problem with the keyboard.

---

### Post by runemaste644 on 2007-09-08
The unhandled action type (nil) is completely normal
Though that screenshot looks weird.
Our new vocabulary word for today is: Garbage Screen 
Garbage screen is a redraw error where if you drag a window, it leaves a trail.

---

### Post by Apothysis on 2007-09-08
> **runemaste644 said:**
> The unhandled action type (nil) is completely normal
Though that screenshot looks weird.
Our new vocabulary word for today is: Garbage Screen 
Garbage screen is a redraw error where if you drag a window, it leaves a trail.

It is not only weird but also very annoying. Also, I cannot seem to find the cube feature. You know where I click some combination, and it zooms out to the cube and lets me rotate it with my mouse. How do I get that?

Nevermind found the cube feature. But I still have the "garbage screen". I've tried turning off several plugins, but still nothing.

---

### Post by Apothysis on 2007-09-08
Sorry for the bump/double-post but I really need this resolved. My only remaining issue is the one seen in the screenshot from the first post. It's not all animations, but say that I would do some firepainting on my desktop. Later, when I remove it, I still see pixels/boxes after it, why?

Here's another screenshot to make it more clear; This is what I get after typing "example" over my desktop. See how the boxes look just like trails after the fire particles? That's basically how it is. If I use the cube and switch to another desktop, I see trails of the animations, like how I turned the cornes and so on.

---

