---
title: "Impossible to enter password after locking screen"
date: 2007-04-24
forum: Desktop Environments
---

### Post by kwaanens on 2007-04-24
So, I can't get back into my session. Worked fine on Edgy. using an MSI s262 (or whatever) laptop. (EDIT: meaning, there is no way of actually getting the letters in to the password field.)

How to fix?

- Ketil

---

### Post by blitzer on 2007-04-24
Hello kwaanens,

Did you try typing user name -hit enter type in password hit enter to see if it will work ?  
I don't totally understand your problem (sorry) 
Here is a link that may or may not help [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_root_user.2Fmain_user_password_if_forgotten]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_root_user.2Fmain_user_password_if_forgotten")

---

### Post by kwaanens on 2007-04-24
I remember my password. When I lock my screen, all I'm asked about is my password, and yes, I tried to just enter the password and hit enter. No luck.

On an unrelated note, I see that while screen is locked, alt+tab still works (at least the beryl version of alt+tab), making it possible for nosy people to see what you're doing on your computer, if you're away from it.

- Ketil

---

### Post by blitzer on 2007-04-24
Hi kwaanens,

Nice find on the alt-tab maybe report it to the Beryl forums - I'm sure they would like to know this :( 

Good luck on the Screen lock - the link didn't help I guess.

---

### Post by Aetherius on 2007-04-24
hey kwaanens just thought i'd stick in a +1 here, I'm suffering from the same problem.


Was working fine for the several months that I've been using Feisty, but I read your post earlier and now I've caught it :(

---

### Post by Aetherius on 2007-04-24
Yup this bug is Beryl's fault.

With Metacity and/or Compiz the bug vanishes...

I like beryl better, what a pity

---

### Post by Aetherius on 2007-04-25
anyone report this yet? If not then i'm gonna

EDIT: Couldn't find it reported on launchpad, so i did the duty.

---

### Post by kwaanens on 2007-04-25
Good work!

- ketil

---

### Post by UMDGaara on 2007-04-26
Read this: [https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/109900](https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/109900)

It helps to understand the concept that F1 to F6 are terminal sessions. X normally runs on F7, so from your messed up or screen locked X session (the normal desktop/beryl/whatever) you push ctrl+alt+F1 (or F2 or F5 or whatever) to go to a new terminal session. Log in there, kill beryl, and then press alt+F7 to return to the X session (you only need alt this time, not ctrl+alt, to change sessions from a terminal session. ctrl+alt is to switch away from X while leaving it running). You can also try killing the gnome-screensaver process, which runs when your screen is locked.

I have the same problem probably 60% of the time my screen locks.
I also have a problem with the screen dimming when asked for my root password to perform administrative tasks. Sometimes the screen doesn't un-dim and i can't see anything, even though all my controls still do stuff. Luckily the workaround for both problems is the same: go to a terminal session, kill beryl (and maybe gnome-screensaver if necessary), go back to X, restart beryl.

---

### Post by javakidv1 on 2007-05-06
It seems to be related to the "unredirect full screen windows" option under general options >main >advanced in beryl. I disabled that and the problem went away. Hopefully this works for everyone else as well.

---

### Post by twinight on 2007-05-27
I would like to resurrect this and offer another workaround, and perhaps provide more information.

As I do a lot of multimedia watching, swapping back and forth between having "unredirect full screen windows" checked was troublesome to say the least.

The problem lies with that setting though, yes, after a suspend the password entry dialog is apparently 'full screened' and somehow that setting prevents it from taking "focus."  You can drop focus onto it though by hitting the power button (assuming you have the power button set to "ask"), and then hitting escape.

For me this has worked 100%, and focus drops back into the window.

However this still doesn't solve the issue of being able to rotate the cube and 'see' what's going on in other windows from an angle, assuming you have some cube transparency.

Should this be a bug reported to ... where?  I'd assume Beryl?

---

### Post by kwaanens on 2007-05-27
> **twinight said:**
> As I do a lot of multimedia watching, swapping back and forth between having "unredirect full screen windows" checked was troublesome to say the least.

Just checking: What does "unredirect full screen windows" actually do?

- Ketil

---

### Post by twinight on 2007-05-27
> Just checking: What does "unredirect full screen windows" actually do?

I'd be lying if I said I really understood -- but to the best of my knowledge, it does something with beryl where it prevents anything 'fullscreened' from being totally 3d mapped or somesuch.  I'm using the wrong words I am _sure_.

As far as practical utility:  When unchecked, my video played fine but fullscreen it was _always_ choppy.  Checked, my video runs at full speed fullscreened or windowed.  It does suffer performance issues whenever I'm rotating the cube though (the video isn't smooth then) but uh... honestly, that's not really a major issue for me.  :)

---

