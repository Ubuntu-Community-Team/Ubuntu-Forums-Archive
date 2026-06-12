---
title: "GDM - possibility to add keyboard layout menu option?"
date: 2007-04-23
forum: Desktop Environments
---

### Post by rrohde on 2007-04-23
GDM - possibility to add keyboard layout menu option?

Is there a possibility to add a keyboard layout chooser at the GDM level? In our organization we have users that require at least 2 different keyboard layouts (QWERTY or AZERTY).  

Since it is not obvious what keyboard layout is default at login time, I observe lots of confusion of users login in. This goes as far as users typing their passwords in the "username" field to figure out the keyboard layout, and then they go about logging in. 

So, is there such a possibility to have a keyboard layout chooser at login-time? If yes, where would I find it and how could it be implemented? 


Cheers, 
Rainer

---

### Post by rrohde on 2007-04-24
Anyone? :)

---

### Post by rrohde on 2007-05-11
Bump

---

### Post by rrohde on 2007-05-29
another bump...

---

### Post by silwol on 2007-08-01
just found your post. i hope it is not too late yet, but maybe this solution works for you:
[http://ubuntuforums.org/showthread.php?t=469237](http://ubuntuforums.org/showthread.php?t=469237)

---

### Post by rrohde on 2007-08-01
Thanks for the reply. No, it's not to late.. this project is ongoing that that issue is just one of the many issues we have. 

Cheers, I will check out that link and post my findings here... :)

Rainer

---

### Post by rrohde on 2007-08-01
No, that's not it. 

Our problem is: 

When the machine boots up, it ends up on the graphical Gnome login screen (GDM). This screen authenticates the user BEFORE he/she ends up on the actual Gnome Desktop. 

Since in our environment, we ultimately support 2 main keyboard layouts (QWERTY and AZERTY), we were looking for a way to have a (custom made) selection switch as soon as the GDM login screen that would allow a user to CHOOSE his/her keyboard layout with a mouse click before they type their username/password. 

That's the issue. That's something we need to resolve. Sadly, GDM allows for selecting the language at login time, but NOT the keyboard layout. 

The language is always English, however, keyboard layouts vary.


Any help in this matter is greatly appreciated!

Cheers, 
Rainer

---

### Post by rrohde on 2007-08-27
Another bump.. :)

---

### Post by rrohde on 2007-09-05
Yet another bump... my mom told me that perseverance pays off in life.. ;)

---

### Post by afonic on 2007-09-05
Just an idea, maybe you can set 2 languages, for example US English with QWERTY and UK English with AZERTY as keyboard layouts and select between those?

Edit: Mark wrong - I just found out you cannot change keyboard layout in login. Maybe KDM can, have you tried it? (KDE noob here :P )

---

### Post by rrohde on 2007-09-06
Our hope is that maybe there's a hack that adds a keyboard layout selector to GDM, which could allow us to pre-define 2 layouts (AZERTY and QWERTY) for the users to choose from. 

This is, as pathetic as it may sound, a real issue, as some of our pilot users have their password locked, requiring them to phone up the helpdesk, because they couldn't figure out how to type their password from a QWERTY layout...  

I can't imagine that our organization is the only one in Ubuntu-land that came across this and requires a solution for it... 

Cheers, 
Rainer

---

### Post by afonic on 2007-09-06
How about contacting Canonical directly?

I think they'll be glad to help you.

[http://www.canonical.com/services](http://www.canonical.com/services)

---

### Post by nick_nitro on 2007-09-11
Did you already find a solution rrohde ?
Because i have te same problem :(

---

### Post by rrohde on 2007-09-11
Sadly - not yet... :(

Contacting commercial Ubuntu support is not really an option yet either, as we're in the intial pilot phase of the project, which is to evaluate the feasability and functionality for various use-cases - without production budget...

---

### Post by rrohde on 2007-10-01
Guess what? Another *bump* :)

---

### Post by daveerickson on 2007-10-27
I am going to throw my name in the hat of people who could use this functionality. I type with the Dvorak layout, my wife does not. She does not like sitting down and having issues logging in...:lolflag:

It would be super awesome if she could just select QWERTY at gdm.

---

### Post by daveerickson on 2007-10-31
Bump.

---

### Post by daveerickson on 2007-11-03
Bump.

---

### Post by daveerickson on 2007-11-12
Bump.

---

### Post by daveerickson on 2007-12-01
Bump.

---

### Post by daveerickson on 2007-12-27
Bump.

---

### Post by daveerickson on 2008-01-09
Bump.

---

### Post by LordVeovis on 2008-01-14
I was on another site and learned of a keyboard shortcut that will let you switch back and forth, perhapse it will do??

the shortcut is to press both alt keys at the same time.

---

### Post by daveerickson on 2008-01-27
> **LordVeovis said:**
> I was on another site and learned of a keyboard shortcut that will let you switch back and forth, perhapse it will do??

the shortcut is to press both alt keys at the same time.

Unfortunatly that does not seem to work under GDM, only after logged in. Thanks for the idea tho.

---

### Post by &#1084;&#1072;&#1083;&#1080;&#1115; on 2008-02-04
Bump! I need "this option", too.

---

