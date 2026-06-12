---
title: "What are the commands to install and remove compiz on Xubuntu 14.04"
date: 2014-05-24
forum: Desktop Environments
---

### Post by danbuz on 2014-05-24
Hi guys,

I'm not a techie and just wonder how to install compiz on Xubuntu and how to completely remove it eventually? I've been searching all over the net with no success, the only thing I found was a guide for 13.03 but I don't know is it the same for 14.04 plus there was no removal guide.

Thanks in advance!

---

### Post by deadflowr on 2014-05-24
Wouldn't
```
sudo apt-get install compiz
```
install compiz.
And
```
sudo apt-get purge compiz
```
remove it?
You can also run it as a simulation
```
sudo apt-get -s purge compiz
```
the -s marks it as a simulated action only.
This will show you exactly will be removed.

---

### Post by grahammechanical on 2014-05-24
Does Xubuntu have a software centre? The software centre will install and remove all kinds of software including Compiz.

Regards.

---

### Post by danbuz on 2014-05-24
nothing works on xubuntu - nither terminal comands nor ubuntu center..

---

### Post by deadflowr on 2014-05-24
Post the output of whatever commands you are trying.
Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by danbuz on 2014-05-24
> **deadflowr said:**
> Post the output of whatever commands you are trying.
Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

I tried the codes above, and ubuntu center

---

### Post by LastDino on 2014-05-24
Yes, but you need copy paste what happened in terminal after you gave/typed and entered above commands.

---

### Post by deadflowr on 2014-05-24
^^^^This
We would need to see what you wrote, and what the output was.

---

### Post by danbuz on 2014-05-25
> **deadflowr said:**
> ^^^^This
We would need to see what you wrote, and what the output was.

in terminal

```

sudo apt-get install compiz

```

```
After this operation, 12,1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y

```

```
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core


```

So compiz does not appear in menu at all. After this I purged it and installed everything via USC, and again nothing appears when i type compiz or try with terminal.

I use i5 with Optimus 2Ghz

---

### Post by grumblebum2 on 2014-05-25
You have to replace your current window manager...
```
compiz --replace &
```

You can find info like this in the manual pages.
ie
```
man compiz
```

To configure compiz settings, install ccsm...
```
sudo apt-get install **c**ompiz**c**onfig-**s**ettings-**m**anager
```

---

### Post by danbuz on 2014-05-25
And what to type if I want to remove all things the old way, how to put back the old window manager ?

---

### Post by grumblebum2 on 2014-05-25
There is no need to remove.
Compiz is not the default window manger in Xubuntu. It will not run unless you have told it to.

If you run **compiz --replace**, your window manager is only replaced for that session
unless you have remember running applications on logout enabled.
Logging out and back in or running **xfwm4 --replace** will return you to 
to the default window manger in Xubuntu.

If you want to uninstall I think this will do it....
```
sudo apt-get remove compiz-core
```
Just check what it wants to remove before answering yes

---

### Post by danbuz on 2014-05-26
> **grumblebum2 said:**
> There is no need to remove.
Compiz is not the default window manger in Xubuntu. It will not run unless you have told it to.

If you run **compiz --replace**, your window manager is only replaced for that session
unless you have remember running applications on logout enabled.
Logging out and back in or running **xfwm4 --replace** will return you to 
to the default window manger in Xubuntu.

If you want to uninstall I think this will do it....
```
sudo apt-get remove compiz-core
```
Just check what it wants to remove before answering yes

So excuse my ignorance, but I understood that if I install compiz the way described above in xubuntu,
it will not be running by default after reboot and I have to start it manually each session? 

If that is correct should I install kwin, or kwin is not permanent again?

---

### Post by grumblebum2 on 2014-05-26
> **danbuz said:**
> So excuse my ignorance, but I understood that if I install compiz the way described above in xubuntu,
it will not be running by default after reboot and I have to start it manually each session? 

If that is correct should I install kwin, or kwin is not permanent again?
The default window manager for the Xubuntu session is xfwm4.
You need to change the default manager or replace at startup.

Don't use xfce and don't know the exact procedure.
Search google or youtube for " Compiz in Xubuntu 14.04" or "compiz in xfce".
Find a recent one and note the changes you make.

---

