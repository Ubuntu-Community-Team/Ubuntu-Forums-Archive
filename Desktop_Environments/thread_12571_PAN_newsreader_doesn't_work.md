---
title: "PAN newsreader doesn't work"
date: 2005-01-25
forum: Desktop Environments
---

### Post by granite230 on 2005-01-25
Hi I tried to install PAN on Ubuntu Linux but it wont work.

**Here's what I did:**

sudo gedit /etc/apt/sources.list

Add the follow lines to the end of the file...

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe

After this, File&gt;Save! :-) Then 2 more steps...

apt-get update
apt-get install pan

**Here's what I get:**

granite@granite:~ $ sudo apt-get install pan
Reading Package Lists... Done
Building Dependency Tree... Done
pan is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pan: Depends: libatk1.0-0 (>= 1.9.0) but 1.8.0-1ubuntu2 is to be installed
       Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
       Depends: libgnet2.0-0 (>= 2.0.4) but it is not going to be installed
       Depends: libgtk2.0-0 (>= 2.6.0) but 2.4.10-1ubuntu1 is to be installed
       Depends: libpango1.0-0 (>= 1.8.0) but 1.6.0b-0ubuntu1 is to be installed
       Depends: libpcre3 (>= 4.5) but it is not going to be installed
       Depends: libxml2 (>= 2.6.17) but 2.6.11-3ubuntu1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
granite@granite:~ $



What should I do to get PAN working on my computer? I'm only a newbie so I'm not sure what's wrong here...

PAN is already in my Applications menu but nothing happens if I click it.

---

### Post by granite230 on 2005-01-25
ah! already fixed it!
here's the answer my friend gave me:

granite@granite:~ $ sudo apt-get remove pan
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  pan
0 upgraded, 0 newly installed, 1 to remove and 36 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3748kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 61586 files and directories currently installed.)
Removing pan ...
granite@granite:~ $

and then:

granite@granite:~ $ sudo apt-get install pan
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  libgnet2.0-0 libpcre3
The following NEW packages will be installed:
  libgnet2.0-0 libpcre3 pan
0 upgraded, 3 newly installed, 0 to remove and 36 not upgraded.
Need to get 1290kB/1397kB of archives.
After unpacking 4297kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main libgnet2.0-0 2.0.4-1 [98.9kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe pan 0.14.2.91-1 [1192kB]
Fetched 1290kB in 5s (225kB/s)

Preconfiguring packages ...
Selecting previously deselected package libpcre3.
(Reading database ... 61535 files and directories currently installed.)
Unpacking libpcre3 (from .../libpcre3_4.5-1.1_i386.deb) ...
Selecting previously deselected package libgnet2.0-0.
Unpacking libgnet2.0-0 (from .../libgnet2.0-0_2.0.4-1_i386.deb) ...
Selecting previously deselected package pan.
Unpacking pan (from .../pan_0.14.2.91-1_i386.deb) ...
Setting up libpcre3 (4.5-1.1) ...

Setting up libgnet2.0-0 (2.0.4-1) ...

Setting up pan (0.14.2.91-1) ...

granite@granite:~ $

I'm not exactly sure what it does, but my friend gave me the advice and it seems to work.

---

### Post by slazh on 2005-01-25
Lemme explain just quick what happend ;) (yes i'm the friend guy :P)

Because apt couldn' t find the package, we tried to install the package (pan deb file)
manually with

**sudo dpkg -i pan_0.14.2.91-2_i386.deb**

This did install the package, but not the dependancies.
That's why PAN wouldn't run if he clicked on it in the menu.

So we removed the package

**sudo apt-get remove pan**

Then we started all over again:

**sudo gedit /etc/apt/sources.list**

Added the follow lines to the end of the file..

[I]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe[/I]

After this, File > Save! Then 2 more steps...
[B]
sudo apt-get update
sudo apt-get install pan[/B]

That's it. 
But it didn't show up in the menu, 
so he restarted Gnome (CTRL- ALT - BACKSPACE), and now it's all good :)

---

