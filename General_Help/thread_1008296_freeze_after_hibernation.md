---
title: "freeze after hibernation"
date: 2008-12-11
forum: General Help
---

### Post by BaristaBoreal on 2008-12-11
OK, I've searched the forums for a few weeks now and have found no thread that could help me. I can't get hibernate to work under Xubuntu Hardy; after selecting hibernate from the exit menu, I get a few error messages along the lines of "power sequence failed" (sorry for the vague description), and then my computer powers off. When I reboot, I'm stuck on the Xubuntu flash screen, until I manually reboot once more, and then I can log in just fine. 
I know I've got enough space in my swap partition (2 GB for 768 MB RAM), and I used to be able to hibernate just fine under Ubuntu Dapper. Any ideas? Thanks a million.

---

### Post by iponeverything on 2008-12-11
just as a test -- try shutting down your wireless and removing the wireless module before hibernation. 


from the command line to see the name of your interface:

```
sudo iwconfig 
```

lets just say its wlan0:

```
sudo ifconfig wlan0 down
```

find the module name like so:

```
sudo lshw -c network|grep module
```

lets say your module name is foobared:

```
sudo rmmod foobared
```

---

### Post by BaristaBoreal on 2008-12-22
I actually have no wireless module installed on my computer.....
sorry for the ridiculous delay in responding, as well.

---

### Post by treepolitik on 2008-12-22
For what it's worth, I don't use Hibernate now.  Thank you for reminding me about the swap space thing though--I currently don't have any.  I have Gnome Hardy and what I do is save my desktop state.  You might check to see if you've a similar option in Xubuntu.  For me, it's Preferences>Sessions>Session Options>Remember Currently Running Applications.

---

