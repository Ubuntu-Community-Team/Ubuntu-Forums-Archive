---
title: "Lost Administrative privileges"
date: 2006-12-02
forum: Desktop Environments
---

### Post by dsimpson on 2006-12-02
I just signed onto WildBlue, a satellite internet service and upon getting the system running lost all admin capabilities. I cannot use synaptic, enter networking and check my connection, cannot do upgrades, downloads which require administative permissions. I was previously on a dialup connection and when I switched to the satellite internet hookup I was working in Networking, deleted all the settings I thought applied to my previous internet connection and hit ok, it was then a message popped up which stated that since I requested changes I would not be able to access the site as username, I assumed (wrongly, i think) that it pertained to my internet connection identity, and wasn't applying to my administration privileges. anyway, I need to reestablish myself as the user with administrative authority so that I can again have control over the functions which will allow me to do upgrades make changes, etc. REALLY need help on this one.

---

### Post by taurus on 2006-12-02
What's the output of this command from a terminal?

```
groups
```
You need to belong to groups adm & admin to use sudo/gksudo...

---

### Post by CatKiller on 2006-12-03
I think you might have broken your /etc/hosts file. Lots of people have done it, so there are many posts about it.

Basically, you need an alias to your localhost (127.0.0.1) called the same as your computer's host name (defined in /etc/hostname). You'll need to boot into recovery mode, from the GRUB menu, to automatically log in as root, and then use **nano /etc/hosts**.

You'll want the first line to look something like this:

**127.0.0.1 localhost.localdomain localhost local *hostname***

---

### Post by dsimpson on 2006-12-03
For Taurus, thanks for the reply, the output for groups is:

adm dialout cdrom floppy audio dip video plugdev scanner admin

Is there anything that is of help here? I am new to Ubuntu and Linux so will need explicit help and directions.

catkiller, thanks for the info, but I need to start at the beginning, first off, I will need to know how to boot from GRUB, and then into recovery mode, as to the first line, is that what I will look for or something I would enter? And after that how will the password issue be resolved, will it automatically be restored when I am listed as root? I know this is a lot of questions but I am really delving into this for the first time and need a lot to learn. HELP!

---

### Post by CatKiller on 2006-12-03
> **dsimpson said:**
> catkiller, thanks for the info, but I need to start at the beginning, first off, I will need to know how to boot from GRUB,

You already do :)

GRUB is the bootloader that you can use to choose which operating system you boot from. If you've only got the one operating system on there, you've probably not looked at it much, but when you boot the computer there will be a line that says something like "Press Esc to enter GRUB menu".

>  and then into recovery mode, as to the first line, is that what I will look for or something I would enter?

Since you mentioned deleting all the hosts, it's probably something that you would have to enter. With the way that some people have broken it, it would be something that they would look for and change. Don't forget that the ***hostname*** that I put in there should be changed to whatever it says in /etc/hostname.

>  And after that how will the password issue be resolved, will it automatically be restored when I am listed as root? 

Either not having a computer name in your /etc/hosts, or having one that differs from the name in /etc/hostname **will** make it so that you can't use sudo. It seems likely to me that this is your problem, and so fixing it will make you able to use sudo again. You might need to reboot to make it work, but you'd need to reboot anyway if you're in recovery mode. 

Good luck!

EDIT: When you're using nano, Ctrl-O saves and Ctrl-X exits. It does actually say at the bottom of the screen, but a lot of people seem to find that confusing.

---

### Post by dsimpson on 2006-12-03
CatKiller, tried going into Grub, everything was total confusion to me, I got a line with a cursor, a message which said something like 2 lines acceptable to IPV6 or something like that and there were no lines of information listed in the window. entered /etc/hosts and it said premission denied. didn't know where to go from there, couldn't even figure out how to exit so rebooted. I think you figure I know a little about Ubuntu, but this isn't the case, I know absolutely nothing and every little thing will need to be explained or I will continue to have serious problems. Sorry, wish I did know more.:confused:

---

### Post by CatKiller on 2006-12-03
Just take it slowly. Almost everything has already been said in this thread and, as I say, there are many others.

First of all, restart your computer.

Then, as it starts, you'll get a line inviting you to enter the GRUB menu. Press Esc to go into the GRUB menu.

You'll be presented with a list of options - pairs of different versions of the Linux kernel, and then memtest86+ at the bottom. Pick one of the ones that says (recovery mode) at the end. It doesn't really matter which one, if there's more than one.

This will automatically log you in as root. You can tell this by the fact that it says *root@* and your prompt is a **#** rather than the usual **$**.

Type ```
more /etc/hostname
``` This should return a single word that is the same as what it says after the @ sign. Write this down, or otherwise remember it exactly.

Type ```
nano /etc/hosts
``` From what you've said, you might have managed to get that far on your last attempt. This will open a command-line text editor called **nano**. On the very first line, above where it might say > # The following lines are desirable for IPv6 capable hosts write ```
127.0.0.1 localhost.localdomain localhost local *hostname*
``` where *hostname* is the word you wrote down earlier.

Press **Ctrl-O** to save, confirm the name by pressing Enter, and then press **Ctrl-X** to exit.

Type ```
shutdown -r now
``` to restart your computer.

Just don't panic, and you'll be fine.

---

### Post by taurus on 2006-12-03
To view those two files, run
```
less /etc/hosts  /etc/hostname
```
To edit them, run
```
nano -w /etc/hosts
nano -w /etc/hostname
```
And if you need to reboot from recovery mode, run
```
shutdown -r now
```

---

### Post by dsimpson on 2006-12-03
Hi Guys, CatKiller and Taurus, thanks for all the help and patience, I am again (finally) back in charge. The next step in my evolution is to learn exactly why and what worked, but for now I am very happy that it all works again. Thanks much.:-D

---

### Post by Emily on 2007-01-04
I am also having this problem but the solutions mentioned here aren't working for me.

-- The hostname is already identical in /etc/hosts and /etc/hostname. 
-- The word "local" was missing from the argument mentioned by CatKiller: [COLOR="Purple"]127.0.0.1 localhost.localdomain localhost **local ***hostname*[/COLOR] ... but I added it. No change.
-- When I tried "addgroup emily admin" as suggested [here]("http://www.ubuntuforums.org/showthread.php?t=233502"), and "addgroup emily adm" I got a line saying that my username was already part of these groups.

I can login as emily using the password that I'm 99% sure is the correct one, and I can run things from the Administration menu that request my password with no trouble. Only when I try su or sudo does it reject that password. It has to be the same one, doesn't it?

I'm not sure this is the right section for my question, but this thread seems to have the most discussion of the problem that I could find.

---

