---
title: "LXDE installed - can't log in and use it"
date: 2016-11-30
forum: Desktop Environments
---

### Post by kkaniff on 2016-11-30
Hi there

I used the ```
sudo apt-get install lxde
``` command to install LXDE. After reboot and multiple tries still can't get it to show in my login window.

This problem seems to have been discussed in many places but none of the suggested solutions work for me. Can't anyone help me test my install?

Thanks
KK

---

### Post by deadflowr on 2016-11-30
> This problem seems to have been discussed in many places but none of the suggested solutions work for me. 
As much as I would like to believe I'm psychic, alas I am not.
Please post the suggestions you tried so we don't re-post those and cause more frustrations than is necessary.

Also,
*Thread moved to **Desktop Environments**.*

---

### Post by vasa1 on 2016-11-30
What does[s]```
ls /usr/share/lxsessions
```[/s]```
ls /usr/share/xsessions
```show?
You should have LXDE.desktop there. For me, ```
grep -v Comment LXDE.desktop

```shows this```
[Desktop Entry]
# The names/descriptions should really be better
Name=LXDE
Exec=/usr/bin/startlxde
# Icon=
Type=Application

```

---

### Post by kkaniff on 2016-11-30
Thanks., Vasa1. I get 
```
ls: cannot access '/usr/share/lxsessions': No such file or directory
```

What am I missing? After trying

```
sudo apt-get install lxde
```

I got:

```
lxde is already the newest version (7ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

---

### Post by vasa1 on 2016-11-30
> **kkaniff said:**
> Thanks., Vasa1. I get 
```
ls: cannot access '/usr/share/lxsessions': No such file or directory
```

...
It should be just **xsessions** and _not_ **lxsessions**.

Very sorry about that!

---

### Post by kkaniff on 2016-12-01
No problem. 

Now it shows that I do have LXDE installed. Here it is:

```
Lubuntu.desktop          LXDE.desktop     xfce.desktop
Lubuntu-Netbook.desktop  openbox.desktop  xubuntu.desktop
```

Does anyone have any suggestions as to what to do next? Thanks.

---

### Post by kkaniff on 2016-12-01
> **deadflowr said:**
> As much as I would like to believe I'm psychic, alas I am not.
Please post the suggestions you tried so we don't re-post those and cause more frustrations than is necessary.

Also,
*Thread moved to **Desktop Environments**.*

Sorry, **Deadflowr**. I didn't phrase my question correctly. I'd tried many different things without knowing what I was really doing, just to get the LXDE desktop up. I can't even remember the commands I used.

 I was hoping for someone to give me pointers how to test if the desktop environment is on my system or not and this is what **Vasa1** is doing. Thanks and sorry a sloppy first post.

---

### Post by vasa1 on 2016-12-01
If everything is normal, there should be an icon somewhere on the login screen that, when clicked on, gives you a dropdown of the various login sessions available. Sometimes, that icon is next to your user name. In the case of Lubuntu, it's near the top right of the screen. I don't know where it is with Xubuntu.

---

### Post by kkaniff on 2016-12-01
> **vasa1 said:**
> If everything is normal, there should be an icon somewhere on the login screen that, when clicked on, gives you a dropdown of the various login sessions available. Sometimes, that icon is next to your user name. In the case of Lubuntu, it's near the top right of the screen. I don't know where it is with Xubuntu.

... The icon is right up top of the screen. I was used to the Ubuntu screen and wasn't looking in the right place. 

You're the man, **vasa1**.

Is there anywhere I click to give thanks?

---

### Post by vasa1 on 2016-12-01
> **kkaniff said:**
> ...
Is there anywhere I click to give thanks?

Here you go: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

