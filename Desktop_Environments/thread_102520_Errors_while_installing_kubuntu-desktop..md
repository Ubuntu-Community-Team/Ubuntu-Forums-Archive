---
title: "Errors while installing kubuntu-desktop."
date: 2005-12-12
forum: Desktop Environments
---

### Post by subscrive on 2005-12-12
Hi All,

- I installed 5.04 in server mode.
- Then I changed the sources.list to point to breezy.
- Then I installed kubuntu-desktop.
- I have burnt the .deb files to some cd.

Due to some reason I had to wipe the ubuntu.

Now I want to reinstall kubuntu. For this I tried the below things.
- Installed 5.04 in server mode.
- Went to the cdrom (I can see all the debs).
- Did a "sudo dpkg -i *.deb".

The system tries to install kubuntu desktop. But then after 5 mins or so, I get an error message saying something like - there were lots of errors. Operation aborted.

Can anyone help me in this?

~A.

---

### Post by Zaventh on 2005-12-12
Why not just download the Kubuntu Breezy 5.10 install CD?...

---

### Post by Sokraates on 2005-12-12
AFAIK server mode installs only what's necessary; so no X etc.

The errors you saw were probably due to missing dependencies. You can either post the error message or simply reinstall Hoary in "normal" (don't know the correct name) mode and then upgrade to Breezy.

For infos on upgrading look [here](http://ubuntuforums.org/showthread.php?t=74990).

---

### Post by subscrive on 2005-12-12
> - I installed 5.04 in server mode.
- Then I changed the sources.list to point to breezy.
- Then I installed kubuntu-desktop.
- I have burnt the .deb files to some cd.

What I did the 1st time was the above steps. So I have the all the debs for kubuntu desktop.

On my other computer I tried the same with ubuntu (gnome).
When I erased the gnome ubuntu (from my 2nd comp) and then tried the below steps, I was able to install gnome desktop, and the ubuntu has become 5.10. uname -a shows 5.10.
"- Installed 5.04 in server mode.
- Went to the cdrom (I can see all the debs).
- Did a "sudo dpkg -i *.deb"."


I would request all you friends to [COLOR="RoyalBlue"]NOT[/COLOR] give me advice like "try kubuntu 5.10, rather than these steps."

---

### Post by subscrive on 2005-12-12
Q: Why am I upgrading using this method?

A: I received the 10 cd set of 5.04 from the company. I have done many installs on my friends' computers. Few of them want KDE and not gnome. Also they want to upgrade to 5.10.
Unfortunately, not everyone has a broadband connection.
Also for past 6 months or so they have created the data.
Doing a regular kubuntu 5.10 install will surely delete the data.

sudo dpkg -i *.deb is the only way to 
1. upgrade their system from 5.04 to 5.10.
2. Give them kde - which they like and are more comfortable with.
(it worked once on one of my friends computer, but now its not working on my computer itself!)

---

### Post by aysiu on 2005-12-12
I think what you're looking for is this:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

