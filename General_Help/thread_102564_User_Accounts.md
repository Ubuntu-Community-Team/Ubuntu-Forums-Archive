---
title: "User Accounts"
date: 2005-12-12
forum: General Help
---

### Post by John Jason Jordan on 2005-12-12
Ubuntu-64 Breezy on Compaq R3240 Laptop

I recently goobered up my user account (jjj) and it took two days of searching everywhere on the net to get things back. Ultimately it took help from someone on IRC #linuxhelp to get the account working again. The process left me with a couple questions:

1) Is there a "clone user" account? I'd like to clone myself so there is an alternate to log in with in case something like this ever happens again. I know about adduser -- but the new user does not have my settings.

2) I did an adduser as jxj and jxj had all kinds of software that I had uninstalled. When I uninstall something I want it to remain forever uninstalled. I always install and uninstall with Synaptic, which requires root password to open. Therefore I assumed all install/uninstall activity was for the computer and every user on it. Where have I gone wrong?

---

### Post by encompass on 2006-01-11
If you uninstalled it... it's uninstalled. :)  as for creating an account with your own settings that would be something called a backup... if you have a copy of the same user in another place, wouldn't that account with the same settings have the same problems.
A=B
if A is bad then B is bad
I would have your user account in a stable state... then back-it up in a nice location.  You rally don't have to back everything up... ussually just the hiddle files... none of the things you have saved.  I have hand my account go down for a number of reasons... and the best way I have found to restore it... is simply bring back my backup that I do every week.  I can even make copys in such a way that it won't destroy my old data.

---

### Post by John Jason Jordan on 2006-01-11
[QUOTE=encompass]If you uninstalled it... it's uninstalled. :)[/QUOTE]
But that isn't what happened. As jjj I had uninstalled Nautilus. Much later I created a new user, jxj. When I logged in as jxj, there was Nautilus. Several other programs that I had removed were back as well. When I uninstalled Nautilus I did so while logged in as jjj. However, I did it with Synaptic, which required root password to open. I'm just trying to figure out how to uninstall a program forever. Like, when I want something gone I want it to be like "hit the road, Jack, and doncha come back no more, no more, no more."

[QUOTE=encompass] ... as for creating an account with your own settings that would be something called a backup.
I would have your user account in a stable state. then back-it up in a nice location.  You rally don't have to back everything up. usually just the _hiddle_ files. none of the things you have saved.  I have hand my account go down for a number of reasons. and the best way I have found to restore it is simply bring back my backup that I do every week.  I can even make copies in such a way that it won't destroy my old data.[/QUOTE]
Where is my account? How do I back it up, that is, is it one file somewhere? Or is it like Windows, with settings scattered all over the Registry?

And speaking of backups, I have learned how to do a backup with Dump, and have done so of the entire computer to an external USB pocket drive. However, I have yet to find a backup utility that is simple enough for a beginner to understand and is designed for backing up just one, standalone computer to an external drive. God help me if I ever actually have to restore from Dump. Surely there is something better out there.

---

### Post by encompass on 2006-01-12
Youy account is everything in your user directory... for me that is /home/jason/
everything in there... even the hidden things... are what my user has for saved settings... even old programs that where installed have the old saving in case you want them. (I do)  If you want to backup your user.. just copy that data to another location... like your drive.  If you want to keep file permissions... look into rsync... that program does a very good job... and when you want to keep the backup current.. rsync will only backup the changes and not have to copy EVERYTHING over every time.  That is interesting that you wanted to remove nautilus.. I am not sure if you know this... but it is what draws your background wiht all the icons on it.  It also may be that it is required in the ubuntu installs.  I would post another thread just about removing nautilus... that should answer your question faster.

---

