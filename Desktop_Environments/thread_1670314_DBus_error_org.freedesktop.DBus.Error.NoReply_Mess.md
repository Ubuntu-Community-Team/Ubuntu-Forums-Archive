---
title: "DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply"
date: 2011-01-18
forum: Desktop Environments
---

### Post by btraill on 2011-01-18
When trying to connect my iPhone via USB I get the error:

Unable to Mount Brads iPhone:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I searched on google and came to a Mandriva thread and the solution was because the user had 4G of RAM the install attempted to run/use the server repositories/files instead of the desktops. Could this be a possibility with Linux?

---

### Post by btraill on 2011-01-19
Anyone?

---

### Post by John L on 2011-01-20
I have the same problem - all was ok until this week.  Is it an update issue?

John

---

### Post by John L on 2011-01-20
I have the same problem - all was ok until this week.  Is it an update issue?

John

---

### Post by killfall on 2011-01-20
I'm having the same issue. Any help would be appreciated!!

---

### Post by manjaca on 2011-01-24
My daughter updated her iPhone 3G the other day and it won't mount any longer?! 

Worked fine before the update...

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

### Post by Johnkozz on 2011-01-24
Hm at first I though it was because I did a jailbreak on my phone...But now seeing that others are having the same issue I know it can't be that.

---

### Post by animaex on 2011-02-11
[FONT="Verdana"]I found this site [**here**]("http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/") and it sugested the following terminal commands: 

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

It worked for me.
[/FONT]

---

### Post by killfall on 2011-02-12
> **animaex said:**
> [FONT="Verdana"]I found this site [**here**]("http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/") and it sugested the following terminal commands: 

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

It worked for me.
[/FONT]

I didn't need the ```
sudo add-apt-repository ppa:pmcenery/ppa
``` Update and dist-upgrade was enough to get it working for me.

---

### Post by harecanada on 2011-04-02
This worked for me too. I still can't seem to sync iTunes to my iPhone 4 though.
harecanada

---

### Post by mpcsm on 2011-04-25
Thanks animaex this solution worked for me.:P

---

### Post by eltonw on 2011-06-01
> **animaex said:**
> [FONT="Verdana"]I found this site [**here**]("http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/") and it sugested the following terminal commands: 

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

It worked for me.
[/FONT]

I found the above solution after I posted here: [http://ubuntuforums.org/editpost.php?do=updatepost&postid=10883281]("http://ubuntuforums.org/editpost.php?do=updatepost&postid=10883281")

Followed the above instructions_ to the letter_. Did a warm boot, and also a cold boot. 
[FONT="Verdana"][COLOR="DarkRed"]Iphone *still* WON'T mount.[/COLOR][/FONT] ](*,)
Hardware: iPhone 3GS, IOS 4.3.2
all current and available updates applied today [01 JUNE 2011]

When connected, the popup says:
 "Unable to mount IPhone
DBus error org.freedesktop.DBus.Error.NoReply:
Message did not receive a reply (timeout by message bus)."

[FONT="Verdana"]This is on an Asus EEE 1000 PC running Natty Narwahl / ubuntu 11.04.[/FONT]

---

### Post by xdragonforce on 2011-06-04
Apple, The losers they are, decided it would be a great idea to make sure you are always using itunes. They only way to hook up your iphone with your computer is to jailbreak it. using windows or mac.

---

### Post by eltonw on 2011-06-05
> **xdragonforce said:**
> Apple, The losers they are, decided it would be a great idea to make sure you are always using itunes. They only way to hook up your iphone with your computer is to jailbreak it. using windows or mac.

A better ***SOLUTION*** would be to provide feedback to the developer of **pmcenery** (the utility that enabled mounting the iPhone in ubuntu.

**pmcenery:** [https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=karmic]("https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=karmic")

---

### Post by mythsmith on 2011-08-04
The same for me. I upgraded to 11.04 and nautilus was blocked, and ubuntuOne didn't work. Plus I had problems with an usb camera.
After adding ppa:pmcenery/ppa and upgrading, all problems were gone.
It seems a quite serious bug!

---

### Post by Ludd1te on 2011-08-05
> **animaex said:**
> [FONT=Verdana]I found this site [**here**]("http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/") and it sugested the following terminal commands: 

```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```It worked for me.
[/FONT]

That didn't work for me, but following the commands on [this]("http://ubuntuforums.org/showthread.php?t=1756890") site did.

[For what it's worth, my exact error in U1 was:
File Sync error. (org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus))]

---

### Post by Ludd1te on 2011-09-16
Update:
Yeah, using [these steps]("http://ubuntuforums.org/showthread.php?t=1756890") to clean out the U1 directory worked for me . . . for a while.  The issue came back.  Following those same steps I just linked to worked again, but still had to go through them.

I've been having [this]("http://ubuntuforums.org/showthread.php?p=11152753#post11152753") issue, too.  Now, I chose "luddite" as my username for a very good reason, but I think they might be related.

---

### Post by ivotkl on 2012-12-30
Reviving an old post here. I tried adding Paul's PPA, but apparently he removed it as I get a 404 error when updating.
I wouldn't know how [this](http://ubuntuforums.org/showpost.php?p=10831433&postcount=3) would help me solve the situation.

BTW, my iPad appeared listed on lsusb the second I connected it, but it didn't next (I believe it happens right after the 'Not Charging' message appears). Since USB port works, as I also use it under Windows (which I hate =P), It is not a PC hardware issue.

Any ideas?

---

### Post by oldos2er on 2012-12-30
Please start a new thread, this one's quite old.

---

