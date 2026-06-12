---
title: "Messed up LOCALES (Caused by new libc6?)"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Falcorian on 2006-09-10
While trying to install *libmono1.0-cil* I tried to install libc6 again from [http://packages.ubuntu.com/edgy/base/libc6](http://packages.ubuntu.com/edgy/base/libc6).

However, it did not install correctly, and asked me to do a apt-get  install -f. I did this (I can't remember all the packages it mentioned), but afterwards I've been getting the following errors when attempting to run various things from the console (firefox, nautilus so far. Haven't tried any others):

```
(nautilus:13680): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nautilus:13680): Gdk-WARNING **: locale not supported by C library
```

I've done some googling and none of the "solutions" I've seen recommened work. sudo dpkg-reconfigure locales for example produces:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'America/Los_Angeles'.
Local time is now:      Sun Sep 10 18:46:06 PDT 2006.
Universal Time is now:  Mon Sep 11 01:46:06 UTC 2006.
Run 'tzconfig' if you wish to change it.
```

Any ideas on how to fix this?

Thanks in Advance.

EDIT: This may be the wrong subforum... If so, could someone put it where it belongs? I'm new here... ;)

---

### Post by Anduu on 2006-09-10
Are you actually trying to upgrade to Edgy or just messing around tryng to update some Dappers stuff?

If you are trying to upgrade you should post here [http://www.ubuntuforums.org/forumdisplay.php?f=144](http://www.ubuntuforums.org/forumdisplay.php?f=144)

Otherwise you are biting off more than you can chew.Dapper and Edgy stuff should ***neve***r be mixed.

---

### Post by Falcorian on 2006-09-10
I was not attempting to upgrade, I just grabbed the wrong packet it seems.


It's the undoing that I could use assitence with, got any ideas on that? :)

---

### Post by Anduu on 2006-09-11
First make sure you have only Dapper repos enabled and do an apt-get update/upgrade and see what happens.

---

### Post by Falcorian on 2006-09-11
> **Anduu said:**
> First make sure you have only Dapper repos enabled and do an apt-get update/upgrade and see what happens.

Ok, I'm using the following Repos:
```

##comments (##) in front of any line to remove it from being checked.

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

##Amarok
##deb http://kubuntu.org/packages/amarok-latest dapper main
deb http://imbrandon.com/packages dapper amarok
deb-src http://imbrandon.com/packages dapper amarok
```

update followed by upgrade yields the following:
```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by erik plaggenmars on 2006-09-11
i'm currently havind the same problem.... My wifi card doesnt work... so i went on windows, tried to download the packages, back to linux, dpkg -i the packages.... But it ****** it all up and i don't know how to fix it.... Stupid how one handle can **** up your whole system :(

---

### Post by chescobar on 2006-09-24
I have the same problem now, i upgrade libc6 to install the new version of qucs and  the same error with locale:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "es_Co:es",
        LC_ALL = (unset),
        LANG = "es_CO.UTF-8"
    are supported and installed on your system.
:(

---

### Post by Anduu on 2006-09-24
Once you are certain you have only Dapper repos installed fire up Synaptic and find libc6.Then select Package from the menu and click force version.It should give you the option of getting the old version back.

2.3.6-0ubuntu20

---

### Post by Falcorian on 2006-09-25
Thanks for the reply but I fixed it finally by reinstalling my root partition, which let me repartition my drives to cut out window's space.


Thanks anyway.

---

