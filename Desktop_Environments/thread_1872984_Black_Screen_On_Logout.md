---
title: "Black Screen On Logout"
date: 2011-10-31
forum: Desktop Environments
---

### Post by powersurge360 on 2011-10-31
If I have a ~/.compiz-1 folder on login, then when I log out I get a black screen. If I delete it before I go in, I can log in/out safely only if I do it before the folder reappears (shortly after logging in).

The black screen is 100% a display issue, because if I log out to the black screen, I can blind-type my password and get logged back in.

This is mostly a nuisance when I want to switch users or use a virtual terminal (the problem also occurs there). What is causing this and how can I fix it?

---

### Post by win0922 on 2011-10-31
[LIST=1]
[*]What is your version of ubuntu.
[*]How many users do have that are availible to swich to.
[/LIST]

---

### Post by powersurge360 on 2011-10-31
Ubuntu 11.10, Oneiric Ocelot

I currently have just one other user to switch to, but that's a red herring I would think because the issue is that the session doesn't refresh properly or something. My display borks when I log out.

---

### Post by win0922 on 2011-10-31
Does your display go of does the signal input go.

---

### Post by powersurge360 on 2011-10-31
I don't fully understand what you're asking me, but I am able to type in my password and get back into my account (suggesting that the login screen is there and active, I just can't *see* it.)

---

### Post by win0922 on 2011-10-31
Does your screen turn off or does your screen display "No Signal". 
 
It could be a settings issue.

---

### Post by powersurge360 on 2011-10-31
Neither. It is a black screen, but the backlight is still on.

---

### Post by powersurge360 on 2011-10-31
Note that I do not have any problems logging out with unity 2d, this seems to be some kind of compiz issue.

---

### Post by The_Autonomist on 2011-11-06
This same issue is happening to me. Whenever I log out, i get a black screen that stays forever. The only way I can get rid of it is to hit the power button and restart my pc...

i'm running ubuntu 11.10...

Does any one have any idea about this?

---

### Post by gleedadswell on 2011-11-12
Yeah, and it also happens when I switch user rather than logging out.  It seems to be fine with the first switch of user.  But when I try to switch back I get a blank screen.

---

### Post by powersurge360 on 2011-11-16
Mine turned out to be an issue with my screen resolution. I've got a couple of options and if I pick a "wrong" one then it blacks out on me. Found out I had a game that would reset the resolution to a "wrong" one and borked it.

---

### Post by sjnovick on 2012-05-13
I'm having the same problem in 12.04!

But, I've set the resolution to something reasonable.  I shouldn't get a blank screen on logout!

Any solutions?

---

### Post by middlechild on 2012-05-13
Running 12.04, clean install.  One user defined, does not require password at boot but does if you log out. The second user is a Guest Session. Since installing three weeks ago, I can switch back and forth from the main account and the guest one.

Now when I go into upper right corner and log out, the screen goes dark.  I have waited up to an hour for the user selection screen, to allow starting Guest or to log back into my primary but it never appears.

I have not tried to blind type my regular password, I will go try that now.

---

### Post by middlechild on 2012-05-13
Ok, I stand corrected.  I tried both ways, that is through the log out option and by switching user. These are two separate ways to get to a guest user session.  Worked fine both ways.
I'll continue to watch for further occurrences and log them here.

---

### Post by nowhereman2 on 2012-05-30
I am also having this problem with my Ubuntu installation. I am using a 10.04 lucid lynx. This happens intermittently with logout. When I leave my PC alone for a bit of time it will log out after five minutes. Sometimes when I come back I will find a black screen with a small cursor in the upper left corner, or on a few occasions a small segment of text. I think that something is faulting as Gnome trys to load itself but as I am very new to Linux and Unbutu, I am flabbergasted as to what could be the problem (if you can forgive my phrase :P). I have only rebooted the cpu and have not tryed blind typing so I am not sure if this problem is the same or similar to everyone elses, except that it seems to have the same sympotoms and cause. Of course I am new so I can be wrong.
 
This is my first post in these forums and I am trying to expand away from my safe haven in Windows. Anyone like to help me branch out?
 
Thanks in advance.

---

