---
title: "Installing GNOME on Kubuntu Breaks KDM ('dpkg-reconfigure kdm' does NOT Help)"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Thorsten on 2005-10-24
[EDIT]
I just solved the problem. It turns out that the culprit was sabayon, a GNOME admin tool. (I have no idea why this is executed by /etc/X11/Xsession, even when we start KDE from kdm. Bad, bad integration!)

Anyway, to fix the problem, run sabayon as root ("sudo sabayon"), create a profile ("default" worked for me) and enable this profile for all users. Bingo, kdm now works as before! (It appears sabayon was installed when I installed GNOME and that's the reason why I didn't have this problem before.)
[/EDIT]

Last night I installed GNOME--just for testing--on top of my finely tuned Kubuntu installation (5.10, originally installed from Kubuntu 5.10 preview and regularly updated.) After that, I could use kdm only to login using the failsafe option. Choosing KDE, GNOME, or even XCFE4 would fail (kdm would simply reappear after a few seconds of black screen.)

Shutting down kdm and manually starting startkde did not help, either.

After installing ubuntu-desktop, I can now use Ubuntu's gdm to login to KDE, GNOME, and XFCE4, but I can't get kdm to work, again. Sure, I can activate kdm with "dpkg-reconfigure kdm", but when I try to login from kdm into KDE *or* GNOME, I again just get a blank screen for a few secs and then kdm will be back.

Any ideas?

Thanks,
Thorsten

P.S. I have both ubuntu-dektop and kubuntu-dektop installed.

---

### Post by shinygerbil on 2005-10-24
This is probably totally irrelevant, but I had a problem logging in a few days back. It turns out I'd ran out of hard disk space - I could log in as root, but only through the command line, and if I tried to log in using kdm I got the same symptoms as you're reporting. I didn't get round to trying gdm. (I have Gnome and KDE installed, i.e. ubuntu-desktop and kubuntu-desktop, but i started with gnome)

The obvious solution was to free up some disk space - after that it worked fine.

Like I said, it's probably of no use to you, but just in case...

Steve

---

### Post by byourg on 2005-10-24
I had the same thing happen to me after installing a few apps needing the Gnome file system files to work. What I found out was some of the files in /home/<username>/.kde/share/config got changed to root ownership so I as a user could not use these files by permission rights. What else got changed in the kdm file system I don't know. I just reinstalled Kubuntu and was careful of what I installed after that, looking in that folder for changes by root. Hope this helps!

---

### Post by Thorsten on 2005-10-24
[quote=byourg]I had the same thing happen to me after installing a few apps needing the Gnome file system files to work. What I found out was some of the files in /home/<username>/.kde/share/config got changed to root ownership so I as a user could not use these files by permission rights.[/quote] 
```
$ find ~/.kde -uid 0
``` doesn't find anything. In any case, I can start both KDE and GNOME as a regular user, but only from gdm. I can run kdm, but not start any sessions from kdm (except for failsafe.)

It looks more like some sort of modules or library conflict to me.

Thanks anyway,
Thorsten

P.S. I do have plenty of free disk space on all partitions.

---

### Post by metoo on 2005-10-26
Well, tryed it brute force?

sudo apt-get install --reinstall kdm
or even
sudo apt-get install --reinstall kubuntu-desktop

as long as the files are still in the /var/cache/apt/archives , nothing will be downloaded.

Might just worth a try.

---

### Post by Thorsten on 2005-10-28
[quote=metoo]Well, tryed it brute force?

sudo apt-get install --reinstall kdm
or even
sudo apt-get install --reinstall kubuntu-desktop
[/quote] 
What is that supposed to accomplish that wouldn't be accomplished by 
     dpkg-reconfigure kdm
     dpkg-reconfigure kubuntu-desktop
?
I'm just curious.

BTW Are there other people who have installed GNOME on top of Kubuntu and are still able to start KDE from kdm?

Thorsten

---

