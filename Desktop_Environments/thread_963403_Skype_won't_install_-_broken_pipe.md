---
title: "Skype won't install - broken pipe"
date: 2008-10-30
forum: Desktop Environments
---

### Post by dbee on 2008-10-30
Trying to install skype. It's a pain in the a**. Won't work from repo or from the .deb on the skype site ...

```


babo@eire:~/Desktop$ sudo dpkg -i skype*.deb
(Reading database ... 178866 files and directories currently installed.)
Unpacking skype (from skype-debian_2.0.0.72-1_i386.deb) ...
dpkg: error processing skype-debian_2.0.0.72-1_i386.deb (--install):
 trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 skype-debian_2.0.0.72-1_i386.deb

babo@eire:~/Desktop$ sudo apt-get remove skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.

babo@eire:~/Desktop$ sudo mv /usr/share/icons/skype.png ~/.Trash

babo@eire:~/Desktop$ sudo dpkg -i --force-all skype*.deb
(Reading database ... 178866 files and directories currently installed.)
Unpacking skype (from skype-debian_2.0.0.72-1_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/skype/lang/skype_et.ts', which is also in package skype-common
dpkg - warning, overriding problem because --force enabled:
..........

babo@eire:~/Desktop$ skype
skype: symbol lookup error: /usr/lib/libQtNetwork.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv


```

Anyone got any ideas ?

---

### Post by burnhero on 2008-10-30
Getting same error here.  Tried to install Skype for Windows using Wine as a work around with no success!  Almost thinking of going back to Hardy Haron.

---

### Post by ww711 on 2008-10-30
Try

```
apt-get purge skype
```

I'm currently running the latest version of skype 2.0.0.72 and ii 8.10 with gnome. It's working fine for me.

I went through the same process to install

```
sudo dpkg -i skype*.deb
```

At first it threw some errors about needing some libraries, that I didn't have. After installing the relevant libraries, it's work fine.

---

### Post by burnhero on 2008-10-30
I cleared my cache and redownloaded the .deb for Skype.  I used the commands above in the terminal to install, and now I'm good as gold!

ww711, you rock!

---

### Post by dbee on 2008-10-31
darn. i purged skype but forgot to include it in the code paste.

Still doesn't work. Found the same solution on the net as well and a purge worked.

bummer.

what to do if a purge doesn't work ... ??

---

### Post by pinguy on 2008-10-31
Same problem here, I did have skype installed but it kept on showing the update for it, everytime I tried to install the update I would get:
```
trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```
So I un-installed it and tried re-installing and I kept on getting the same message.

I went into /usr/share/icons/ and deleted the skype.png and tried re-installing but I kept on getting the same message. I wish I didn't un-install it now but theres not alot I can do about it now.

If it didn't take me so long to setup Ubuntu 8.10 I would just do an fresh install, as I did have it installed at one point.

I have ran out of ideas to try, I might try and live without it for a week and see if theres an update for it.

---

### Post by pinguy on 2008-11-05
Got it working.

What I did was install Wajig and did a force install of skype.

 ```
sudo apt-get install wajig
```

To open the GUI tool use the following command

```
gjig
```

Once it opens you should see the following screen

[IMG]http://www.ubuntugeek.com/images/clean/12.png[/IMG]

Now type **skype** into package(s) box and the click **Force Install**

---

### Post by Konsumkind on 2010-02-14
It's an ancient thread, though since I just had the same problem:
You need to purge the **skype-common** package. 

```
sudo apt-get purge skype-common
```

The installation will work without problems afterwards.

---

