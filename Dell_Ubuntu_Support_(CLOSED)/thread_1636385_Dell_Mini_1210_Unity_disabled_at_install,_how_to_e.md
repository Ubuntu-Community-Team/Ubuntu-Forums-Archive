---
title: "Dell Mini 1210 Unity disabled at install, how to enable?"
date: 2010-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sinerasis on 2010-12-03
I'm installing 10.10 on a Dell mini 1210.

Install runs fine, no problems.

On first boot, I got a message saying unity can't start because no drivers for graphics. I fixed this using some other threads, and have proper graphics at this point.

I found some other forum posts on how to install/enable Unity, however I'm unable to switch to the Unity interface at this point.

I'm going to System>Administration>Login Screen and adjusting the default session. I've toggled it between Ubuntu Desktop Edition and Ubuntu Netbook Edition with no change at all.

Lil' help? :)

---

### Post by garvinrick4 on 2010-12-03
In terminal:
```
sudo apt-get install aptitude
``````
aptitude show unity
```If not installed:
```
sudo apt-get install unity
```
Something is not installed properly:
```
aptitude show ubuntu-netbook
```
Does it have to be installed with unity?
```
sudo apt-get install ubuntu-netbook
```
Something is just not installed:

---

### Post by fjgaude on 2010-12-03
> **sinerasis said:**
> I'm installing 10.10 on a Dell mini 1210.

Install runs fine, no problems.

On first boot, I got a message saying unity can't start because no drivers for graphics. I fixed this using some other threads, and have proper graphics at this point.

I found some other forum posts on how to install/enable Unity, however I'm unable to switch to the Unity interface at this point.

I'm going to System>Administration>Login Screen and adjusting the default session. I've toggled it between Ubuntu Desktop Edition and Ubuntu Netbook Edition with no change at all.

Lil' help? :)

Did you reboot after making the change? I have to do that to effect the change.

Also, take a look at the Log-on Screen in the System Folder and notice what the options are.

---

### Post by sinerasis on 2010-12-03
garvinrick4: Both show they're installed, I'll try re-installing at this point.

fjgaude: Yes, I did a reboot after changing the login setting, still nothing.

---

### Post by fjgaude on 2010-12-04
Okay, I installed the version you speak of on a mini 10n and got the same results as you. We seem to not be ready yet for Unity! <smile>

---

