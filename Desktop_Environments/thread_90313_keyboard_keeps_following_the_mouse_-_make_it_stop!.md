---
title: "keyboard keeps following the mouse - make it stop!"
date: 2005-11-14
forum: Desktop Environments
---

### Post by tbe on 2005-11-14
Hi all, 

I've had Ubuntu stored on my laptop for about six months now.  I recently  upgraded from to Breezy from Hoary.  I like both a lot - well done to the Ubuntu crew!...
I have one problem on the desktop that was minor irritation at first, but it is really beginning to piss me off - I hoped it would go away after the upgrade to Breezy...

Whenever I type, on any text editable area, periodically, the keyboard loses focus and jumps to whereever the mouse is at the moment.  There it goes!  (I just lost it again; - it went back 3 lines to where the mouse was resting).

Does anyone know why this happens? What can I do to fix it?

Here's my system:

tbe@acer01:~$ uname -a
Linux acer01 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

I'm running 
Ubuntu using the 
Gnome desktop on an
Acer TravelMate 290 LMi with a 
15.0 XGA TFT LCD monitor.  I've set my keyboard layout to
"Acer TravelMate 800'", it used to be "Generic 105-key (intl)" but this change makes no difference

Thanks in advance for any help you can give me.

---

### Post by Sheco on 2005-11-14
Sounds like youre tapping your mouse so it's sending mouse clicks.

---

### Post by ltmon on 2005-11-14
You could try debugging it with the following:

- open a terminal
- type 'xev'
- roll your mouse over the white window that is created
- Type a few letters
- inspect the output on the terminal for any non existent mouse clicks

xev basically monitors keyboard and mouse events being sent to the X server.  If there's some kind of extraneous mouse click event being produced, this should tell you.

L.

---

### Post by tbe on 2005-11-14
Good suggestion - I wish that it were so ;-)   

At least then with practice, I could stop it.   I touch type, and I'm pretty good at it. I'm absolutely positive that I'm not touching the mousepad when the shift to the mouse occurs.  The fact that I can touch type is what makes this behaviour so annoying - it constantly stops me in mid-flow...

Nope, I think is that this is a bona fide feature.  I don't how to generate evidence to prove it, so I'm hoping to find someone else who has experienced it and hopefully fixed it...

---

### Post by tbe on 2005-11-14
Thanks, 
I'll try that

---

### Post by daller on 2005-11-22
I have the same problem with my Dell Inspiron 8600...

...Quite rarely though!

---

