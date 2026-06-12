---
title: "Cannot login to LXDE"
date: 2015-09-26
forum: Desktop Environments
---

### Post by SepLite on 2015-09-26
I ran some software updates and noticed that some of the repositories were obsolete and were returning a 404 error when running apt-get update and apt-get upgrade, so I removed them. However, when I tried to login to LXDE today after the update, my screen turned black for a short while, and then I was returned to the login screen again. I can still login to the unity desktop fine. Since I have never dealt with this issue, I am not too sure what else I need to describe or include in this post, so please tell me if you need any logs, screenshots(albeit not exactly too feasible), etc. 

Also, even though my system is set to check for updates every day, I stopped receiving update notifications 5-6 months ago.

Thanks!
SepLite

UPDATE: I seem to be able to login to the lubuntu netbook desktop that installed with LXDE, however, it opens with an error dialog(see screenshot attached).
[ATTACH=CONFIG]264674[/ATTACH]

---

### Post by Rex Bouwense on 2015-09-26
What version are you running and what did you remove (By remove I assume you meant un-install)?

---

### Post by vasa1 on 2015-09-26
> **SepLite said:**
> ... when I tried to login to LXDE 

... the lubuntu netbook desktop that installed with LXDE ...
It's less confusing if you specify exactly what you log in to. AFAIK, there's no LXDE option available at login time if Lubuntu has been installed. There are some Lubuntu options and an Openbox option (on 14.04).

What exactly did you install? Was is "lxde" or "lubuntu-desktop" and when did you do the installation? Which version?

Could you please post the contents of **/usr/share/xsessions** within code tags?

The output of **dpkg --get-selections** could be uploaded via **pastebinit**.

---

### Post by uninvolved on 2015-09-27
Ha! I had this problem just the other day - I make it a point to break something often and to break it well. It's how I learn. Anyhow, the process is not too complicated to fix it - at least it wasn't in my situation and you are doing much the same.

Found: [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

Now, the key thing to remember is that you don't do it from the live disk nor do you do it from the guest account (if you have that enabled). Instead,  you pound the F2 key until you get to the login terminal and it works from there. At least, again, that's what I did and it worked for me.

Best of luck and let us know if it worked. Remember, if you're not breaking something then you're not trying hard enough.

Edit: I should mention - you pound the F2 key at the login screen. I had to attempt to login a couple of times before it worked. So, in other words, try to login a couple of times (it won't let you) and then pound the F2 until you get to the terminal. Then proceed with the directions on that page - the person who discovered that is brilliant. Basically, I was locked out of my own Xauthority file as I recall. It didn't need all the commands so I typed them in anyhow to see if it broke something else. It didn't. It worked like a champ.

---

### Post by SepLite on 2015-10-01
Sorry for my late reply.

> [COLOR=#000000]What version are you running and what did you remove (By remove I assume you meant un-install)?[/COLOR]

I am running Ubuntu 14.04, however I am not sure which one's I removed other than that they were obsolete and returned 404 errors when running apt-get update. 

> [COLOR=#000000]What exactly did you install? Was is "lxde" or "lubuntu-desktop" and when did you do the installation? Which version?[/COLOR]

I installed lubuntu-desktop around half a year ago, and I am not sure how to view the version of lubuntu-desktop. I thought these were same/similar things, but I still seem to still have a lot to learn.

Contents of /usr/share/xsessions

```
Lubuntu.desktop  Lubuntu-Netbook.desktop  openbox.desktop  ubuntu.desktop

```

and dkpg --get-selections output here: [http://paste.ubuntu.com/12635938/](http://paste.ubuntu.com/12635938/)


Also every time I log in to lubuntu netbook(somehow still works) there is a system error that "Xorg crashed with SIGSEV in pci_device_vgaarb_set_target()"

Thanks and sorry for my really late reply
SepLite

---

