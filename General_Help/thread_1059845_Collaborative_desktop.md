---
title: "Collaborative desktop"
date: 2009-02-04
forum: General Help
---

### Post by uvaio on 2009-02-04
Hi everyone, this is more scifi question then a real problem.

So anyone willing to free up fantasy is welcome.

PC with attached lets say 3 sets of keyboards and mouses. Doable over USB.
What I'd like to is to have Desktop where lets say 3 people can work at the same time in front of same computer. Lets say you've got big big screen with great resolution so plenty of space on desktop and you want more people to work with it as the same time.
What would be needed is possibly something like to have numbered sets of kb and mouse as set1, set2 and set3. Then focus at multiple windows would be needed.
So if one person klicks by mouse on open window it gets focus but only for set1, so user1 can type and use mouse on that window. 
Meantime user2 klicks mouse on other window and he gets focus on it. So at this time there are two users typing to two different programs at the same on the same desktop. Lets call it Collaborative desktop.
What modifications would be need to achieve this on ubuntu ?

---

### Post by derki on 2009-02-04
Xserver is maintaing all the inputs, but you will need to make somethink like dual sessions, when all sessions will be enabled in one time, but i dont think it will be worth of time doin this :)

---

### Post by uvaio on 2009-02-04
I'm thinking about it more like to have one session. One user is logged in.
Lets say people working with the computer would be user PopcornGroup.
the fact that there are multiple controllers connected and multiple users are using them does not mean they are individuals. Exact opposite, they are ONE. So all stuff would remain as for single user. just to be able to assign keyboards output to particular windows. And because normally user does it using mouse to click on the window, mouses and keyboards should be paired somehow to determine which keyboard output to link with window when you click on it by mouse.

---

### Post by mister_pink on 2009-02-04
[MPX]("http://http://en.wikipedia.org/wiki/MPX") is halfway there...

---

### Post by uvaio on 2009-02-04
wow, great ;o) saw few videos on youtube. Seems like exactly what I was looking for. Thanks mister_pink.

---

### Post by motin on 2009-02-28
The official bug report for integration of MPX: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220036](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220036)

---

