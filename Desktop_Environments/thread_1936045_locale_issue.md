---
title: "locale issue"
date: 2012-03-05
forum: Desktop Environments
---

### Post by Cyctemic on 2012-03-05
Hi everyone,

I've got a problem with the locale definitions. I use git and sometimes have these warnings :
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_MESSAGES = "en_US.UTF-8",
    LC_COLLATE = "en_US.UTF-8",
    LC_CTYPE = "en_US.UTF-8",
    LANG = "fr_FR.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```So I looked over the web... Found some threads about reinstalling the locales :
```
sudo apt-get install --reinstall locales
```
or re-generate some compiled locales :
```
sudo apt-get install language-pack-en-base
export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
sudo locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales
```None of these worked for me. If you have any other idea it would help me a lot. I use git and repo a lot, on a lot of git projects, and these warning are coming all the time...

Here are some config infos that might help :
```
**arnaud~$ locale**
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE=en_US.UTF-8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE=en_US.UTF-8
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES=en_US.UTF-8
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
``````
**arnaud~$ cat /etc/environment**
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en"
LC_MESSAGES="en_US.UTF-8"
LC_CTYPE="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
``````
**arnaud~$ ll /usr/lib/locale/**
total 8680
drwxr-xr-x   3 root root    4096 2011-10-12 16:32 ./
drwxr-xr-x 230 root root   69632 2012-03-05 15:48 ../
drwxr-xr-x   3 root root    4096 2011-10-12 16:27 C.UTF-8/
-rw-r--r--   1 root root 8789520 2012-03-05 17:53 locale-archive
```

---

### Post by diesal3 on 2012-04-30
Please tell me that you are using Unity on Precise, because I have this after logging onto Unity. I found that the first block of code would appear with apt-get after logging into Unity, and consistently appear afterwards no matter which DE I used (and I mean, I log in and then it carries on no matter what until I deal with it).

This seems to make it so that the whole system doesn't run properly for me (making dpkg stop midway and making Ubuntu Tweak unable to run amongst other things).

A fix seems to be to not use Unity, and run locale-gen (required locales here) and never touch Unity, or that's what I have done. I am now using GNOME3 Classic with no problems.

@Cyctemic I take it that you tried to use these:

[http://ubuntuforums.org/showthread.php?t=1346581&highlight=unset+locale](http://ubuntuforums.org/showthread.php?t=1346581&highlight=unset+locale)
[http://www.linuxquestions.org/questions/showthread.php?p=3540541#post3540541](http://www.linuxquestions.org/questions/showthread.php?p=3540541#post3540541)

I also reported my problem as a bug here:

[https://bugs.launchpad.net/unity/+bug/991914](https://bugs.launchpad.net/unity/+bug/991914)

---

