---
title: "login dialog not appearing"
date: 2012-08-19
forum: Desktop Environments
---

### Post by harshalnachnolkar on 2012-08-19
My unbuntu has been running fine for last 2 years. I've been updating it constantly and it hasn't given me any problems at all, except now.

Everytime I boot my system, the boot now takes longer than it used to before and then when the login screen is supposed to appear it makes the ubuntu drums sound but I don't get the dialog box where I get to choose the user and enter password.

If I press the power switch it gives me Shut Down, Restart, Suspend, Hibernate options. My mouse is fully active.

In the last session when it was working fine, I tried installing a program called pbrt. I hand edited certain pbrt files in /usr/local/ by giving me permissions to write using su. In the same session, gedit started giving me Segmentaion Fault. I opened Synaptic Manager. Couldn't open.

Things I've already tried by reading through forums -
1.I logged in through root shell prompt and ran updates, reinstalled ubuntu-desktop package

2. Logged in through shell prompt changed back permissions of the file I had changed.

3. Did a recovery mode boot and selected the repair broken packages option

4. At login time did ALT+CTRL+F1 to go to shell, logged in successfully then launched startx. Wanted to install lightdm through synaptic manager, but synaptic manager wouldn't open. Just the same way as in my last proper ubuntu session. I open it, only the waiting icon appears for my mouse pointer and then just nothing

Can someone please help me?

---

### Post by Frogs Hair on 2012-08-20
Hello and Welcome
 
> My unbuntu has been running fine for last 2 years. 
Knowing what version may help you to get an answer.

> Wanted to install lightdm through synaptic manager, but synaptic manager wouldn't open. 

May not be compatible depending on Ubuntu version.

---

### Post by GeorgeWhite5 on 2012-08-20
> **harshalnachnolkar said:**
> My unbuntu has been running fine for last 2 years. I've been updating it constantly and it hasn't given me any problems at all, except now.

Everytime I boot my system, the boot now takes longer than it used to before and then when the login screen is supposed to appear it makes the ubuntu drums sound but I don't get the dialog box where I get to choose the user and enter password.

If I press the power switch it gives me Shut Down, Restart, Suspend, Hibernate options. My mouse is fully active.

In the last session when it was working fine, I tried installing a program called pbrt. I hand edited certain pbrt files in /usr/local/ by giving me permissions to write using su. In the same session, gedit started giving me Segmentaion Fault. I opened Synaptic Manager. Couldn't open.

Things I've already tried by reading through forums -
1.I logged in through root shell prompt and ran updates, reinstalled ubuntu-desktop package

2. Logged in through shell prompt changed back permissions of the file I had changed.

3. Did a recovery mode boot and selected the repair broken packages option

4. At login time did ALT+CTRL+F1 to go to shell, logged in successfully then launched startx. Wanted to install lightdm through synaptic manager, but synaptic manager wouldn't open. Just the same way as in my last proper ubuntu session. I open it, only the waiting icon appears for my mouse pointer and then just nothing

Can someone please help me?

Type either:

```
$ sudo apt-get install lightdm
```
or
```
$ sudo apt-get install gdm
```

into a console (or terminal) to install a login manager.

**EDIT:** Type 'cd /var/log; ls' into a console/terminal and see if there is such thing as "synaptic.log". If there is, type 'nano synaptic.log' or 'cat synaptic.log' and paste it in to a post.

---

### Post by harshalnachnolkar on 2012-08-22
My ubuntu version is 10.04.4 LTS 
codename lucid

---

### Post by harshalnachnolkar on 2012-08-22
I tried installing gdm and it said gdm is already newest version.

I couldn't find a synaptic.log but I did however find a /var/log/gdm folder only viewable to root. I checked inside and I found a log corresponding to my last boot.

the files are named like :0.log.1 or :1-greeter
a log file named :0-greeter was written when I just logged in.
I'm trying to get it uploaded here. But I can't post it through my ubuntu so I tried to copy the files into my Windows partition and read and copy, paste from there. Unfortuanately windows doesn't support the format the file is in

---

