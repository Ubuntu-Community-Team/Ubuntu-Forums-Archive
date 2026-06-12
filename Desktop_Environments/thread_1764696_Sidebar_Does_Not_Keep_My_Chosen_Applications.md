---
title: "Sidebar Does Not Keep My Chosen Applications"
date: 2011-05-22
forum: Desktop Environments
---

### Post by moforilla on 2011-05-22
Hi,

I recently upgraded to 11.04 and the sidebar seems to not be functioning as one would expect. 

I removed unwanted applications that come by default and added my own applications by clicking "Keep In Launcher".

After a reboot the sidebar returns to default applications. I did a quick Google search but wasn't able to find anyone else reporting the problem.

Has anyone heard of this happening to anyone else and can you think of anyway to fix it?

Thanks.

---

### Post by Copper Bezel on 2011-05-22
I haven't heard of this problem before - are you running Unity 3D or 2D? (If it's 2D, you can see the process for the Unity 2D panel in your System Monitor.)

---

### Post by moforilla on 2011-05-23
It seems 2D to me but I'm not sure. It is whatever comes as standard with a 11.04 upgrade.

The following process are listed in my system monitor.

unity-applications-daemon
unity-files-daemon
unity-panel-service
unity-window-decorator

Maybe doing a reinstall of unity could fix it? I will give it a try.

---

### Post by Copper Bezel on 2011-05-23
Nope, you're using 3D - see [here]("http://manpages.ubuntu.com/manpages/natty/man1/unity-panel-service.1.html").

A fresh install would doubtless fix it, yes. However, I'm really curious why the Unity Launcher isn't saving its settings to gconf as it ought to. I'm not running Natty, so I'll have to defer to someone with firsthand experience.

---

### Post by moforilla on 2011-05-23
I tried reinstalling unity and it doesn't seem to have fixed it.

What I did was open synaptic and marked unity for reinstall.

Should I reinstall any other packages? A part from doing a full system reinstall can anyone think of anything else to try?

---

### Post by mc4man on 2011-05-23
Maybe try deleting some files in home folder

Open home > (view show hidden files) and delete in this order, whole folder unless blue
.compiz
.gconf/apps/[COLOR="Blue"]compiz-1[/COLOR]
.gconf/apps/[COLOR="Blue"]compizconfig-1[/COLOR]
.gconfd
.cache/[COLOR="Blue"]dconf[/COLOR]
.config/[COLOR="Blue"]dconf[/COLOR]
Then log out/in, try removing some launcher icons, log out/in and see if it sticks

---

### Post by moforilla on 2011-05-25
I tried deleting those folders and still the sidebar returns to default.


I wasn't able to find these:

.cache/dconf
.config/dconf

I will try what you said again tomorrow and look at all this in a bit more detail.

---

### Post by Krytarik on 2011-05-25
Make sure that everything in your home directory is owned by you:
```
sudo chown USERNAME:USERNAME -R /home/USERNAME
```
You may get an error message about the directory ".gvfs", that's ok.

Greetings.

---

### Post by GonZo on 2011-05-27
I had the same problem.

Verify you have installed libdconf0
```
sudo apt-get install libdconf0
```
It seems upgrade doesn't install all the necessary libs
[https://bugs.launchpad.net/unity/+bug/778321?comments=all]("https://bugs.launchpad.net/unity/+bug/778321?comments=all")

---

### Post by moforilla on 2011-05-29
Thank you all for your suggestions.

GonZo, you are right. libdconf0 was not installed and after installing it that problem was fixed.

For future reference for anyone with this problem.

***SOLUTION***
```
sudo apt-get install libdconf0
```
***SOLUTION***


P.S. Why has ethanolgasoline posted the same thing as the first post by Copper Bezel?

---

