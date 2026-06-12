---
title: "Can't install anything from apt-get, synaptic or add application"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Omning on 2005-11-13
I'm having a problem installing *any* package right now.  Using 5.10/32bit, by the way.

```
sudo apt-get install gstreamer0.8-lame Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
tdear@serenity:/var/cache/apt/archives$

```

and when I try to -f it, I get pretty much the same output
```
sudo apt-get -f install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Synaptic returns
```
E: /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb: unable to open files list file for package `libbonoboui2-0'

```

Add application returns the same error.   This happens regardless of the package I try to download, the only thing that changes about is the package names, or the name listed in "unable to open files list file for package `xxx'

Any idea/help would be greatly appreciated!

---

### Post by Kapre on 2005-11-13
Maybe the repos are down. Try again later or you may want to read this [thread]("http://www.ubuntuforums.org/showthread.php?t=66563&page=72&highlight=automatix") since your trying to install some codecs

K

---

### Post by Omning on 2005-11-13
[QUOTE=Kapre]Maybe the repos are down. Try again later ...

K[/QUOTE]

I thought about this, so I tried to simply download the packages (synaptic), and then install them locally...

```

/var/cache/apt/archives$ sudo dpkg -i liblame0_3.96.1-1_i386.deb (Reading database ... dpkg: error processing liblame0_3.96.1-1_i386.deb (--install):
 unable to open files list file for package `libbonoboui2-0': Input/output errorErrors were encountered while processing:
 liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
```

If the repos were down I wouldn't even be able to download a package, would I?

---

### Post by Omning on 2005-11-14
Just got an update notification, and get the same results

```
E: /var/cache/apt/archives/libnautilus-extension1_2.12.1-0ubuntu1.1_i386.deb: unable to open files list file for package `libbonoboui2-0'

```

terminal output is
```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libnautilus-extension1_2.12.1-0ubuntu1.1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error

```

---

### Post by Omning on 2005-11-14
Is there some apt config file that I've lost permission of or something? The only one I know if is sources.list

---

### Post by Omning on 2005-11-14
(bump)

---

### Post by Omning on 2005-11-14
come on guys don't give me the standard windows answer.  I really don't want to reinstall.

---

### Post by professor_chaos on 2005-11-14
can you try to delete /var/cache/apt/archives/libnautilus-extension1_2.12.1-0ubuntu1.1_i386.deb

and

/var/cache/apt/archives/liblame0_3.96.1-1_i386.deb

then what happens when you update/install???

---

### Post by Omning on 2005-11-14
I rm *.deb in the  /var/cache/apt/archives folder, and ran update again
Downloads the files fine (and they show up in /var/cache/apt/archives) and spits out this error

> 
E: /var/cache/apt/archives/libnautilus-extension1_2.12.1-0ubuntu1.1_i386.deb: unable to open files list file for package `libbonoboui2-0'


---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]I rm *.deb in the  /var/cache/apt/archives folder, and ran update again
Downloads the files fine (and they show up in /var/cache/apt/archives) and spits out this error[/QUOTE]do the folllwing:
```
sudo rm -f /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/partial/lock
sudo apt-get clean
```and try again.

---

### Post by Omning on 2005-11-14
Same errors and I verified the removal of the lock files and the recreation of them after running apt-get clean

---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]Same errors and I verified the removal of the lock files and the recreation of them after running apt-get clean[/QUOTE]
please paste the contents of your */etc/apt/sources.list*

---

### Post by Omning on 2005-11-14
> 
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 


edit

---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]edit[/QUOTE]
ok try the follwing one after the other:
```
sudo apt-get -f install
sudo apt-get install liblame0
```

---

### Post by Omning on 2005-11-14
[QUOTE=arnieboy]ok try the follwing one after the other:
```
sudo apt-get -f install
sudo apt-get install liblame0
```[/QUOTE]

> 
sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get install liblame0
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  liblame0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/151kB of archives.
After unpacking 385kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output errorErrors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
 .

---

### Post by arnieboy on 2005-11-14
```
sudo apt-get --purge remove libbonoboui2-0 liblame0
sudo apt-get -f install
sudo apt-get install liblame0
```

---

### Post by Omning on 2005-11-14
[QUOTE=arnieboy]```
sudo apt-get --purge remove libbonoboui2-0 liblame0
sudo apt-get -f install
sudo apt-get install liblame0
```[/QUOTE]
```
The following packages will be REMOVED:
  bug-buddy* contact-lookup-applet* eog* evince* evolution*
  evolution-exchange* evolution-plugins* evolution-webcal* file-roller*
  firefox-gnome-support* gcalctool* gconf-editor* gdm* gedit* gnome-about*
  gnome-app-install* gnome-applets* gnome-applets-data* gnome-btdownload*
  gnome-control-center* gnome-cups-manager* gnome-games* gnome-media*
  gnome-netstatus-applet* gnome-panel* gnome-pilot* gnome-pilot-conduits*
  gnome-session* gnome-spell* gnome-system-monitor* gnome-system-tools*
  gnome-terminal* gnome-utils* gnome-volume-manager* gnomemeeting* gthumb*
  gtkhtml3.8* gucharmap* hal-device-manager* hwdb-client* libbonoboui2-0*
  libedataserverui1.2-6* libeel2-2* libexchange-storage1.2-0*
  libgnome-desktop-2* libgnome2-perl* libgnomecupsui1.0-1* libgnomeui-0*
  libgtkhtml3.8-15* libgucharmap4* liblpint-bonobo0* libpanel-applet2-0*
  nautilus* nautilus-cd-burner* nautilus-sendto* python-gnome2*
  python-gnome2-extras* python2.4-gnome2* python2.4-gnome2-extras* rhythmbox*
  serpentine* sound-juicer* totem* totem-gstreamer* tsclient* ubuntu-desktop*
  update-manager* update-notifier* vino* yelp*

```

That's a lot of packages to remove.. you sure I should do that?

---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]```
The following packages will be REMOVED:
  bug-buddy* contact-lookup-applet* eog* evince* evolution*
  evolution-exchange* evolution-plugins* evolution-webcal* file-roller*
  firefox-gnome-support* gcalctool* gconf-editor* gdm* gedit* gnome-about*
  gnome-app-install* gnome-applets* gnome-applets-data* gnome-btdownload*
  gnome-control-center* gnome-cups-manager* gnome-games* gnome-media*
  gnome-netstatus-applet* gnome-panel* gnome-pilot* gnome-pilot-conduits*
  gnome-session* gnome-spell* gnome-system-monitor* gnome-system-tools*
  gnome-terminal* gnome-utils* gnome-volume-manager* gnomemeeting* gthumb*
  gtkhtml3.8* gucharmap* hal-device-manager* hwdb-client* libbonoboui2-0*
  libedataserverui1.2-6* libeel2-2* libexchange-storage1.2-0*
  libgnome-desktop-2* libgnome2-perl* libgnomecupsui1.0-1* libgnomeui-0*
  libgtkhtml3.8-15* libgucharmap4* liblpint-bonobo0* libpanel-applet2-0*
  nautilus* nautilus-cd-burner* nautilus-sendto* python-gnome2*
  python-gnome2-extras* python2.4-gnome2* python2.4-gnome2-extras* rhythmbox*
  serpentine* sound-juicer* totem* totem-gstreamer* tsclient* ubuntu-desktop*
  update-manager* update-notifier* vino* yelp*

```

That's a lot of packages to remove.. you sure I should do that?[/QUOTE]
nopes just do the following:
```
sudo apt-get --purge remove liblame0
sudo apt-get -f install
sudo apt-get install liblame0
```

---

### Post by Omning on 2005-11-14
[QUOTE=arnieboy]nopes just do the following:
```
sudo apt-get --purge remove liblame0
sudo apt-get -f install
sudo apt-get install liblame0
```[/QUOTE]

```
sudo apt-get --purge remove liblame0
Reading package lists... Done
Building dependency tree... Done
Package liblame0 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

 sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get install liblame0
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  liblame0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/151kB of archives.
After unpacking 385kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output errorErrors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]```
sudo apt-get --purge remove liblame0
Reading package lists... Done
Building dependency tree... Done
Package liblame0 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

 sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get install liblame0
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  liblame0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/151kB of archives.
After unpacking 385kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output errorErrors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```[/QUOTE]
ok do the following :
```
sudo apt-get --purge remove liblame0
sudo apt-get -f install
sudo apt-get clean
```
**now DONT try and install liblame0 again.** 
just open synaptic and install any other arbitrary package. (a small lib for example).. see how it goes. if everything goes well search for the gstreamer0.8-lame package in synaptic, try and install it and let me know how it goes.

---

### Post by Omning on 2005-11-14
[QUOTE=arnieboy]ok do the following :
```
sudo apt-get --purge remove liblame0
sudo apt-get -f install
sudo apt-get clean
```
**now DONT try and install liblame0 again.** 
just open synaptic and install any other arbitrary package. (a small lib for example).. see how it goes. if everything goes well search for the gstreamer-0.8-lame package in synaptic, try and install it and let me know how it goes.[/QUOTE]

First part, 
```
sudo apt-get --purge remove liblame0
Reading package lists... Done
Building dependency tree... Done
Package liblame0 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


sudo apt-get install liblame0
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  liblame0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/151kB of archives.
After unpacking 385kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output errorErrors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Second part, decided to install apt-doc, figured I could use it right?

```
E: /var/cache/apt/archives/apt-doc_0.6.40.1ubuntu9_all.deb: unable to open files list file for package `libbonoboui2-0'
```

---

### Post by arnieboy on 2005-11-14
read my last post again. I told u **NOT to install liblame0** and u did exactly that.
REDO the instructions on my last post and try not to make mistakes this time.

---

### Post by Omning on 2005-11-14
[QUOTE=arnieboy]read my last post again. I told u **NOT to install liblame0** and u did exactly that.
REDO the instructions on my last post and try not to make mistakes this time.[/QUOTE]

Actually, I didn't, I just copied crap out of the wrong (old) terminal.   

sudo apt-get --purge remove liblame0
Reading package lists... Done
Building dependency tree... Done
Package liblame0 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get clean

Still results in 
E: /var/cache/apt/archives/apt-doc_0.6.40.1ubuntu9_all.deb: unable to open files list file for package `libbonoboui2-0'

---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]Actually, I didn't, I just copied crap out of the wrong (old) terminal.   

sudo apt-get --purge remove liblame0
Reading package lists... Done
Building dependency tree... Done
Package liblame0 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

sudo apt-get clean

Still results in 
E: /var/cache/apt/archives/apt-doc_0.6.40.1ubuntu9_all.deb: unable to open files list file for package `libbonoboui2-0'[/QUOTE]
ok. this means that the **libbonoboui2-0** package is corrupt. thats bad news because its a core lib package and almost whole of gnome depends on it. 
this basically means that u have to remove it and install it again.
u cant do it from inside gnome for obvious reasons. copy the following on a sheet of paper and do them one by one:
press **ctrl-alt-F1**
u will immediately leave gnome and go into console. from there do the following after logging in:
```
sudo /etc/init.d/gdm stop
sudo apt-get --purge remove libbonoboui2-0
sudo apt-get -f install
sudo apt-get clean
sudo apt-get install ubuntu-desktop
```
when u remove **libbonoboui2-0** it will remove most of gnome and all its libs but thats ok since ur home directory will not be harmed and all settings will remain saved. when u install ubuntu-desktop most of these packages will get reinstalled and u shd have a working gnome desktop after that with all the previous settings in place. best of luck!

---

### Post by Omning on 2005-11-14
Tried this, and got an error when doing apt-get --purge remove libbonoboui2-0.  Rebooted into recovery mode, and tried it from there.  Same error 

0 upgraded, 0 newly installed, 70 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 222MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing ubuntu-desktop (--purge):
 unable to open files list file for package `libbonoboui2-0': Input/output errorErrors were encountered while processing:
 ubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by arnieboy on 2005-11-14
well am out of ideas.. u can try the following though i doubt it will help.
if gnome isnt dead yet, go to synaptic and try and **reinstall** the libbonoboui2.0 package.
I think one or more of your core lib packages got badly corrupted because of some screwed up update.
I guess u really need to go for a reinstall .. am sorry abt that.

---

### Post by Omning on 2005-11-14
Thanks for the help.  Was really hoping to avoid the reinstall (just got everything set up and working on 32bit 5.10 a few days ago) but sometimes I guess you have to.

---

### Post by steevc on 2006-01-13
Any progress on this? I've just started getting this error when trying to update anything

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/dash_0.5.2-5_i386.deb (--unpack):
 unable to open files list file for package `dash': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/dash_0.5.2-5_i386.deb
Processing was halted because there were too many errors.
```

---

### Post by arnieboy on 2006-01-13
try the following:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/dash_0.5.2-5_i386.deb
```

---

### Post by steevc on 2006-01-13
[QUOTE=arnieboy]try the following:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/dash_0.5.2-5_i386.deb
```[/QUOTE]

I get the same error :(

---

### Post by steevc on 2006-01-14
Looking in /var/lib/dpkg/info I can see that there is no dash.list file and it looks like there should be. Can I get one from somewhere?

Thanks

---

### Post by steevc on 2006-01-15
Here's the latest update. I managed to build my own dash.list file by getting the file list from dash_0.5.2-5_i386.deb, or rather the data.tar.gz within it. So now I get the same error, but referring to initramfs. I notice that has a different set of files in /var/lib/dpkg/info. It has a .conffiles and no .conf, .list, .prerm or .templates compared with what dash had.

Is there some utility that can re-populate the files in /var/lib/dpkg/info based on the deb files?

I suspect I might fix initramfs and then be confronted by an error on a different package. Trying to fix them manually is likely to result in mistakes.

---

### Post by steevc on 2006-01-16
I've fixed it! It seems that my disk was corrupted. I managed to run fsck and now it seems to be okay. apt-get still complains about some list files being missing, but can cope with that.

This might be useful information to someone else.

---

