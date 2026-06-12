---
title: "ntp.ubuntulinux.com"
date: 2006-01-13
forum: General Help
---

### Post by KhanArash on 2006-01-13
When I turn on my computer and I want to log on linux there comes a list with ok or faild...(loading list)

I see "ntp.ubuntulinux.com" is faild...how can I dix it?

---

### Post by BitTorrentBuddha on 2006-01-13
that's for updating the clock, you need to have an internet connection for that to work

---

### Post by KhanArash on 2006-01-13
I have an internet connection,I am using linux now...
but this faild will not go away in the loading page!

---

### Post by dcstar on 2006-01-13
[QUOTE=KhanArash]I have an internet connection,I am using linux now...
but this failed will not go away in the loading page![/QUOTE]
If you can ping that address now, then it is possible that it is running the time sync command too quickly at start up (your machine doesn't have full network functionality at that time).

If you can't ping it now, then the site is unavailable from your system for some reason.

Either way, if you want to get rid of the function at boot up, edit /etc/default/ntpdate and comment out the line with that time server.

---

### Post by professor_chaos on 2006-01-13
for the last week or so, mine has been failing as well. I thought it was the ubuntulinux.com server. 
No big deal for me, I don't care about keeping time in sync, because I usually live by my own time anyway.

---

### Post by Mr_Grieves on 2006-01-13
You could just change to sync against some other NTP server.
Do a google search on 'public NTP' and choose one close to you.

I'm atm not on Ubuntu.. but perhaps you can do this via:
System -> Administration -> Time and Date

---

### Post by BoneKracker on 2006-01-14
Three things:

1:  I'm not an expert (I have 1 week of Linux experience), but here are three possible ways I've found to fix this:

a) Switch to using fixed IP (ntpdate is probably timing out because your network interface is not yet active because it's waiting for DHCP).  That's what I did, and it's working now.
b) Edit the file /etc/defaults/ntpdate and comment-out everything (I didn't try this because (a) worked, but apparently this makes ntpdate just skip on through).
c) Disable the ntpdate boot-up script (NOT recommended).

2:  It's probably also helpful to optimize your ntpdate configuration:

a) Edit the file /etc/defaults/ntpdate and replace the ubuntu ntp server address with two or three carefully selected ones (tier 2 public servers at reliable institutions that are geographically close to you).  Either that or set it to poll the ntp pool (the address is already in the file, commented out).
b) Alternatively, just delete the file (/etc/defaults/ntpdate) and the boot process defaults to using the ntp pool anyway.  That's what I did.  Since I've set up ntpd (not ntpdate) to synch periodically during normal up-time with a specific set of servers, polling a random selection of servers during boot-up has some value.

3: Also, you should be aware that you can probably just ignore the ntpdate failure (unless you are obsessive-compulsive, anally-retentive, or running either an ntp server of your own or a system that needs continuously precise time for logging or other needs).  ntpdate is becoming obsolete soon anyway, and you do have the option to use ntpd (right-click the clock, press "adjust", etc.).  Or, you could also write a post-boot-up pre-login script to run ntpdate after enough time has passed for your dhcp connection to come up.

---

### Post by dcstar on 2006-01-14
[QUOTE=BoneKracker]Three things:

1:  I'm not an expert (I have 1 week of Linux experience), but here are three possible ways I've found to fix this:
......[/QUOTE]
You can also install the ntp-server package and have your system configured to regularly go to time server(s) to keep itself in sync during normal operation.

Simple to do, and then you don't have to worry about anything apart from the tiny network traffic every time it queries a time server.

---

### Post by BoneKracker on 2006-01-15
Exactly.  As I said, "...and you do have the option to use ntpd...".

---

