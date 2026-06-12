---
title: "I am prompted for a password after turning off my laptop screen"
date: 2008-04-25
forum: Desktop Environments
---

### Post by curlingdude on 2008-04-25
I am running Hardy on an IBM ThinkPad T40. I just recently upgraded.

Before when I used to turn of my screen (using Fn-F3) it would turn off and then I would be able to move my mouse or hit a key to turn it back on. Now in Hardy, when I move my mouse it prompts me to enter my password. It locked the screen.

I have scoured the system configuration tools found under both System->Preferences and System->Administration but have been unable to resolve this. I am sure there is a setting somewhere saying lock screen when I turn it off but I haven't been able to find it. I would like to disable this feature as there are many people in my house who use the laptop and I feel secure enough that I don't need them to type in the password each time.

I have checked the places I thought it might be (Power Management, Screensaver) but none are enabled. Is there another place to edit acpi configurations? It does not need to have a fancy GUI, I am willing to read man pages, etc.

Thanks for your help.

---

### Post by NilsE on 2008-04-25
Look in the configuration editor  which should be in Application > System Tools. If not then install it via synaptic. 

Then navigate to

apps > gnome-power-manager > lock

and play with those settings. Basically the first and last check boxes should not be checked.

---

### Post by curlingdude on 2008-04-26
Thanks for your reply. I have conirmed that the problem is in Gnome. I have run gconf-editor both as me and as root. In both case, the settings you mentioned were disabled. It seems to be ignoring the setting for blank screen.

Does anyone have any other ideas?
Thanks so much.

---

### Post by encompass on 2008-04-26
What button is it exactly?  Is it the one with the little lock on it?  The Fn-F-key.

---

### Post by curlingdude on 2008-04-26
It's the one with a square (representing a screen) and an X next to it.

I found out that is is eventually calling /etc/acpi/screenblank.sh. That part works fine. If I run that as root, my screen turns off and when I move the mouse it comes back without a password prompt. The problem is that Gnome is running something after that which is locking my screen.

---

### Post by encompass on 2008-04-26
I would search for and report a bug to the launchpad account.  This is something that they should be able to fix for you.  I wish I could help you further, but I don't think it's possible.
ACTUALLY
could it be it's doing a lock screen?
For example, does it "fade" out... rather then just shut off?  if it does, we can do something otherwise do the above.

---

### Post by curlingdude on 2008-04-26
Now that you mention it, it does seems to fade out. Why is it doing a lock screen and what can I do to stop it?

Thanks

---

### Post by encompass on 2008-04-26
OK now we are getting somewhere... for some reason... your lock screen button is not the right button... usually it's a little picture of a lock or a running man. But your isn't... 
The purpose of the button is to lock the screen so people can't use it when you go away.  if you set a screen saver and then press the lock key... you will get the idea.
Sounds totally off subject... but it's not...
do you have bluetooth?  if so I can show you something cool you can do to unlock and lock the screen.  It sounds like you do that alot. :)

---

### Post by curlingdude on 2008-04-26
The Fn-F3 on my ThinkPad T40 is not for locking the screen. It is simply for turning off the screen. In Gusty, Gnome would simply turn off the screen when I clicked Fn-F3. Now it has started locking it. In my opinion this is a bug (which I will file at some point).

My workaround is to simply close my lid (which I have set to simply turn off the screen or wait 6 mins until the power management turns off the screen.

---

### Post by encompass on 2008-04-26
Actually, I think what it is SUPPOSED to do it switch to the external monitor and back again.(Hence your screen blank and back again.)  That is what the symbol is for on all laptops that I have seen, including a t61 I just got working with hardy.
Additionally,
I don't think Ubuntu or gnome even have that feature you mention at all.  If so it would be pretty shocking for me.
BTW the T40 is a fantastic Lappy.  Congrats.

---

