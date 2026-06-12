---
title: "Absolutely needed features - GUI'zing Alien"
date: 2006-04-02
forum: Desktop Environments
---

### Post by envykris on 2006-04-02
Hi..
I dint know where to post this..but still.

If Ubuntu needs to be seen as perfect replacement for Windows.  It need to do this without an excuse.  The key capability that makes users happy in Windows is how easy it is to self-install an app package.

So..basic objective:

1.  User shd never need to fire up terminal and run dpkg or alien
Answer: GUI'ize Alien, user should be able to right-click on a .deb or .rpm he download from any site, and it should show "instal" as an option, which then fires up Synaptic for him.

2.  Extended feature for the above - Ability to configure your HDD as one of the repositories in Synaptic and be able to list all the deb and rpm you downloaded yourself.  And go ahead perform all the Synaptic actions such as "mark for install" "unmark" etc on the local packages.

Currently, i dont think Breezy offers both the above, which is forcing users to CLI.  That will not fly if its the same with Dapper.

I say all this becos i used Xandros for a year....it had all these long before.  

This is the key win for attracting windows users.

- Krishna

---

### Post by OffHand on 2006-04-02
I agree 1 would be a really great option to have. It will def make like easier for novice users. There is already an aplication called checkinstall which will add the app you installed to the synaptic (so you can easily uninstall apps).

```
sudo apt-get install checkinstall
```

---

### Post by siminone on 2006-04-02
> 
Quote by envykris

Answer: GUI'ize Alien, user should be able to right-click on a .deb or .rpm he download from any site, and it should show "instal" as an option, which then fires up Synaptic for him


A GUI can be made if somebody has the time. Tk is the easiest to learn and to get up running but it isn't the prettiest.

---

### Post by slider2800 on 2006-04-02
Thats definietly worth some effort.
If i had time and a computer for my own, i would try to do something about it.

an Install option for the GUI is a great idea.

---

### Post by siminone on 2006-04-02
when I think about this, it wouldn't work.

The problem is that if the RPM's or deb's had dependencies, they sometimes conflict with Ubuntu and Synaptic gets broken. 

As Ubuntu has over 3000 converted deb's, this covers almost all of a beginners needs so this will not be a problem hence the reason why there is no GUI for alien.

---

