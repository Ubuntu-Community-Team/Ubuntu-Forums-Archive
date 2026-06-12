---
title: "No &quot;instal widget&quot; option in Plasma widget manager"
date: 2008-08-16
forum: Desktop Environments
---

### Post by zachthejones on 2008-08-16
when I right-click on the desktop and click on "Add widgets" get the little screen which manages your widgets (lets you add and remove them). BUT I don't have an "install widget" button, which I only recently learned I should have.

Any Idea what I should do/install to get this?

Note: I started with a clean Ubuntu Gutsy install, then installed kubunt-desktop, and finally installed kde4-core from this repo:

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

---

### Post by txcrackers on 2008-08-17
Check and make sure you have **all** of the "plasma"-related modules installed - and that they're version **4.1**. If you have the old 4.0 versions installed, remove them.

---

### Post by zachthejones on 2008-08-17
okay, quick question along that line...will I need to have KDE 4.1, or is 4.0 okay? I installed 4.0, but it never automatically upgraded to 4.1, so I'm assuming that's something I have to do manually.

---

### Post by txcrackers on 2008-08-17
Correct - you will need 4.1, and yes you will need to probably handle it manually. Some of the packages were renamed, thereby "breaking" the update path. The basic rule of thumb is if there's a package with version 3.8x, 3.9x, or 4.0, delete it or update to version 4.1

---

### Post by zachthejones on 2008-08-18
thanks! I actually found the problem in my repo - I had the address wrong and therefore the updates never came through. I got that fixed and think I've gotten everything ironed out. I now have access to the "install widgets" button and am definitely liking 4.1 a lot more than 4.0.

Thanks!

---

