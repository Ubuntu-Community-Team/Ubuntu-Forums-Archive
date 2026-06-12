---
title: "xsession can't read .profile"
date: 2010-06-08
forum: Desktop Environments
---

### Post by tripple_des on 2010-06-08
Hello all,
Ive spent the last several days (yes that long) trying to get my nix box back in order. Last week i somehow managed to screw it up big time. I didnt know how and so slowly spent days going through and putting things right.

Im near done, im sure of it, bar one problem which i cant figure out how to get past. You help is much needed.

I got my system to a state where when i authenticate it authenticates me fine, but it fails to load my gnome desktop. It goes black and then reloads the login screen.

I can successfully go into single user mode via the recoveryoption in the grub menu and noticed that .xsession-errors in my users home space was logging:
```
34 Can't open /home/superuser/.profile
```

Ive tried the usual things:
1. Profile is there and looks to have the standard profile content
2. Permisions are rw---r--r so that looks fine also 

What i have i also done is:
1. Deleted the profile (renamed it) in the hope it will generate a new one. When i authenticate it goes to a gnome desktop but the desktop is empty, nothing there, i cant do anything just my background.

2. Created a brand new user but .xsession-error has the same error message for that user's profile.

3. Ran dbpkg to repair any broken dependencies 

But nothing seems to work. 

Thanks for any help

---

### Post by vadimxx on 2010-06-10
Hi all.
I've got the same problem. And I try the same things and also I've changed kernel to 2.6.34-020634 but nothing helps.
I've got intel video 965gm if it helps.
I've found that people got the same problem in Karmic
[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)
[http://ubuntuforums.org/showthread.php?p=8839815](http://ubuntuforums.org/showthread.php?p=8839815)
but advices in the topics didn't solve the problem.

What can we try doing also to solve it?

---

### Post by delcypher on 2010-06-15
I had this problem today. I managed to fix it but I'm not quite sure what fixed it so I'll just have to list the different things I tried.

First of all the error message
```
34 Can't open /home/superuser/.profile
```

Is in the script /etc/gdm/Xsession on line 34. You can try commenting out that line and line 37 for now to see if that helps you.

For me it stopped the login screen from being shown again but gdm just showed a black screen and did nothing so I had to goto to a terminal (CTRL + ALT + F1) and run

> sudo service gdm stop

Here are the things I tried:

1.First of all I noticed that in gdm when I clicked on my username and looked at the bottom of the screen I noticed that the list that let me choose my session was blank. You should have at least GNOME in there.

To fix that I created the file (as root)
```
/usr/share/xsessions/gnome.desktop
```

With the following contents:
```

[Desktop Entry]
Type=XSession
Exec=gnome-session
TryExec=gnome-session
Name=GNOME
Comment=The GNU Network Object Model Environment. A complete, free and easy-to-use desktop environment
X-Ubuntu-Gettext-Domain=desktop_kdebase-workspace

```

The syntax is quite correct as I actually copied this from a file designed for kde, but it works for me.

Once you've made the file restart gdm by running.
```
sudo service gdm stop && sudo service gdm start
```

Now select your user and select the Session "GNOME" (set by the Name= attribute in the file you just made).

2. I completly removed gdm and reinstalled it. This requires an internet connection though. Don't do this if you don't have one.
```
sudo aptitude remove gdm
sudo aptitude install gdm
```

3.Check the partition the /home is mounted from and make sure it has available space. Apparently gdm and gnome has problems if there isn't any space left. You can do this by running
```
df --si
```. Look at the "Use%" column.


I can't guarantee any of these will work for you but I did manage to get my system working again.

As a last resort you could use KDE

To install kdm (KDE) and used it instead of GNOME.
```
sudo aptitude install kubuntu-desktopcd

```


I hope this helps.

---

### Post by adriaanjoubert on 2010-06-16
Had the same problem after trying to uninstall evolution. Finally fixed it by re-installing the gnome-desktop as in 

sudo aptitude install gnome-desktop-environment

Hope this helps,

Adriaan

---

### Post by kusharan on 2011-02-14
delcyphers fix did it for us. I created the gnome.desktop file as mentioned. then rebooted. The session tab listed gnome as an option and was selected. Only thing left to do is that all me windows appear on the far right corner of the screen so they cannot be moved or resized. Only a minor thing considering.

---

### Post by zensys on 2011-04-18
adriaanjoubert, thanks a million, you saved me from a reinstall!!!

---

### Post by CyberBob on 2011-05-02
Allow me to echo what **zensys** said only a week or so ago: 

> **adriaanjoubert**, thanks a million, you saved me ...

from doing some dumb stuff to myself (again).  Reinstalling the gnome-desktop-environment restored all that was wiped (thus breaking my gdm login to the desktop) after I un-installed evolution.

This community is nothing short of wonderful.  Thank You!

---

### Post by RidOfWinFinally on 2013-01-11
Nothing groundbreaking new from my side but I need to join CyberBob's and zensys' chorus, too:

**adriaanjoubert: **
thank you so much - you didn't save me from a reinstall because I had found your thread too late and reinstalled Lucid already (after upgrading to Precise with Unity which I don't like. All steps tried before and while reinstalling were actually a quite good experience to deepen my Linux knowledge).

But you saved me from driving nuts completely, as I did it - removing evolution - again after Lucid reinstall. So, after several hours I restarted the system just for being on the safe side, glad to be back, and then...  >:-[

The only thing I do not really understand: why is it possible that Ubuntu behaves almost (or even worse) like Windows when you try to uninstall Internet Explorer... ?

---

### Post by overdrank on 2013-01-11
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

