---
title: "Switching keyboard layouts"
date: 2009-02-10
forum: General Help
---

### Post by broecher on 2009-02-10
Hello, 

I have a problem switching between two keyboard layouts. I use hardy with gnome. I have a microsoft usb keyboard. I switch between the USA (default) keyboard layout to a Russian layout (problem occurs with any second keyboard layout). I set it to switch layouts by pressing ctrl-shift. It works great until I restart, the ctrl-shift no longer works. I have to go into the keyboard preferences, delete the layout, and then add it again. Then it works again for that session. The settings for switching and the keyboard are all still correct before I delete them.

-oh I am a newbie so please try to explain where to go and what to do carefully.

Thanks!
John

---

### Post by emmwee on 2009-02-12
Go to: system - preferences - keyboard. Then disposition, add a language, choose "separate disposition for every window", click on "other options", click on switching/commutation disposition and look for a combination you like (I choosed the left window key).
Now try: type a letter, then press the key you choosed (f.e. window key), type the same letter again: it should be the one of the second keyboard you added. Then press the key you choosed once again (f.e. window key), type the same letter again: it should be the one of the 1st keyboard. So can switch between two keyboards. - I hope this will help everyone who writes in differentlanguages and needs special characters like è, ü and so on.

---

### Post by Icebear on 2009-02-12
how to install a new keyboard layout in ubuntu goto:
system>preferences>keyboard

Then hit the layout tab and hit the add button

**for changing the keyboard** when in the layout tab hit the layout option button

then choose the layout switching and choose what key you want to use.

if you want a keyboard indicator on the panel go to a empty space on the panel and click the right mouse button and choose +add to pannel

then scroll down to keyboard indicator and click it and then click the +add button at the bottom of the window.

ps If you need a third level leaver again goto the layout option button then click the third level leaver and choose your key you want.(for example some US keyboards you can use this to get a &#8364; on the number 5 key)

---

### Post by broecher on 2009-02-13
Thanks for the replies, I did not know I could have a keyboard indicator. That is useful. 

I understand how to enable a second keyboard layout, and how to switch between them. The problem is after the computer restarts, it no longer will switch. When I go back into the layout switching options, I can see that everything is still set correctly. To make it start working, I have to de-select and re-select the switching key (I use right win key). Then it works again until I restart the computer....

---

### Post by prshah on 2009-02-13
> **broecher said:**
> The problem is after the computer restarts, it no longer will switch. 


See any of these links: 

[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

---

### Post by broecher on 2009-02-13
thanks, also I just noticed I can switch by clicking the indicator which is just as easy as pressing the win key!

---

### Post by bengershon on 2009-03-19
The links all say pretty much the same, and solve the reboot problem. However, I have a similar, but slightly different problem. My system shares a keyboard and mouse with a Windows machine using a USB KVM. Every time that I use this to switch to Windows and back I lose the second (non-US) keyboard. It shows up on the 'keyboard preferences' dialog, but does not work unless I make some change to the preferences. Likewise with the GNOME keyboard indicator. Looking at the Xorg.0.log file it looks as if the KVM effectively 'unplugs' the keyboard and the plugs it back in, but then sets it up incorrectly as being only "us" and not "us,il" as I have configured it.

This is really annoying, and I have not found any solution despite days of searching on the net.

I have a feeling that it is relatively new though - presumably some upgrade over the last few months must have broken something.

---

