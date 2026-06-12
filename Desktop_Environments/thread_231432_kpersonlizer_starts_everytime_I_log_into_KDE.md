---
title: "kpersonlizer starts everytime I log into KDE"
date: 2006-08-07
forum: Desktop Environments
---

### Post by mexlinux on 2006-08-07
Hi 
I did my update to kde 3.5.4 and everything went OK, It worked very good but ater some sessions, when I loged into KDE kpersonalizer started, and now it does every time I log in!

I guess some file might be corrupted or something like that, but where to look for?

Any help will be really appreciated!

Thanks in advance
Miguel

---

### Post by RajivNair on 2006-08-10
hi miguel,
 today even i faced this same problem,u can rectify it by:-

To stop it from starting every time, edit 
/home/your_name/.kde/share/config/kpersonalizerrc

(while kpersonalizer isn't running) and add those lines:

[General]
FirstLogin=false

you dont need to be a root user since u r changing a file in ur home directory.i found this lil piece of info from :-
[http://mozillaquest.com/Linux02/Mandrake_Linux_8-2_ships_update_story-01.html](http://mozillaquest.com/Linux02/Mandrake_Linux_8-2_ships_update_story-01.html)
by searching in google.

regards,
Rajiv Nair.

---

### Post by mexlinux on 2006-08-16
Thanks, It worked

---

### Post by msak007 on 2006-09-04
I just ran into this problem on 2 different computers, and discovered it's a Kubuntu specific bug with KDE 3.5.4 (not sure if it's been reported yet). [Here's]("http://www.kde-forum.org/artikel/15137/KDE-wizard-after-every-reboot-why.html") a post I found in a KDE forum with a more complete solution. Editing the kpersonalizerrc file in your home directory will only resolve the issue for one user. In addition to that (editing each existing user's kpersonalizerrc file), you also have to edit the main file that it is generated from to prevent it from happening for all / new users.

---

### Post by Copter on 2006-09-09
Hi RajivNair,

It also worked on my box. Thanks a lot :)

Copter :]

---

### Post by cherry316316 on 2007-10-28
I am having a similar problem but with "KILE"

i am using ubuntu-gnome and I have kile installed
and everytime I login , it starts automatically , I dono why!
I tried to check every damm place to stop the auto start of kile 
but no success so far.

when I run kile from terminal this is the output i get 
```
 kbuildsycoca running...
kile: ERROR: Could not create symlink: /home/cherry/.lyx/lyxpipe.in --> /tmp/kde-cherry/kileXknNqM/.lyx/lyxpipe.in
kile: ERROR: Could not create symlink: /home/cherry/.lyx/lyxpipe.out --> /tmp/kde-cherry/kileXknNqM/.lyx/lyxpipe.out
kdecore (KProcess): WARNING: _attachPty() 14

```

I also tried to put

```
 FIRSTLOGIN=false 
```
in the kile file of same folder.
and I also installed lyx
but I have no idea for the source of error

---

