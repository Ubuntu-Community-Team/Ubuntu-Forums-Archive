---
title: "cannot update Compiz"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by gentlemanmasher on 2007-09-20
i added the amaranth repo for compiz but I am not able to update no matter which way I use.

sudo aptitude update
sudp aptitude upgrade

synaptic or Update manager 

It says it completes the upgrade but I continue to get the upgrade message.

i am trying to upgrade from 1:0.5.2git20070829-0Ubuntu1amaranth to 1:0:5.2+git20070829-0ubuntu1amaranth1

Any ideas???

---

### Post by praet on 2007-09-21
Can you post your exact repo url?
Using the recommended source, my version reads as follows:
(0.5.2+git20070829-0ubuntu1amaranth1) 

Just note that the url has changed from ppa.dogfood .... to 
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

Additionally, there is a ppa bug that causes compiz-core package to continually ask to be updated, regardless of if it was already updated. If you want to put that package on hold use dpkg --set-selections.

---

### Post by gentlemanmasher on 2007-09-21
That actually is the error.  It is the Compiz core.  So will this work itself out if I just leave the source on?


Also could you be more specific on how to put a package on hold??

Thanks a million

---

### Post by praet on 2007-09-24
Here is how to set the package on hold:
```
echo compiz-core hold | sudo dpkg --set-selections
```

To un-hold the package change the 'hold' command to 'install'
```
echo compiz-core install | sudo dpkg --set-selections
```

---

### Post by petit.padavoine on 2007-09-24
This bug and the fact that many plugins are missing from Amaranth's packages is why I use Trevino's repos. I suggest you do the same :).

---

### Post by Amaranth on 2007-09-24
Sure, if you don't want to upgrade to gutsy.

---

### Post by petit.padavoine on 2007-09-25
Yes, most people are still using Feisty, and will uninstall their Trevino packages before upgrading. It's worth the hassle to get packages with are up-to-date and have all the plugins.
Sorry Amaranth, you're doing great work, I just prefer Trevino's repos lol ^^.

---

