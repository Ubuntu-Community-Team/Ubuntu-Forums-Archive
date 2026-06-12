---
title: "ubuntu white terminal no gui"
date: 2010-06-23
forum: Desktop Environments
---

### Post by koryusai on 2010-06-23
my brother was on my pc typed 'sudo apt-get remove nautilus' and he reinstalled it now when i login all i get is a white terminal and no gui anyone know how to change it back to normal without re-installing ubuntu:

[IMG]http://i49.tinypic.com/x4kv7p.jpg[/IMG]

im running 10.04 LTS

Thanks in advanced koryusai kun

---

### Post by Deadite81 on 2010-06-23
That was a silly thing to do!
Nobody else seemed to have replied, perhaps this command will work (it won't hurt anyway):
```
sudo service gdm start
```

---

### Post by koryusai on 2010-06-23
when i enter that command it comes up with:

```
start: Job is already running: gdm
```

---

### Post by Deadite81 on 2010-06-23
I thought that might be the case.  It's strange that you get a login background and no login window.  Are you certain Nautilus was reinstalled?  You could always try:
```
sudo apt-get install nautilus
```And you could try starting Nautilus if it's not starting for some reason:
```
nautilus
```
That's all I can think of right now, but I'm certainly no expert.

---

### Post by snowpine on 2010-06-23
Try:

```
sudo apt-get install ubuntu-desktop
```

This should reinstall any parts of the default Ubuntu desktop that your brother may have accidentally removed. :)

---

### Post by koryusai on 2010-06-23
deadite81, when i try your post i get:
[img]http://i50.tinypic.com/2dj3195.jpg[/img]

snowpine, when i try your post i get:
[img]http://i45.tinypic.com/24e1jd2.jpg[/img]

---

### Post by Deadite81 on 2010-06-23
Snowpine's answer was correct, it appears that getting those packages will ifx your problem.  It appears you're not connected to the internet however...I don't know how to do that from the command line.  However, those packages are likely still in your cache (/var/apt/cache).  You could install them from there.

---

### Post by Deadite81 on 2010-06-23
I think the command would be
```
cd /var/cache/apt/archives
```then
```
ls
```Find the exact name of the "gnome-session" package, then
```
sudo dpkg -i NAMEOFPACKAGE
```Then you'll probably have to restart.

---

### Post by Deadite81 on 2010-06-23
Sorry wrong directory! 
it's** /var/cache/apt/archives**

---

### Post by koryusai on 2010-06-23
Thanks for your reply im just reinstalling the .deb pack's now will get back to you if it works

---

### Post by Deadite81 on 2010-06-23
I've checked, and the package in my cache is:
```
gnome-session_2.30.0-0ubuntu1_all.deb
```this should work:
```
sudo dpkg -i /var/cache/apt/archives/gnome-session*.deb
```Sorry about the confusion, doing too many things at once.

---

### Post by JK3mp on 2010-06-23
Wow what a not so funny joke, for future reference connecting to THE WORLD(aka Internet) from cmd line is ```
ifup eth0
``` i believe.(for eth0 NIC)

---

### Post by Deadite81 on 2010-06-23
> **JK3mp said:**
> Wow what a not so funny joke, for future reference connecting to THE WORLD(aka Internet) from cmd line is ```
ifup eth0
``` i believe.(for eth0 NIC)

Ha!  Never needed to do it, so never bothered to see how simple it is!  Learn something new every day...:)

---

### Post by koryusai on 2010-06-23
that didnt work deadite and JK3mp that didn't work eather is there anyway of installing the ubuntu-desktop update from the live cd?

---

### Post by Deadite81 on 2010-06-23
Did the gnome-session package not install at all?  After looking up what that package actually does, it is unclear to me if it is even necessary to logging in.  If you haven't deleted any of your apt cache, this command should install ubuntu-desktop:
```
sudo dpkg -i /var/cache/apt/archives/ubuntu-desktop*.deb
```As for installing from a live cd, I don't know if that's possible or not.  You can [download]("http://packages.ubuntu.com/") those three packages your missing onto a usb stick and install them that way.  

You should know that the "ubuntu-desktop" package is a "meta package", meaning that it doesn't contain anything, it only points to certain packages and makes sure they all stay installed and up to date.  The only packages you're actually missing (as far as from ubuntu-desktop) are gnome-session and nautilus-share.

If your setup to automatically connect to the internet, ```
ifup -a
```might work.  The command```
sudo lshw -C network
```will show you your available network devices, just to make sure your device is even being recognized.

A way to get around the login screen, which I've used before, is to login using a virtual terminal.  If you press ctrl+alt+F1 you should be taken to a virtual term that asks you for your username and password (assuming virtualization is enabled on your computer.  I had to enable mine in the bios).

Put that in and wait for it to log you in.  Now hit ctrl+alt+F7 to return to the X session.  This may get you past the login screen.

Are you sure that's all your brother did?

---

### Post by koryusai on 2010-06-23
im just going throught the steps how do i insall them from my usb stick?

---

### Post by koryusai on 2010-06-23
if i type:
```
gnome-session
```

it shows up the normal desktop but when i close the terminal window it vannishes

---

### Post by Deadite81 on 2010-06-23
Type ```
gnome-session &
```
This will start gnome-session as a background prossess.  Then hit ctrl+C to get your terminal prompt back.

Can you interact with your desktop normally after that?

---

### Post by koryusai on 2010-06-23
yes all i had to do is type gnome-session then reboot then activate my gfx card:

gnome-session
wait a bit
open new ternimal 
sudo apt-get -f install
sudo apt-get install ubuntu-desktop
sudo reboot
sudo nvidia-xconfig
sudo reboot

---

