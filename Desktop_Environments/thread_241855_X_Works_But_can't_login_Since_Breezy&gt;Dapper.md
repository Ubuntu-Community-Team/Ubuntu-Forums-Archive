---
title: "X Works But can't login Since Breezy&gt;Dapper"
date: 2006-08-22
forum: Desktop Environments
---

### Post by jazzfish on 2006-08-22
I don't think this is the same X-Broken issue - 

I did an upgrade from Breezy to Dapper over the Internet.  Took a while but seemed to go OK. But I can't get to my desktop.

I get a graphical login screen so X Graphics must be working. BUT I can't complet a login and get to my Gnome desktop. AFter I enter the username/PW The screen changes and appears to be starting up the window manager - I see the rectangur UBUNTU graphic then the screen goes black.  Then the Login screen returns. HELP!!  

I tried using WGET to get and earlier X core (in the console) then
sudo dpkg -i xerver-xorg-core*.deb (after the wget.. That seemed to work but no change in behaviour. 

The GDM log says something about GLibcore not loading.

I also renamed all the Gnome related files to .bak's but that made no difference. 

Any explanation why the screen continues to respawn?  Can anyone suggest logs I should look at or what I can do?  I am getting close to the point of trashing the entire install but I really prefer not to do that.. H-E-L-Ppppp.... 

- Bob

---

### Post by Boelcke on 2006-08-23
There was just an announcement on the front page of the forums that a recent update of Xserver makes the X windows system completely fail.  It refers you to:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

I'm thinking that your upgrade from Breezy to Dapper just happened to coincide with this unfortunate bug release.  It might not be anything you did!!!

---

### Post by jazzfish on 2006-08-23
Thanks for the link to the fix for ver XOrg... V10.3.  I took the steps in the link you sent me. Unfortunately I already have 10.4 installed.  I tried rebooting after I took the steps in the blog entry but no change.  The login screen comes up nicely. It accepts my password. Displays the new rectangular Ubuntu graphic. The screen goes black for about 3 seconds. Then the login screen redraws yet again..

I wonder if it must have something to do with the Gnome  desktop.. 

Is there a log entry somewhwere that shows the steps X is taking to bring up the login screen?  I wonder what component is responsible for redisplaying the login splash screen...  

Still looking...

---

### Post by simohell on 2006-10-13
I have this same problem with a desktop I upgraded from Breezy to Dapper.

- Login succeeds 1 out of 10 the first try
- Login succeeds 4 out of 10 the second try
- Login succeeds 3 out of 10 the third try
- Login succeeds 1 out of 10 the fourth try
- Login succeeds 1 out of 10 the fifth to tenth try

So it might take 50% of times 3 or more logins to get through.

I think it is user related problem - with my another username I haven't experienced the same problem.

---

### Post by simohell on 2006-10-13
The syslog gives some info:

*time* localhost gconfd (*user*-*processnumber*): Recieved signal 15, shutting down cleanly
*time* localhost gdm[*processnumber*]: Error reinitilizing server
*time* localhost gconfd (*user*-*processnumber*): Exiting

---

### Post by kingcharles1666 on 2006-10-24
I have the same problem but with me it started after an upgrade from dapper to edgy. Was there a fix for this?
I have 2 users set up on my machine (AMD64) but none of them work.
 0 out of 10 times, 100% failure.
But on my machine it does show the desktop of the user that tries to log on but after a few seconds it drops back (logout?) to the login screen

---

### Post by simohell on 2006-10-30
> **kingcharles1666 said:**
>  Was there a fix for this?

No, not any I know of.

---

### Post by CatKiller on 2006-10-30
It sounds very much like you've got something quite broken in your session startup scripts that causes Gnome to crash very shortly after logging in. Especially you, simohell, since you weren't having the problem with a different user.

---

