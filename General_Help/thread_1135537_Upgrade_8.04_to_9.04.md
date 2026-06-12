---
title: "Upgrade 8.04 to 9.04"
date: 2009-04-24
forum: General Help
---

### Post by ade234uk on 2009-04-24
I had real issues burning .iso for 9.04
I have wasted 5 cd's and none of them work regardless of how slow I burn.

I found a copy of 8.04 and I now a new system.
I would like to upgrade to version 9.04, how do I go about this.

---

### Post by jamessnell on 2009-04-24
In the Synaptic Package Manager, under Settings > Preferences > Distribution (or something similar) there should be a setting that's currently set to LTS (Long Term Support) as 8.04 is meant to be supported for quite some time.. If you change the setting in there to whatever it's called, perhaps something like "Always prefer the highest version", then go run the Update Manager, I bet you'll be presented with an option to Upgrade your Distro.

Please let me know if that does it for you..

Also, sounds like you should get a new burner ;)

---

### Post by sgtbug on 2009-04-24
always hash check thru the torrent before burning.. ;-) u can never go wrong..

---

### Post by ade234uk on 2009-04-24
What I am currently doing is upgrading from 8.04 to 8.10
Then I will upgrade from 8.10 to 9.04, crazy I know but I am so sick to death of wasting CD's lol.

---

### Post by sgtbug on 2009-04-24
if you have direct downloaded the iso from a mirror, hash check the iso with a torrent client.. i am pretty sure that is the problem.. that always happens to me when i direct download the image.. i must have wasted 10 cds before figuring it out.. LOL

wont hurt to try it.. if there is no corruption in it and it shows that the file is complete then do it the apt way.. otherwise just try for the last time on an RW..

---

### Post by snowpine on 2009-04-24
> **ade234uk said:**
> I had real issues burning .iso for 9.04
I have wasted 5 cd's and none of them work regardless of how slow I burn.

I found a copy of 8.04 and I now a new system.
I would like to upgrade to version 9.04, how do I go about this.

Easiest method (in my opinion), from the terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Reboot into 8.10. Repeat the steps above to upgrade from 8.10 to 9.04.

HOWEVER, if the 9.04 live CD did not work on your computer, that is a warning sign. If there is any kind of incompatibility or bug that prevents 9.04 from working on your computer properly, upgrading from 8.04 will not necessarily solve the problem. Can you go into more detail than "it didn't work"?

---

### Post by jamessnell on 2009-04-24
@coolaks: That's insane, I've downloaded the CD image nearly every time (at least 10 downloads over a few years now). I've never had that issue. I wonder wtf is going on there. Weird.

---

### Post by ssdt on 2009-04-24
You can also check out Administrator>> Software Sources and check if you have upgrade for normal releases enabled.

---

### Post by ade234uk on 2009-04-24
1) I was getting a read error at the main menu when the CD booted.

2) Another kept halting at a busybox

3) Another CD got to me the live CD desktop and menus the login box was garbled

4) Another CD Got me to 60% of the install and through an error and rebooted 

These are just some of the issues I have had.

---

### Post by ade234uk on 2009-04-24
Darn it, the upgrade from 8.04 to 8.10 canned by system lol. Damn Kernal Panic. What I am going to do is stick with 8.04 and order 9.04 from Ubuntu. I know this will probably work or if anyone has a torrent that works I can give this a go.

---

### Post by sgtbug on 2009-04-24
this worked for me.. just verify it with this.. and if there are some parts missing just let it finish them.. there are 2 files in the archive.. one for i386 and another for amd64.

@jamessnell
dude.. it happens many times.. when u move the iso too much in a usb drives etc.. sometimes even the download managers screw it up..

---

### Post by jamessnell on 2009-04-24
> **coolaks said:**
> this worked for me.. just verify it with this.. and if there are some parts missing just let it finish them.. there are 2 files in the archive.. one for i386 and another for amd64.

@jamessnell
dude.. it happens many times.. when u move the iso too much in a usb drives etc.. sometimes even the download managers screw it up..

lol, fire your isp -> ;) jk

---

### Post by Ikbear on 2009-08-09
[SIZE=3][FONT=Times New Roman]Hey, you can try this method:

1. sudo apt-get install [COLOR=#000000][FONT=-webkit-monospace]Update-maager-core
[/FONT][/COLOR][/FONT][/SIZE][SIZE=3][FONT=Times New Roman]2. sudo gedit /etc/update-manager/release-upgrades[/FONT]
[/SIZE][FONT=Times New Roman][SIZE=3]    change "Prompt=lts" to " Prompt=normal[/SIZE][/FONT][SIZE=3]"
3. sudo do-release-upgrade

That's it!
[/SIZE]

---

### Post by Sylslay on 2009-08-09
Easy way ever!!!

1 step: press alt+F2,
2 step: write command: update-manager -c 
Welkome in next version of ubuntnu

or
2 step : write command update-manager -d 
Welkome in "DEVELOPMENT" version of ubuntu

BTW: Check 
man update-manager

---

### Post by zkriesse on 2009-08-09
I once had a problem like this...if you get a stable version of Ubuntu on your pc...then download the latest vers of your choice...it seems to work if you download Ubuntu ON Ubuntu...don't know why but that's how it is....crazy but it works

---

### Post by chrowe on 2009-10-18
I guess you have to go from 8.04 > 8.10 and then 8.10 > 9.04

The instructions in these links worked for me.
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)
[https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

---

### Post by poohpeer on 2009-11-03
I'm trying to upgrade my 8.04 to 9.04. I have ran the following, 

> sudo apt-get update
sudo apt-get dist-upgrade

but  it says that my system is up to day

> notroot@sofa:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What is wrong? May be I need to add any new repositories?

---

### Post by snowpine on 2009-11-03
> **poohpeer said:**
> I'm trying to upgrade my 8.04 to 9.04. I have ran the following, 



but  it says that my system is up to day



What is wrong? May be I need to add any new repositories?

Try 'do-release-upgrade' instead of 'dist-upgrade'.

'dist-upgrade' is for upgrading within a release. 'do-release-upgrade' is for upgrading to the next release.

---

### Post by poohpeer on 2009-11-03
> **snowpine said:**
> Try 'do-release-upgrade' instead of 'dist-upgrade'.

'dist-upgrade' is for upgrading within a release. 'do-release-upgrade' is for upgrading to the next release.

also this one do not think I need to upgrade.

---

