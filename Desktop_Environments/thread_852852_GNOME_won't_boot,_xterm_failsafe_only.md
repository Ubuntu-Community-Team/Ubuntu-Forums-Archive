---
title: "GNOME won't boot, xterm failsafe only"
date: 2008-07-08
forum: Desktop Environments
---

### Post by CleverJake on 2008-07-08
I shut down my Hardy laptop, and when I turned it back on an hour later, GNOME won't load.
I think
Im not 100% sur what isnt loading, but basically I get the login screen, I log in, and into a xterm fail safe terminal that says

I could not open your session and so i have started the failsafe xterm session


then when I load that it says cannot execute binary, over and over for about twenty lines.

Seems like that would be related, but I know very little on this part of Ubuntu or linux in general

any help or tips or anything would be very much appreciated

---

### Post by CleverJake on 2008-07-08
I shut down my Hardy laptop, and when I turned it back on an hour later, GNOME won't load.
I think
Im not 100% sure what isnt loading, but basically I get the login screen, I log in, and into a xterm fail safe terminal that says

I could not open your session and so i have started the failsafe xterm session


then when I load that it says cannot execute binary, over and over for about twenty lines.

Seems like that would be related, but I know very little on this part of Ubuntu or linux in general

any help or tips or anything would be very much appreciated

---

### Post by p_quarles on 2008-07-08
Duplicate threads merged. Cross-posting is against the rules here as well as on most of the internet for as long as it's been around. :)

---

### Post by CleverJake on 2008-07-08
sorry mate, meant to cancel the first one

---

### Post by CleverJake on 2008-07-10
sorry to bump, but any help would be great, id hate to have to reformat the partition

---

### Post by podness on 2008-09-23
[B][SOLUTION]
[/B]

I found what was the problem.

I had this one too just a moment ago..

what you do is:
1. log in your account 
2. Now you see that xterm failsafe thing
3. Move your mouse on it and type

```
gnome-session
```

this will launch your gnome

4. Go to your home folder, show hidden files (CTRL+H)
5. Find the file **.profile** and either delete it **or** rename it
6. Reboot
7. Never mess up with this file, lol.  oh and yes, all works normal again.

The goal is to make Ubuntu recreate that file.

The reason your gnome doesn't run is probably because there were some
changes made to the file > .profile in your home directory..

I myself mistakenly saved the settings of my advanced desktop effects,
straight into this file.. and I wasn't supposed to do this..

I read over the net that someone else removed a line from that file > .profile and that caused him the same problem, so...

Good luck! :guitar:

---

### Post by wazzoo on 2009-05-13
Legend! I did *exactly* the same thing, I figured I'd already saved my effects settings once, and when i saw the .profile file sitting there I promptly overwrote it. Cheers!

---

### Post by buddywilliams on 2009-10-07
Work for me!!! Removing .profile fixed my problem too. 

I wasn't able to login at all. I wasn't finding any solutions until I tried this one.

Why would this cause gnome to break for me?

---

