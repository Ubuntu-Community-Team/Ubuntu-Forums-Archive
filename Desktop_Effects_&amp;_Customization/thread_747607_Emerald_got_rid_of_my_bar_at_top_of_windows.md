---
title: "Emerald got rid of my bar at top of windows"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by mikeric on 2008-04-06
I installed emerald, and started trying to get some themes and it got rid of the bar at the top of windows, for minimizing it and stuff. I dont know how to get it back, anyone have any ideas?

---

### Post by xpod on 2008-04-06
Try ALT-F2 or the terminal
```
emerald --replace
```

---

### Post by mikeric on 2008-04-06
i do that and they come back, but as soon as i close the terminal i lose them all again.

---

### Post by xpod on 2008-04-06
Do it with ALT-F2 instead:)

EDIT:
If you want them starting automatically when you boot up then navigate to Preferences>Sessions>Startup programs and ADD the same command in there

---

### Post by mikeric on 2008-04-06
Thanks for the help. i did it with alt-f2 and it worked

---

### Post by xpod on 2008-04-06
Good stuff....
Now just dont be spending toooo many hours playing with Compiz:mrgreen:

---

### Post by mikeric on 2008-04-06
I have probably been spending more than i should with my comp now. I actually have been using my girlfriends old dell desktop more than my laptop with WIndows XP on it. If i didnt need some programs for tuning my car my laptop would probably already be on its way to running ubuntu. My next challenge is to learn to set up so i can run both on the laptop, then ill just about be done with windows. Its great how much help and information is out there for new users.

---

### Post by xpod on 2008-04-07
> I have probably been spending more than i should with my comp now

Ubuntu & Co does have that effect on people it seems:)

> My next challenge is to learn to set up so i can run both on the laptop, then ill just about be done with windows. Its great how much help and information is out there for new users.

A Dualboots certainly the best way to go when first starting out,especially if you have programs you need in Windows.Just remember and backup anything important before you go playing around with important machines though........

Good luck either way

---

### Post by andahunter on 2008-04-07
> **xpod said:**
> Ubuntu & Co does have that effect on people it seems:)



A Dualboots certainly the best way to go when first starting out,especially if you have programs you need in Windows.Just remember and backup anything important before you go playing around with important machines though........

Good luck either way

If u want 2 dual-boot and dont want to mess something up here's everything that u need 2 know :D Gl and Hf with both of em
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)
Oh and if u have any other ubuntu, dont worry its the same procedure just a bit different looking startup

---

### Post by mikeric on 2008-04-07
Thanks for the help, ill backup the laptop,l already lost most important stuff on that when my harddrive failed. So i learned the hard way to back up stuff more often.

---

### Post by russo.mic on 2008-04-08
You know, Virtualbox is getting easier and easier.  I've got a virtual WinXP that runs fairly well!!!

---

### Post by mikeric on 2008-04-10
Does Virtual WinXP let you run windows programs in it?

---

### Post by russo.mic on 2008-04-11
it allows you to run the windows xp operating system in it, so yes.  Now, a few things don't work.  Don't expect to play half-life 2 in this thing.  Firewire still isn't supported.  but for general use, iTunes, office, (not that you HAVE to do those things in windows), it works great!  There are also a bunch of howtos on migrating your existing winXP partition into a virtual machine that make it fairly easy.

Check out this great article on just this:
[http://www.linuxjournal.com/article/9942](http://www.linuxjournal.com/article/9942)

Russo

---

### Post by Zorael on 2008-04-12
As a side note, if you ever want to run commands in a terminal and you don't want them to close whenever you close the terminal console itself, add an ampersand (&) to the end of the line.

```
$ gedit &
```
It will return a process ID (PID) which, if you have stellar numeric memory, you can use to terminate the process.
```
$ kill 2039
```
Provided the pid was 2039.
You can also kill it "by name", but this might become messy if you have several processes with the same name running. As in, several gedits up at once. They'll all close.
```
$ killall gedit
```

Goes well with pancakes!

---

