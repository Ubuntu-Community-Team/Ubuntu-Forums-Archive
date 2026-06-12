---
title: "Startup Applications - missing!!"
date: 2015-06-26
forum: Desktop Environments
---

### Post by Jon_Parker on 2015-06-26
14.04 LTS with no special mods or anything as I'm new to Ubuntu. I'm trying to add an app called Gigolo to the startup list as it auto-mounts a network share.

SuperWin key - then type startup - only app I see is Startup disk creator.

Trying to launch it form the terminal:

jon@LANFIRE:~$ gnome-session-properties
The program 'gnome-session-properties' is currently not installed. You can install it by typing:
sudo apt-get install gnome-session-bin
jon@LANFIRE:~$ ^C
jon@LANFIRE:~$ sudo apt-get install gnome-session-bin
[sudo] password for jon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-bin is already the newest version.
The following packages were automatically installed and are no longer required:
  apturl apturl-common evolution-indicator libcamel-1.2-45 libgdata13 libt1-5
  libupstart1
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
jon@LANFIRE:~$ ^C
jon@LANFIRE:~$ 


HELP!

---

### Post by kerry_s on 2015-06-26
try "session" in dash search

also your term there tells you to run:
sudo apt-get autoremove
sudo apt-get dist-upgrade

---

### Post by deadflowr on 2015-06-26
Might also do a quick manual search.
Super + A then toggle the Installed Applications, and scroll down.
See if it shows up that way.
It'll be listed way down, since it shows everything alphabetically...

An even more manual approach is to open Files and go to the left pane, click on Computer, then go to usr, then share, then applications and scroll down till you get to the S listings.
If it is there then simply doubleclick to launch it.

---

### Post by Jon_Parker on 2015-06-27
> **kerry_s said:**
> try "session" in dash search

also your term there tells you to run:
sudo apt-get autoremove
sudo apt-get dist-upgrade

Hi,

Those haven't worked, but thanks for the suggestion.

Jon

---

### Post by Jon_Parker on 2015-06-27
> **deadflowr said:**
> Might also do a quick manual search.
Super + A then toggle the Installed Applications, and scroll down.
See if it shows up that way.
It'll be listed way down, since it shows everything alphabetically...

An even more manual approach is to open Files and go to the left pane, click on Computer, then go to usr, then share, then applications and scroll down till you get to the S listings.
If it is there then simply doubleclick to launch it.

Hi,

Nope - it's simply not there! Grrrr! This is so frustrating!

---

### Post by deadflowr on 2015-06-27
Not the best solution, but do you happen to have the autostart folder in the .config folder?
(ctrl +h to view dot folder/files as they are normally hidden from view)

If so, perhaps try creating a startup desktop file.

Basically it would look like this
```
[Desktop Entry]
Type=Application
Exec=the command goes here
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Whatever name you want to call it goes here
Name=Whatever name you want to call it goes here
Comment[en_US]=
Comment=
```
then save it as a .desktop file in the .config/autostart folder.
(something like gigolo-start.desktop)
then see if it works.

Not optimal, but it might be something.

Also, side question, but what did you remove?
I ask because your first post lists several packages no longer needed and that usually comes after you remove packages.
(and I see there haven't been any upgrades I can tell for, at least, apturl on trusty...)

---

### Post by mc4man on 2015-06-28
The above post should work, certainly value in seeing how to create a 'startup app' manually.

As far as package error what do these show?
```
apt-cache policy gnome-session-bin
```
```
apt-cache madison gnome-session-bin
```

---

### Post by Bucky Ball on 2015-06-28
To launch it from a terminal, you type:

gigolo

That's it. What does it say? It is installed as far as the Software Centre is concerned?

---

### Post by Jon_Parker on 2015-06-28
> **mc4man said:**
> The above post should work, certainly value in seeing how to create a 'startup app' manually.

As far as package error what do these show?
```
apt-cache policy gnome-session-bin
```

```
jon@LANFIRE:~$ apt-cache policy gnome-session-bin
gnome-session-bin:
  Installed: 3.12.1-0ubuntu1~trusty3
  Candidate: 3.12.1-0ubuntu1~trusty3
  Version table:
 *** 3.12.1-0ubuntu1~trusty3 0
        500 [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     3.9.90-0ubuntu12.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     3.9.90-0ubuntu12 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
jon@LANFIRE:~$ ^C
jon@LANFIRE:~$ 
```


> **mc4man said:**
> 
```
apt-cache madison gnome-session-bin
```

```
jon@LANFIRE:~$ apt-cache madison gnome-session-bin
gnome-session-bin | 3.12.1-0ubuntu1~trusty3 | [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/) trusty/main amd64 Packages
gnome-session-bin | 3.9.90-0ubuntu12.1 | [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
gnome-session-bin | 3.9.90-0ubuntu12 | [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
gnome-session | 3.9.90-0ubuntu12 | [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main Sources
gnome-session | 3.9.90-0ubuntu12.1 | [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main Sources
jon@LANFIRE:~$ 
```

I have no idea what any of this means!

JP

---

### Post by Bucky Ball on 2015-06-28
Please use code tags for terminal output. Last link in my signature. Thanks. ;)

---

### Post by CantankRus on 2015-06-28
You appear to have the GNOME3 Staging ppa enabled which may be causing conflicts.
> GNOME3 Staging
PPA description
This PPA will be used to test uploads before they are copied to the main GNOME 3 PPA.

=== *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

=== Installing ===
To use this PPA, you should enable the main GNOME3 PPA.

- You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please read the output before entering 'Y' to make sure important packages won't be removed.

=== Removing ===
**Use ppa-purge to remove this PPA**. It is *particularly* important to do this before upgrading to a new release!

=== Bugs ===
Please use 'ubuntu-bug' to report bugs against packages in this PPA
```
sudo apt-get install ppa-purge
```
```
sudo ppa-purge ppa:gnome3-team/gnome3-staging
```

---

### Post by mc4man on 2015-06-28
There is a bug with the gnome3 ppa's  gnome-session-bin package , here's one report, maybe others.. [https://bugs.launchpad.net/ubuntu-gnome/+bug/1310003](https://bugs.launchpad.net/ubuntu-gnome/+bug/1310003)
(any version over 3.9.90 will show this behavior.
So either live with or use the official 14.04 version... ppa-purge would do the job as noted.

---

