---
title: "GNOME crashing during log in - help"
date: 2005-06-12
forum: Desktop Environments
---

### Post by davegahan on 2005-06-12
During watching a DVD in Totem I got an error message that GNOME panel would restart due to an error. When I shut down my computer the machine was hanging during the shut down sequence and I had to remove the battery of my laptop as the machine would neither accept "ctrl-alt-del".

Now when I boot up, after entering my name and password in the GNOME log in screen,  the machine goes blank and returns 5-6 seconds later back to the log-in screen. I cannot get into GNOME even with the failsafe log-in.

I can get fail-safe terminal to work.

My question is, *** can I apt-get GNOME to do a reinstall and have GNOME working properly again - if so, **what package** do I need to downlad and install *** ?

HELP ! I am writing this from my friends windows PC and I need access to my Ubuntu box.,

---

### Post by Alexander Kirillov on 2005-06-12
[QUOTE=davegahan]During watching a DVD in Totem I got an error message that GNOME panel would restart due to an error. When I shut down my computer the machine was hanging during the shut down sequence and I had to remove the battery of my laptop as the machine would neither accept "ctrl-alt-del".

Now when I boot up, after entering my name and password in the GNOME log in screen,  the machine goes blank and returns 5-6 seconds later back to the log-in screen. I cannot get into GNOME even with the failsafe log-in.

I can get fail-safe terminal to work.

My question is, *** can I apt-get GNOME to do a reinstall and have GNOME working properly again - if so, **what package** do I need to downlad and install *** ?

HELP ! I am writing this from my friends windows PC and I need access to my Ubuntu box.,[/QUOTE]
 The problem is likely to be with various gnome config files in your home directory. 
Try logging in form text console and then rename directories 
~/.gnome, ~/.gnome2, ~/.gnome_private, ~/.gnome2_private
adding .backup to each of them. Now try logging in again in grpahical mode. 


This way, you lose much of your gnome customization -- panel objects, themes, etc - but this shouldn't be a great loss. 

If this fails, login in text terminal and look at the file ~/.xsession-errors 
Post its contents here.

---

### Post by davegahan on 2005-06-12
I wish now I was proficient in using the command line.

How to find those files with the command line  - how to change their names ?
How to find the file you were mentioning and post its contents ?

I`ll promise to school myself in terminal use - but for now - I am in serious trouble not being able to get into my GUI to to the usuall stuff.

Could you be so kind to be more specific ?

---

### Post by polt on 2005-06-12
Can you login as root?

---

### Post by Joeb on 2005-06-12
[QUOTE=davegahan]I wish now I was proficient in using the command line.

How to find those files with the command line  - how to change their names ?
How to find the file you were mentioning and post its contents ?

I`ll promise to school myself in terminal use - but for now - I am in serious trouble not being able to get into my GUI to to the usuall stuff.

Could you be so kind to be more specific ?[/QUOTE]

The directories mentioned are hidden directories (any directory begin with a period is a hidden directory).  To see them from the command line you would type ls -a and it would show you everything in the directory, hidden (with a dot infront or not).

To rename things you need to move them so to rename .gnome to .gnome.backup you would type:  mv .gnome .gnome.backup

In the post telling you to move, where it said move ~/.gnome to ~/.gnome.backup, the ~ is a command line shortcut for your home directory.  If your user name were bob, then ~/.gnome is the same as /home/bob/.gnome.

So, if you can get to a terminal window, or command line (try pressing ctl-alt-f1) you can do all of those moves like:
  mv ~/.gnome ~/.gnome.backup
  mv ~/.gnome2 ~/.gnome2.backup
etc.

 If you are actually in your home directory, then you can ommit the ~/ in each of the commands.  Chances are if you move all of those .gnome directories and then log back into gnome, things will work (but you will have lost and custom settings you made to gnome).  Also, if you got to the command line by the ctl-alt-f1 I mentioned above, you would need to hit ctl-alt-f7 to get back to the graphical login manager (gdm).



Hope that gets you started.

---

### Post by desdinova on 2005-06-12
Its more likely the session has got corrupted perhaps... My guess its hanging on gnome-session-manager

---

### Post by Joeb on 2005-06-12
[QUOTE=desdinova]Its more likely the session has got corrupted perhaps... My guess its hanging on gnome-session-manager[/QUOTE]


Deleting the various .gnome and .gnome2 files in his home directory will fix that, though.  Won't it?

---

### Post by desdinova on 2005-06-12
[QUOTE=Joeb]Deleting the various .gnome and .gnome2 files in his home directory will fix that, though.  Won't it?[/QUOTE]
 I'd try just $HOME/.gconf/apps/gnome-session/* first

---

### Post by Xian on 2005-06-12
[QUOTE=davegahan]Now when I boot up, after entering my name and password in the GNOME log in screen,  the machine goes blank and returns 5-6 seconds later back to the log-in screen. [/QUOTE]
Does it give you a message like, "...your session lasted less than..."?
Can you ctrl+alt+F1 to get to a shell, login, and enter the command below.

Are there any error messages displayed?

```
$ sudo /etc/init.d/gdm stop
$ sudo startx
```

---

