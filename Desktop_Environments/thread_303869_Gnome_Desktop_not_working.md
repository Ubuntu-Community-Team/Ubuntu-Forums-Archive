---
title: "Gnome Desktop not working"
date: 2006-11-20
forum: Desktop Environments
---

### Post by tsiMental on 2006-11-20
My gnome desktop doesn't work.

It doesn't show any items on the desktop. And nothing happens when I right click on the desktop background.

It does show the background picture though. And the panel loads.

I saw in another thread on another forum that someone else had the same problem with gnome on his redhat installation. He managed to fix it by deleting his user and recreating it.

That's not an option for me. How can I fix this problem?
(I created another user and logged into gnome and it works fine with the other user).

I guess removing and reinstalling gnome doesn't help, since this seems to be related to my user.

Thanks in advance.

---

### Post by CrazyGenie on 2006-11-21
Logout of your Gnome desktop, go to a shell and move all your .gnome* and .gconf* files to a temporary location (or tar them up). Then come to GDM Login screen, select the session as "Default system session" and language as "System default" from GDM Login screen options. Then, login and check. This might, work in case there is some conflict in your .gconf and .gnome configurations. Remember that you will get a Gnome desktop with default settings!!

---

### Post by tsiMental on 2006-11-21
Thank you CrazyGenie.

You truly grant wishes :)

It worked like a charm.

Logged out and into a failsafe terminal.
Where I did the following (from my home directory):
```
tar -cpzf gnome-config.tar.gz .gnome* .gconf*
rm -r .gnome* .gconf*
exit
```When I logged back into gnome, it restored the default settings. - And everything seems to be working :D

---

### Post by The_Apprentice on 2006-11-30
Just to add a bit to this post, I had the same problem.

I followed the above and still got the same problem.

So, I went out to a failsafe terminal and did

sudo apt-get install gnome-desktop-environment

When it has finished, exit out and do the "Then come to GDM Login screen, select the session as "Default system session" and language as "System default" from GDM Login screen options. Then, login and check."

It all worked fine for me then.

---

### Post by farish on 2006-12-08
> **CrazyGenie said:**
> Logout of your Gnome desktop, go to a shell and move all your .gnome* and .gconf* files to a temporary location (or tar them up). Then come to GDM Login screen, select the session as "Default system session" and language as "System default" from GDM Login screen options. Then, login and check. This might, work in case there is some conflict in your .gconf and .gnome configurations. Remember that you will get a Gnome desktop with default settings!!

Thank you so much for this solution!  My Gnome desktop was doing crazy things, ](*,)  but this fixed it right up.  Thanks again!!!

---

### Post by CrazyGenie on 2006-12-14
Nice to know that you all got benefited from my answer.
Cheers,

---

### Post by Ape3000 on 2008-07-17
> **tsiMental said:**
> It worked like a charm.

Logged out and into a failsafe terminal.
Where I did the following (from my home directory):
```
tar -cpzf gnome-config.tar.gz .gnome* .gconf*
rm -r .gnome* .gconf*
exit
```When I logged back into gnome, it restored the default settings. - And everything seems to be working :D

I had the same problem and I didn't need to do it in so complicated way. I just:
```
1. Open your favorite terminal
2. tar -cpzf gnome-config.tar.gz .gnome* .gconf*
3. rm -r .gnome* .gconf*
4. Then just press ctrl + alt + backspace
```
So you don't have to log out for deleting the gnome-files.

---

