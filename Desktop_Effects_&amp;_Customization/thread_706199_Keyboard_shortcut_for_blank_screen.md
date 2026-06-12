---
title: "Keyboard shortcut for blank screen?"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by Mujaheiden on 2008-02-24
I have a spare thinkpad button on my laptop and I wish to assign it to the same function as which is triggered when i close the laptop lid, namely shutting down the screen.

So if I go for a coffee, I just press ThinkPad and save my screen a bit, until I come back, after which a mouse wiggle etc. should wake-up the screen again.

Is this possible?

---

### Post by H_out on 2008-02-29
Try this:

```
xset -display :0 dpms force off
```

Mouse movement will turn the monitor back on.

---

### Post by FreewareFan on 2008-02-29
To actually assign a physical key on your keyboard to do what you want, you'll need the program Keytouch.   Just install it, read the docs, and you'll have what you want within 15 mins or less!!   It's a great program.

Hope this helps!

FwF

---

### Post by H_out on 2008-02-29
Most likely you already have some kind of settings manager that will allow you to map a key to execute a command.

Compiz-fusion has commands you can map to shortcuts.  Look under "General" and then "Commands".  Set a command for command0 and then go to "Actions".  Assign a key to command0.

Also, I know Xubuntu 7.10 has a keyboard preferences manager.  It's under Settings >> Keyboard Settings >> Shortcuts.

---

### Post by FreewareFan on 2008-02-29
> **H_out said:**
> 

Also, I know Xubuntu 7.10 has a keyboard preferences manager.  It's under Settings >> Keyboard Settings >> Shortcuts.

You cannot set your own custom shortcuts with that program.  You can only change the keys that run the pre-defined actions.  In other words, if there is a pre-defined action, and you don't like the keyboard shortcut associated with it, you can change the shortcut, but not the pre-defined action.   Hope that made sense...

Anyways, to make a custom keyboard shortcut, that starts a custom action of your choice, the only thing that will do it is Keytouch, as I already said...  

Check it out for yourself, see if what I say isn't true..:)

FwF

---

### Post by AmericanYellow on 2008-02-29
> **H_out said:**
> Most likely you already have some kind of settings manager that will allow you to map a key to execute a command.

Compiz-fusion has commands you can map to shortcuts.  Look under "General" and then "Commands".  Set a command for command0 and then go to "Actions".  Assign a key to command0.

Also, I know Xubuntu 7.10 has a keyboard preferences manager.  It's under Settings >> Keyboard Settings >> Shortcuts.

That's right.  In Ubuntu, Go System >>Preferences  >> Keyboard Shortcuts. There, look for "Lock Screen" and you can easily reassign the key.

---

### Post by H_out on 2008-02-29
> **FreewareFan said:**
> You cannot set your own custom shortcuts with that program.  You can only change the keys that run the pre-defined actions.  In other words, if there is a pre-defined action, and you don't like the keyboard shortcut associated with it, you can change the shortcut, but not the pre-defined action.   Hope that made sense...

Anyways, to make a custom keyboard shortcut, that starts a custom action of your choice, the only thing that will do it is Keytouch, as I already said...  

Check it out for yourself, see if what I say isn't true..:)

FwF


Hmm...I'm not sure what FreewareFan is talking about.  I'm running Xubuntu 7.10, here is my Keyboard Preferences window:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61210&stc=1&d=1204341208[/IMG]


Just click "Add", it will prompt you for a command and then a key to bind it.  You can see in the background I have the command for turning off the monitor binded to my standby button.  No additional software required!

Hope that helps!

---

### Post by FreewareFan on 2008-02-29
Ah, that must be it then!!   I run Ubuntu, and you are running Xubuntu.   The keyboard shortcut program is different in Ubuntu, and will not let me add shortcuts like yours will.   

I'm wondering if I could install that program on my Ubuntu installation??  Would you do me a favor, and run your program, and see exactly what the name of it is in the Help section?   Thanks!!

FwF

---

### Post by Mujaheiden on 2008-03-01
It took me over an hour, but after making my Thinkpad R32 file, I think I managed. I dont get why there is not just an "add key" in the Ubuntu Keyboard shortcuts.
I mean, I didnt really have fun in the hour spent.

---

### Post by FreewareFan on 2008-03-01
Yep, that looks like it will work.  But I see you only mapped like 3 or 4 buttons, yes?  I would have done them all, and then anytime in the future, they would be there to assign any custom command you wanted...

But anyway, glad you got it to work with Keytouch.  It is a powerful program!

FwF

---

### Post by Mujaheiden on 2008-03-01
I only have 4 extra buttons, beside my normal keys.
The power buttopn didnt work, and I didnt persist :), and the regular Fn>PgUp (Thinklight) already work, so no need to add, i guess.

Its similar to the on on the [picture]("http://www.geocities.com/yuho0/P5240784.JPG") to the right, just a wee different OS :)

---

### Post by FreewareFan on 2008-03-01
Ah, I see.   Well then, you've done all you can with Keytouch, then.  But, at least you now know of it's exsistance, and if you ever run an external keyboard you'll know how to set it up!

Be well....

FwF

---

