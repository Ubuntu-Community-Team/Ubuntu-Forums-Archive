---
title: "Viber does not start after update to 7.0.0.1035"
date: 2017-12-15
forum: Desktop Environments
---

### Post by ockac23 on 2017-12-15
Hi folks,

Yesterday I noticed, that my desktop version of the Viber application misses some new features and I decided to update the application on my Ubuntu 14.04. 64 bit system. 

Old Viber version 6.5.x.x...?
New Viber version after update 7.0.0.1035

I downloaded the viber.deb file and installed it with the command #sudo dpkg -i viber.deb. Installation ran successful.
The Viber icon appears in my start menu now but Viber does not start anymore.

I tried several things. If i try to run: 

~ /opt/viber/Viber

the output is as follows:

/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by /opt/viber/Viber)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /opt/viber/Viber)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /opt/viber/lib/libQt5Location.so.5)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /opt/viber/lib/libicui18n.so.52)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /opt/viber/lib/libicuuc.so.52)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by /opt/viber/lib/libQt5WebEngineCore.so.5)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by /opt/viber/lib/libQt5Qml.so.5)
/opt/viber/Viber: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /opt/viber/lib/libQt5Core.so.5)

---

### Post by again? on 2017-12-17
You could try a full-upgrade.
From man apt:
> **upgrade**
upgrade is used to install available upgrades of all packages currently installed on the system from the sources configured via sources.list(5).
New packages will be installed if required to satisfy dependencies, but existing packages will never be removed.
If an upgrade for a package requires the remove of an installed package the upgrade for this package isn't performed.

**full-upgrade**
full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.
```
sudo apt update
sudo apt full-upgrade
```

---

### Post by ockac23 on 2017-12-17
Thanks for the idea, guber2. 
But viber still does not start after this.

:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by again? on 2017-12-17
The problem seems to be described [HERE]("https://github.com/CauldronDevelopmentLLC/CAMotics/issues/178") for another package in Linux Mint 17.3 which is based on Ubuntu 14.04.
> You need at least libstdc++.so.6.0.20 for GLIBCXX_3.4.20 support. 
This library is provided by libstdc++6 v4.9.0. 
Since you have v4.8.4 you are one minor version behind. 
v4.8.4 provides C++ ABI support only up to **GLIBCXX_3.4.19**.

I tried the solution offered to use a ppa to install a newer version of gcc.
This was done on a live cd of 14.04.5 where I installed the latest viber.deb then added the repo...
```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt update
sudo apt install gcc-4.9
sudo apt install libstdc++6

```

After install it showed I now have GLIBCXX > 3.4.19 ...
```
**[COLOR="#008000"]ubuntu@ubuntu:~$[/COLOR] strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX_3.4**
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBCXX_3.4.18
GLIBCXX_3.4.19
GLIBCXX_3.4.20
GLIBCXX_3.4.21
GLIBCXX_3.4.22
GLIBCXX_3.4.23
GLIBCXX_3.4.24
GLIBCXX_DEBUG_MESSAGE_LENGTH
```

After using the ppa it would be a good idea to disable and make yourself familiar with ppa-purge if not already.
[How to purge a PPA]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

---

### Post by ockac23 on 2017-12-18
Ahh guber2, I tried all the steps above, it does not work. The app does not start.
I don't know why.... Maybe I will wait for another viber update on my ubuntu and till then I will use the app only on my phone.. :-(
Thank you for your efforts.

---

### Post by again? on 2017-12-18
ok.
Just curious.
Was your output from the following showing greater than GLIBCXX_3.4.19 as in my previous post.
```
strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX_3.4
```

You could move on to the next LTS, Ubuntu 16.04, a little earlier than you might have normally.

---

### Post by ockac23 on 2017-12-19
I have done these steps again today, 

sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt update
sudo apt install gcc-4.9
sudo apt install libstdc++6

and suddenly viber 7.0.0. started this time..... I don't know why yesterday it did not work. Maybe because I have purged the ppa after installing the above packages using the command

[COLOR=#000000][FONT=&amp]sudo add-apt-repository --remove ppa:[/FONT][/COLOR]ubuntu-toolchain-r/test 

But that's what I understood from the article, that a ppa can be purged this way to free space without uninstalling the packages?

And regarding your last question, there is no output of the code:

strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXXGLIBCXX_3.4

The cursor just goes to the next line.

---

### Post by again? on 2017-12-19
Ahh sorry, the strings command was a copy and paste error.
Should be 
```
strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX_3.4
```

As for ppa-purge, that was only meant to be used if for some reason the packages from  ppa:ubuntu-toolchain-r/test
caused problems.
ppa-purge disables a PPA and reverts to official packages.
You should also use ppa purge on all third party repositories before you upgrade Ubuntu to a new release.

I still recommend to disable the ppa using **software and updates > other software**.
If in the future you wish to purge the ppa, you will need to re-enable.

I first thought when the ppa didn't work ...maybe ockac23 went all the way through and ran ppa-purge as well.
Said to myself, "Nah... he wouldn't do that" :p

---

### Post by ockac23 on 2017-12-20
Hi guber2,

Here the output from the code, as you asked for it:

$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX_3.4
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBCXX_3.4.18
GLIBCXX_3.4.19
GLIBCXX_3.4.20
GLIBCXX_3.4.21
GLIBCXX_3.4.22
GLIBCXX_3.4.23
GLIBCXX_3.4.24

And two additional questions. 
1.In **software and updates -> other software** this [COLOR=#000000]ppa:ubuntu-toolchain-r/test source code appears twice. Can I delete one of the entry's? Screenshot attached. 
2. Should I disable all ppa's in "other software", when I decide to upgrade Ubuntu to 16.4.lts

Thank you.[/COLOR]

---

### Post by again? on 2017-12-20
You can delete multiple entries that you may have from adding the ppa twice.

When you add a ppa it also adds a "Source Code" entry.
The "Source Code" entry can be removed or disabled also if you like.
Only needed if you want to download and inspect the code.

It's always a good idea to run ppa-purge on added ppas before upgrading.
This command will list your enabled ppas in a form to use with ppa purge.
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*.list); do cat ${PPA_FILE} | egrep -v '^#|^ *$' | grep "ppa.launchpad.net" | cut -d "/" -f4-5; done
```
eg for me...
```
**[COLOR="#008000"]glen@GU17:~$[/COLOR] for PPA_FILE in $(ls /etc/apt/sources.list.d/*.list); do cat ${PPA_FILE} | egrep -v '^#|^ *$' | grep "ppa.launchpad.net" | cut -d "/" -f4-5; done**
graphics-drivers/ppa
linvinus/altyo
**team-xbmc/ppa**
```
So to purge the xbmc ppa I would use
```
sudo ppa-purge ppa:**team-xbmc/ppa**
```

You should start with a base as close to default as you can which includes removing proprietary gfx drivers.
I prefer not to upgrade but just do fresh installs.
Saves the headache of not knowing if an upgrade is the cause of a problem.

Tips for using ppas:
Always check in synaptic to see what the ppa contains as it may also contain other unwanted upgrades.
[ATTACH=CONFIG]277902[/ATTACH]

Use the edit button to add a comment to reflect what the ppa contains. This becomes the ppa title in "other software".
[ATTACH=CONFIG]277901[/ATTACH]

---

### Post by ockac23 on 2017-12-20
Thank you very much, guber2!

---

### Post by keypress on 2017-12-28
Another solution that helped me was:

cd /tmp/
wget [http://ftp.pl.debian.org/debian/pool/main/g/gcc-4.9/libstdc++6_4.9.2-10_amd64.deb](http://ftp.pl.debian.org/debian/pool/main/g/gcc-4.9/libstdc++6_4.9.2-10_amd64.deb)
sudo mkdir /opt/fakeroot
sudo dpkg -x /tmp/libstdc++6_4.9.2-10_amd64.deb /opt/fakeroot/
# run Viber
( LD_LIBRARY_PATH=/opt/fakeroot/usr/lib/x86_64-linux-gnu/ /opt/viber/Viber )

---

### Post by ockac23 on 2018-02-22
> **guber2 said:**
> .......
You should also use ppa purge on all third party repositories before you upgrade Ubuntu to a new release.

I still recommend to disable the ppa using **software and updates > other software**.
If in the future you wish to purge the ppa, you will need to re-enable.


So guber2, just to clarify, when upgrading ubuntu to a new release, is it enough to disable the ppa using "software and updates > other software" or I should purge it?

---

### Post by again? on 2018-02-22
> **ockac23 said:**
> So guber2, just to clarify, when upgrading ubuntu to a new release, is it enough to disable the ppa using "software and updates > other software" or I should purge it?
Using ppa-purge is the safest way to go.
It will downgrade third party packages or if there is no version of a third party package 
in the official repos, it will remove it.

---

