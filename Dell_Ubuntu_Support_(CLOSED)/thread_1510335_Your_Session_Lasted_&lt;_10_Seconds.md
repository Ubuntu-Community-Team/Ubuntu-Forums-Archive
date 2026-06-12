---
title: "Your Session Lasted &lt; 10 Seconds"
date: 2010-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirius1 on 2010-06-15
After trying to update openoffice.org to 3.0 via Synaptic Package Manager, I got the error message about Fix Broken Packages. I shut down and powered up after lunch. The login window shows the following error message:

```
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
```

Behind this code is my desktop, but I can't access it.

I'm in Failsafe Terminal, which is the only place I can be. I don't want to screw it up from here. What should I do to logon and access my home folder again?

Thanks.

---

### Post by mikewhatever on 2010-06-16
I am confused, since when is OpenOffice3 in 8.04 repositories?
As for the problem, the error suggests you may be lacking free disk space. Do you think it probable?
To check the free space status, run **df -h**. 
If the root partition is full, run **sudo apt-get clean**.
To deal with the broken package, **sudo apt-get install -f**.

---

### Post by ianmillington on 2010-06-16
You could take a look here

[http://www.justlinux.com/forum/showthread.php?p=890381](http://www.justlinux.com/forum/showthread.php?p=890381)

---

### Post by sirius1 on 2010-06-17
> OpenOffice3 in 8.04 isn't in 8.04 repositories . . . I learned that 

$ df -h 
Filesystem     Size     Used     Avail     Use%     Mountd on
/dev/sda2      7.1G     3.1G     3.7G      46%      /
varrun         1009M    92K      1009M     1%       /var/run
var lock       1009M    0        1009M     0%       /var/lock
udev           1009M    52K      1009M     0%       /dev 
devshm         1009M    0        1009M     0%       /dev/shm
lrm            1009M    1.7M     1007M     1%       /lib/modules/2.6.24-27-lpia/volatile

Root partitio wasn't full.

$ sudo apt-get install -f
Reading package lists... Done
Bulding dependency tree
Reading state information... Done
0 Upgraded, 0 newly installed, 0 to remove and 0 to upgrade.

$ ls -ld /home/staton
drwxrwxr-x 49 staton staton 4096 2010-06-17 0800 /home/staton

What else might help you? Thank you.

---

### Post by sirius1 on 2010-06-17
ian, thanks, I read 
[http://www.justlinux.com/forum/showthread.php?p=890381](http://www.justlinux.com/forum/showthread.php?p=890381)

which talks about /.ICEauthority I ran:

chown -R username:usergroup /home/username
chmod -R ug+rw /home/username

as you can see fron above. 

When I 'View details' of the 10 second error messasge:
/etc/gdm/Ssession: Beginning session . . . 
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/defaut.
find: /usr/share/gnome/autostart/usrshare/ume-config-common/ume-gui-start: line 11: /usr/lib/sapwood-server No such file or directory.
: No such file or directory
matchbox-wm: unable to open theme: /usr/share/themes/mobilebasic/matchbox/theme.xml . . .

it goes on. Somehow after updates I got the hildon-desktop loaded,I don't beleieve I want.

---

### Post by ugm6hr on 2010-06-18
Let's start from the beginning... I presume this is a Mini 9.

How did you try "to update openoffice.org to 3.0 via Synaptic Package Manager" when it isn't in the repo?

---

### Post by sirius1 on 2010-06-22
Sorry ugm got called away for a few days.

1. I tried to upgrade Open Office.org to 3.1 in Synamtic Package manager.
2. This is A Dell Mini 9 Hardy 8.04.
3. I receive the error message, failed to fetch [http://ppa.launchpad.net/openffice-pkgs/ppa/ubuntu/dist/haardy/Release.gpg](http://ppa.launchpad.net/openffice-pkgs/ppa/ubuntu/dist/haardy/Release.gpg) Could not resolve 'ppa.launchpad.net'
4. I understand this now.

This is exatly where I am as of this morning:
I enter Username and password ENTER

```
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
```

Then, I can see my desktop in the background, and the "Wireless Network Authentication Reuired" message appears. (This is OK because I changed the passphrase and need to re-enter it. For the time  being, I cancel this dialogue box.

Right now, I'm looking at the session lasted < 10 seconds, message, with my desktop in the background.

I will read over what you posted and keep in touch. Thanks for your time!

---

### Post by sirius1 on 2010-06-22
Correction, I deleted openofffice.org2 via command line, then tried to install openoffice.org 3.0.

The deletion completed, the installation did not, obviously :)

---

### Post by ugm6hr on 2010-06-22
Your options:
1. Just start again with Ubuntu 10.04 (which I would recommend).
2. Correct your sources.list file by removing all non-default repos, and then apt-get update / install -f

Let us know which you would prefer, and we can help you try and resolve.

---

### Post by sirius1 on 2010-06-23
1. I do intend to move to 10.0, but want to redolve this issue first, can't reload every time there is a problem, I've found  :popcorn:

2. Anyhow . . . from the failsafe terminal, I attempted:
```

$ gksudo gedit sources.list
```

which returned the command prompt and nothing else. Then I ran:
```
$ gksudo nautilus
```

which usually loads the file. This time it didn't. I navigated through:

etc > apt > sources.list. It is a valid file. I clicked on sources.list to open it, with the 'custom command' gksudo gedit ... nothing happened.

Can I correct the login problem, and then edit my sources.list file?

---

### Post by sirius1 on 2010-06-27
OK, ugm, I went off for a few days to read through the great documentation, beginning with Ubuntu Pocket Guide.

I would like your help to resolve this problem, before I reload, as you suggest.

My repositories via Failsafe terminal > Synaptic. Currently read:

[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-main
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-multiverse
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-universe

That **is not** at all what they used to be, before this probem. They were:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) hardy main

(I deleted the Oo.o debs, and uninstalled openoffice.org)

What is the next step?

Tnank you! :p

---

### Post by sirius1 on 2010-06-27
Re: Your Session Lasted < 10 Seconds

ugm, Hello! Unfortunately, I did not direct my recent answer, to your post to the right staff member. I replied to myself. 

factory Dell Mini 9 Hardy heron

Appreciate your help . . . .

---

### Post by ugm6hr on 2010-06-27
Honestly, I have never encountered this.  But without specific detail about how your sources.list got changed, and what you did, this is going to be impossible.

All I can suggest is returning sources.list to what it is supposed to be, then running 
```
apt-get update
apt-get install -f
```

If that doesn't work, I'm not sure what else to suggest.

---

### Post by sirius1 on 2010-06-28
I was able to correct my sources.list file via Synaptic in Failsafe terminal per my previous post.

I had a backup of ~/.profile, so I deleted:

.Xauthority
.ICEauthority
.xsession-errors (alas, I finally found that!)
.gconf
.gconfd

I can now login again through Ubuntu GNOME. Ran
```
apt-get update
apt-get install -f
```

Updates went well, and I'm now moving things back over. Thanks for the pointers! ):P

---

