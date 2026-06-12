---
title: "Calling the music player from keyboard - can I change the default one?"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Turin Turambar on 2006-08-04
I have a multimedia keyboard with music player button. When pressed, it starts the music player (doh!). However, I installed another player called Listen and I'd like to make it default.

Unfortunately I couldn't change anything. Rhythmbox still appears when I press the button.

Any solution?

Oh yeah, it's a real shame that they included only 3 programs in "preferred applications" and two of them being mail&web.
Some limitations in Gnome are just pure nonsense! :mad:

---

### Post by Lunar_Lamp on 2006-08-04
How did you configure the key originally?  What keyboard are you using?

---

### Post by Turin Turambar on 2006-08-04
I configured it with keyboard shortcuts. My keyboard is a Genius 12e.

---

### Post by Nicks Spleen on 2006-08-06
This is how I solved this problem. It just changes the link to redirect to listen. 

sudo mv /usr/bin/rhythmbox /usr/bin/rhythmbox.old
sudo ln -s /usr/bin/listen /usr/bin/rhythmbox

I think audio player should be under perfered applications along with web and email. If you still want to use rhythmbox from the applications menu, fire up alacarte and change its command to:

/usr/bin/rhythmbox.old

Hope this helps for anyone else needing a fix without that keyboard.

---

### Post by savage on 2006-08-27
Preferred applications is where I looked first for setting the default audio application for specific file types. Instead use your mouse to right click on the file type you would like to change the default application for, choose properties, now select the  "Open With" tab, select your application there, this will now be the default for all files of that type.

Sometimes I wonder if Gnome development is making things so easy, that they are becoming hard.

---

### Post by Turin Turambar on 2006-08-31
> **Nicks Spleen said:**
> This is how I solved this problem. It just changes the link to redirect to listen. 

sudo mv /usr/bin/rhythmbox /usr/bin/rhythmbox.old
sudo ln -s /usr/bin/listen /usr/bin/rhythmbox

I think audio player should be under perfered applications along with web and email. If you still want to use rhythmbox from the applications menu, fire up alacarte and change its command to:

/usr/bin/rhythmbox.old

Hope this helps for anyone else needing a fix without that keyboard.

Hey, thanks a lot!! This worked! :D

---

### Post by p.i.m.p on 2006-09-02
hey thanks man! you've been of great help! :D

---

### Post by shakma on 2006-12-15
Awesome!  Thanks a mil, spleen!  Works like a charm on the Microsoft Natural Multimedia keyboard, too.

---

### Post by xopher on 2006-12-15
Check this out for a graphical approach, with added configurability ;)

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

> KeyTouch is a program which allows you to easily configure the extra function keys of your keyboard. This means that you can define, for every individual function key, what to do if it is pressed.

EDIT: It's of course available in the repositories (universe).

```
sudo apt-get install keytouch
```

---

