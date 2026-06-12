---
title: "Nothing appeared after login"
date: 2011-01-19
forum: Desktop Environments
---

### Post by azayrahmad on 2011-01-19
I use ubuntu 10.10 

Last night when I use my laptop I hangs and when I shut it down the last thing I see is there's a not responding app called at-spi register (or at-sys or something I don't really remember) and the next time I log in to my account there's only login sound heard and the wallpaper I set before, and the mouse cursor. There's nothing else. No nautilus, no panels, nothing. Nothing happened when I press alt-f2, ctrl alt L, etc. There's even nothing happened when I press the power button (unless if I press it a long time it will shut down). the only thing I can do (that I know) is press ctrl-alt f1 & ctrl-alt-f7 to change to tty. And only through tty and recovery mode I can access my account. I decide to create new account using adduser and I can login into the new account successfully. but then again in my new account I can't access all the data from my original account. and I can't use root or sudo command in my new account. 

I've tried to reset gnome and nautilus using rm -rf but apparently nothing appeared but login sound, wallpaper (that change to default ubuntu maverick wallpaper), and a mouse cursor that can't do anything.

What's wrong with my Ubuntu?

---

### Post by azayrahmad on 2011-01-19
no one really?

oh god

---

### Post by sbrandon on 2011-01-19
experienced the same thing after I updated today. background only

---

### Post by Krytarik on 2011-01-19
There is obviously something wrong with your user profile, take a look in ~/.xsession-errors.

To grant your newly created user admin rights enter:
```
sudo adduser NEW_USER admin
```

---

