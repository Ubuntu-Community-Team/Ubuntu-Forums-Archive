---
title: "Adding a System Language"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by ClrScr on 2007-07-15
Hi

I need to add French to my Ubunto systems for my students who do not understand english.

How do I do that?

Please I am a SuperNewbie who are forced to use Ubuntu because I can not buy Windows!

Thanks
J

---

### Post by Theimon on 2007-07-16
From the taskbar: System --> Language Support --> Select the right language and set the default.

---

### Post by ClrScr on 2007-07-17
Thanks for your response. I tried that but nothing happens. It shows that busy cursor (circle thingy with a 'light' going in circles) and then nothing else happens.

I warned you I am a supernewbie!

---

### Post by Theimon on 2007-07-17
Hmm, first off it should ask you for your password, then when selecting a language it checks to see if the package is present on the system. If not, it will download and install the package. 
So make sure your internet connection is up. Other than that I can't think of any solution just now....

---

### Post by ClrScr on 2007-08-04
Hi, again

I have now upgraded to 7.04. Uhm when I follow your advice it asks for the password then opens a window called Language Support 

It shows that **only** English is suppoted and there are various options under the default language, ie variations of english. But I can not add a new supported language? SO what do I do now?

Thanks

---

### Post by atomkarinca on 2007-08-04
to add a language support you should check the little box near the name of the language, that's all :) one more thing, don't forget to check "enable support to enter compex characters" at the bottom. it downloads some files and installs them, then reboot your computer and you're good to go.

---

### Post by ClrScr on 2007-08-04
The problem is that it does not SHOW other optons. Only English! How do I get more options so that I can tick the box?

---

### Post by atomkarinca on 2007-08-04
system > administration > synaptic package manager
search "language-pack" and select language-pack-fr and language-pack-fr-base and click apply.
or open a terminal and type
```
sudo apt-get install language-pack-fr language-pack-fr-base
```

---

### Post by ClrScr on 2007-08-04
I have downloaded

for french
 language-pack-fr-base  Version 1:7.04+20070412 
also
for Afrikaans
 language-pack-af-base  Version 1:7.04+20070412

BUT I get 

Error:dependency is not satisfiable

What am I doing wrong?

Thanks

---

### Post by atomkarinca on 2007-08-04
you should also check language-pack-fr and language-pack-af

---

### Post by ClrScr on 2007-08-04
I have copied the files to the directory called student and this is what happens:

student@student:~$ sudo apt-get install language-pack-af language-pack-af-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-pack-af
student@student:~$ 

I have also tried the alternative solution, but Feisty does not see the files. I have tried searching for them. 

PS the Feisty computer is not online. I have another windows system online and then copy it from the one to the other with a memory stick.

Eish, I dont know!!!!

Yes I know I am doing something stupid

Thanks!

---

### Post by atomkarinca on 2007-08-04
try to download the .deb files:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flanguage-pack-af%2Flanguage-pack-af_7.04%2B20070412_all.deb&md5sum=eb3280a1f7dc78e2e52d1bdbf58dd839&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flanguage-pack-af%2Flanguage-pack-af_7.04%2B20070412_all.deb&md5sum=eb3280a1f7dc78e2e52d1bdbf58dd839&arch=all&type=main)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flanguage-pack-af-base%2Flanguage-pack-af-base_7.04%2B20070412_all.deb&md5sum=eb91458af085db6597166b3c934a1916&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fl%2Flanguage-pack-af-base%2Flanguage-pack-af-base_7.04%2B20070412_all.deb&md5sum=eb91458af085db6597166b3c934a1916&arch=all&type=main)

edit: you just need to double-click to install these files.

---

### Post by ClrScr on 2007-08-04
Thanks. These are the same files I mentioned in the previous post. I redownloaded them.

If I double click them it says dependency is not satisfiable.
The same with the french files
I still have to try and install a HP 1018, if/when I (you) this thing running in french!

---

### Post by atomkarinca on 2007-08-04
alright. note the dependencies down, search them here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)
download them and install them. without internet it's hard to go around.

---

### Post by ClrScr on 2007-08-05
Here is the latest update in the saga student

@student:~$ dir
Desktop    Examples                                language-pack-af_7.04+20070412.tar.gz        Music     Windows\ XP.jpg
Documents  language-pack-af_7.04+20070412_all.deb  language-pack-af-base_7.04+20070412_all.deb  Pictures
student@student:~$ 
student@student:~$  sudo apt-get install language-pack-af language-pack-af-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-pack-af
student@student:~$  sudo apt-get install language-pack-af_7.04+20070412_all.deb language-pack-af-basee_7.04+20070412_all.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-pack-af_7.04+20070412_all.deb
student@student:~$ 


SO from this it is clear (I think) that the relevant files are in the actual directory

As you can see I have also modified the command to include the COMPLETE file name.
BUT no luck

Also If I double click these files the following happens

Clicking pack-af it will complain about a ERROR:Dependency not satisfiable:language-pack-af-base
And then
Clicking pack-af-base it will complain about a ERROR:Dependency not satisfiable:language-pack-af

So it is a circular thing

Next suggstion please!

The reason why I can not go online with this pc is: I am living in madagascar and use a dialup system I have a HUAWEI Wireless usb modem ETS2056 and guess what, no driver is available!

---

### Post by atomkarinca on 2007-08-05
> **ClrScr said:**
> Here is the latest update in the saga student

@student:~$ dir
Desktop    Examples                                language-pack-af_7.04+20070412.tar.gz        Music     Windows\ XP.jpg
Documents  language-pack-af_7.04+20070412_all.deb  language-pack-af-base_7.04+20070412_all.deb  Pictures
student@student:~$ 
student@student:~$  sudo apt-get install language-pack-af language-pack-af-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-pack-af
student@student:~$  sudo apt-get install language-pack-af_7.04+20070412_all.deb language-pack-af-basee_7.04+20070412_all.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package language-pack-af_7.04+20070412_all.deb
student@student:~$ 


SO from this it is clear (I think) that the relevant files are in the actual directory

As you can see I have also modified the command to include the COMPLETE file name.
BUT no luck

Also If I double click these files the following happens

Clicking pack-af it will complain about a ERROR:Dependency not satisfiable:language-pack-af-base
And then
Clicking pack-af-base it will complain about a ERROR:Dependency not satisfiable:language-pack-af

So it is a circular thing

Next suggstion please!

The reason why I can not go online with this pc is: I am living in madagascar and use a dialup system I have a HUAWEI Wireless usb modem ETS2056 and guess what, no driver is available!

now i can only think of one way. try these:
```
sudo dpkg -i language-pack-af_7.04+20070412_all.deb
sudo dpkg -i language-pack-af-base_7.04+20070412_all.deb
```

---

### Post by ClrScr on 2007-08-05
I have had some success. I installed the pack-af, but have had absolute no luck with the pack-af-bqse

It is in the directory but that feisty is obviously not very farsighted.

[I]student@student:~$ sudo apt-cache search language-pack-af
language-pack-af - translation updates for language Afrikaans
student@student:~$ sudo apt-get install language-pack-af language-pack-af-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
language-pack-af is already the newest version.
Package language-pack-af-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  language-pack-af
E: Package language-pack-af-base has no installation candidate
student@student:~$ 
student@student:~$ sudo dpkg -i install language-pack-af-base
dpkg: error processing install (--install):
 cannot access archive: No such file or directory
dpkg: error processing language-pack-af-base (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install
 language-pack-af-base
student@student:~$ sudo apt-cache search language-pack-af-base
language-pack-af - translation updates for language Afrikaans
student@student:~$ 
[/I]


It sees af but not base and with the cache search also does not see it, but if you do q *dir* command it shows it.

If you run the synaptic package manager it says that there is a broken package, which turns out to be pack-af

aaaaahhhhhh

---

### Post by ClrScr on 2007-08-05
I tried. It doesnt work!

---

### Post by ClrScr on 2007-08-05
I have had some succes. I instqlled the tqr files qnd something hqppened. What do I do next?

The synaptic package manger still does not see these.

Thanks


[I]student@student:~$ tar xfvz language-pack-af_7.04+20070412.tar.gz
language-pack-af/
language-pack-af/COPYING
language-pack-af/data/
language-pack-af/debian/
language-pack-af/debian/changelog
language-pack-af/debian/compat
language-pack-af/debian/control
language-pack-af/debian/copyright
language-pack-af/debian/rules
language-pack-af/debian/upgrade-notes/
student@student:~$ language-pack-af-base_7.04+20070412.tar.gz
bash: language-pack-af-base_7.04+20070412.tar.gz: command not found
student@student:~$ tar xfvz language-pack-af-base_7.04+20070412.tar.gz
language-pack-af-base/
language-pack-af-base/COPYING
language-pack-af-base/data/
language-pack-af-base/data/extra.tar
language-pack-af-base/data/af/
language-pack-af-base/data/af/LC_MESSAGES/
language-pack-af-base/data/af/LC_MESSAGES/adduser.po
language-pack-af-base/data/af/LC_MESSAGES/apt.po
language-pack-af-base/data/af/LC_MESSAGES/bluez-pin.po
language-pack-af-base/data/af/LC_MESSAGES/coreutils.po
language-pack-af-base/data/af/LC_MESSAGES/discover.po
language-pack-af-base/data/af/LC_MESSAGES/gaim.po
language-pack-af-base/data/af/LC_MESSAGES/sed.po
language-pack-af-base/data/af/LC_MESSAGES/ssed.po
language-pack-af-base/data/af/LC_MESSAGES/synaptic.po
language-pack-af-base/data/af/LC_MESSAGES/xmms.po
language-pack-af-base/data/af/LC_MESSAGES/libxfcegui4.po
language-pack-af-base/data/af/LC_MESSAGES/po4a.po
language-pack-af-base/data/af/LC_MESSAGES/tuxpaint.po
language-pack-af-base/data/af/LC_MESSAGES/tuxpaint-stamps.po
language-pack-af-base/data/af/LC_MESSAGES/xfce-mcs-manager.po
language-pack-af-base/data/af/LC_MESSAGES/xfce-utils.po
language-pack-af-base/data/af/LC_MESSAGES/launchpad-integration.po
language-pack-af-base/data/af/LC_MESSAGES/xkeyboard-config.po
language-pack-af-base/data/af/LC_MESSAGES/alacarte.po
language-pack-af-base/data/af/LC_MESSAGES/bootloader.po
language-pack-af-base/data/af/LC_MESSAGES/gstreamer-0.10.po
language-pack-af-base/data/af/LC_MESSAGES/libpq5.po
language-pack-af-base/data/af/LC_MESSAGES/postgres-8.2.po
language-pack-af-base/data/af/LC_MESSAGES/gst-plugins-good-0.10.po
language-pack-af-base/data/af/LC_MESSAGES/Thunar.po
language-pack-af-base/data/af/LC_MESSAGES/verve-plugin.po
language-pack-af-base/data/af/LC_MESSAGES/ubiquity.po
language-pack-af-base/debian/
language-pack-af-base/debian/changelog
language-pack-af-base/debian/compat
language-pack-af-base/debian/control
language-pack-af-base/debian/copyright
language-pack-af-base/debian/postinst
language-pack-af-base/debian/postrm
language-pack-af-base/debian/rules
student@student:~$ [/I]

---

### Post by atomkarinca on 2007-08-05
after you extracted those files with tar xfvz, you can install them by:
```
cd language-pack-af
./configure
make
sudo make install

cd ..
cd language-pack-af-base
./configure
make
sudo make install
```

---

### Post by ClrScr on 2007-08-05
Thanks, but....

the first command 
cd language-pack-af
works

Then on 
./configure

I get bash:./configure: No such file or directory

There are 2 Directories nl. data and debian

and one file nl. copying

It is the same with af-base

so on make I get

make: ***No targets specified and no makefile found. Stop

---

### Post by atomkarinca on 2007-08-05
i just realized there are no configuration files extracted. i'm looking into it.

---

### Post by ClrScr on 2007-08-06
Question:

I have been playing around with the Add/Remove applications. 

And under System Tools

There is a Language Support option

but it says that it cannot be installed on my computer type AMD 64

Do you think this can be the cause? And if you do not know, where can I go and ask?

Thanks
ClrScr

---

