---
title: "mplayer-386 and notification speech bubbles"
date: 2005-11-22
forum: Desktop Environments
---

### Post by stalefries on 2005-11-22
I have two problems, both of which I hope can be easily fixed. 

The first is an apt-get issue: after doing a successful dist-upgrade, I had several packages which would not get updated; apt-get specifically stated this. The number has slowly dwindled down to one: mplayer-386. Can someone tell me what I've done wrong? When I edited my /etc/apt/sources.list with gedit, I just told it to do a find-and-replace of "hoary" to "breezy". Here's the output of " cat /etc/apt/sources.list"

```
 deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` 

My second problem is those notification bubbles that the Update Manager pops up whenever I have packages that can be updated. Not only do they bug me, they won't go away if I click "Tell Me Later" nor if I click "Show Updates". I can right-click the tray icon and click show updates, and update that way, and I can also do an "apt-get upgrade" to upgrade packages, but those annoying messages won't go away! They also are always on top, so I'm limited to a smaller screen area.

---

### Post by stalefries on 2005-11-26
/bump

Does anyone have any ideas? Maybe just a suggestion on what I should research?

---

### Post by stalefries on 2005-12-08
Never mind. I fixed this by installing mplayer-586, which removed mplayer-386. And the bubbles were removed after I told it to stop, and then rebooted. I'm not sure if I needed to reboot, but I didn't notice it until after I rebooted.

---

