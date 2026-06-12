---
title: "unable to install any packages in command line or thru synaptic.,getting same error"
date: 2013-03-05
forum: Desktop Environments
---

### Post by khoshalar on 2013-03-05
unable to install any packages in command line or thru synaptic.,getting same error

I am logged in as root, using ubuntu 10.10 on desktop.,I was trying to configure LAMP server and I ended up deleting some files alongway.,and now I am unable to install any packages thru CLI or GUI.,the error i am getting when i try on CLI or GUI is --

E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

Also tried with: apt-get install tasksel && tasksel install  lamp-server and it gives out error as : tasksel: aptitude failed (100)

Please suggest on what has to be done.,

Thanks in advance

---

### Post by oldfred on 2013-03-05
You will have to do a new install. It has expired.
 Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases")
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You need to backup /home and a list of installed applications. If you have a separate /home, just make a list of installed apps and reinstall.

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

   1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications

---

### Post by khoshalar on 2013-03-05
I am newbie nd am sorry for asking this --
 but apart from doing a new install as stated above --is there any way this issue can be fixed -- bcuz this is my work lapi and I am not clear about the new installation.please suggest

---

### Post by schragge on 2013-03-05
Do what the error message suggests, i.e. deactivate immediate configuration for install of *libattr1*.
```

sudo apt-get -o [COLOR=#000000]APT::Immediate-Configure=false [/COLOR]install libattr1

```

---

### Post by oldfred on 2013-03-05
apt-get anything will not work, it obsolete. 

Someone did post that there are archives somewhere and with some effort you can connect to those just to add a package, but nothing is maintained. You would have to search forum for support of versions that are past their support by dates.

---

### Post by schragge on 2013-03-05
Well, the repositories are available at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

