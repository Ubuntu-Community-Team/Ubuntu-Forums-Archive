---
title: "Removing Suspend Hibernate buttons"
date: 2012-09-24
forum: Desktop Environments
---

### Post by c4c on 2012-09-24
I'm running Lubuntu 12.04 with LXDE. I would like to know if it is possible (and of course how to) remove the options, or simply the *buttons* to Suspend and Hibernate from the "Logout Lubuntu Session" dialogue box that pops-up from the power menu.
 
Thanks in advance to anyone who can tell me if/how this is accomplished, or lead me in the right direction.

---

### Post by stinkeye on 2012-09-24
This is how I remove hibernate/suspend from the session menu in unity.
No idea if it applies to lubuntu.
In terminal...
```
gksudo gedit  /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```

There are two sections in this file, the first for suspend and the second for hibernate. Near the end of each section there is a line...
```
<allow_active>[COLOR="Red"]yes[/COLOR]</allow_active>
```

Change this entry from “yes” to “no” in each section to disable hibernate and suspend.
```
<allow_active>[COLOR="red"]no[/COLOR]</allow_active>
```

---

### Post by marinara on 2012-09-26
build the lxsession package with your changes in the c code for lxsession-logout

---

### Post by mc4man on 2012-09-29
> **stinkeye said:**
> 
There are two sections in this file, the first for suspend and the second for hibernate. Near the end of each section there is a line...
```
<allow_active>[COLOR="Red"]yes[/COLOR]</allow_active>
```
]
Thanks for that, was just thinking about whacking that option after inadvertent hitting it for the hundredth  time instead of the log out. 

(will probably put in a .pkla so it can't get updated away

---

### Post by vasa1 on 2012-09-29
> **mc4man said:**
> Thanks for that, was just thinking about whacking that option after inadvertent hitting it for the hundredth  time instead of the log out. 

(will probably put in a .pkla so it can't get updated away
And thank you pointing out Stinkeye's post which I didn't pay enough attention to. I subsequently offered a bounty at [askubuntu.com]("http://askubuntu.com/q/192911/25656") and got pointed to the same thing :)

The only drawback I can think of is that updates may overwrite the changes.

So could you please explain the **.pkla** approach? What exactly has to be done?

---

### Post by vasa1 on 2012-09-29
I came across your answer [here]("http://askubuntu.com/a/98032/25656").

---

