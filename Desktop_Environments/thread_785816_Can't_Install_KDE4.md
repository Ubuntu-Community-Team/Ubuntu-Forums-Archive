---
title: "Can't Install KDE4"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Bobbins069 on 2008-05-07
my sudo apt-get install kubuntu-kde4-desktop command is not working. It tells me that the packages can't be found. I am running on Hardy as well. Any suggestions?

---

### Post by smartboyathome on 2008-05-07
Try reloading by running sudo apt-get update.

---

### Post by Bobbins069 on 2008-05-07
I tried that a bunch of times, still same error

---

### Post by c4v3m4n on 2008-05-07
I didn't think KDE4 was done yet.  Isn't it still in deveolopement?  Most people i've seen with it go back to kde3 until it's done.

---

### Post by skyjacker on 2008-05-07
> **Bobbins069 said:**
> my sudo apt-get install kubuntu-kde4-desktop command is not working. It tells me that the packages can't be found. I am running on Hardy as well. Any suggestions?Try this.... Go to and click on the kmenu icon. Choose "system,adept manager, and when it loads put in your password & search for kde4-core. Right click on the line for kde4-core and choose request install. Then click on "apply at the top. The program will then install. You will now have the choice to load kde3 or kde4 in the menu when you first log into kde (click on the icon in the lower right that looks like a page before you enter your password). Good luck. P.S. I have had kde3 since it came out. I tried kde4 and didn't like it because it still has bugs.

---

### Post by Zorael on 2008-05-07
> KDE 4.0.4 Released

KDE 4.0.4 has been released and packages are available for Kubuntu 8.04. They install to /usr/lib/kde4 and can be installed alongside your existing KDE 3.

Instructions:

The packages are in hardy-backports, available from Adept Manager when you choose Unsupported Updates from the Updates tab of Manage Repositories, kubuntu-kde4-desktop and do a full upgrade.

Thanks to nixternal and stdin for their help with these packages.
[http://kubuntu.org/announcements/kde-4.0.4.php](http://kubuntu.org/announcements/kde-4.0.4.php)


Make sure you have said repository enabled.

edit: I'm actually not sure the new version is up yet, I can't find it on packages.ubuntu.com. I have it installed but apt-cache policy says it's the version from universe.
```
zorael@sunspire:~$ apt-cache policy kubuntu-kde4-desktop
kubuntu-kde4-desktop:
  Installed: 0.14
  Candidate: 0.14
  Version table:
 *** 0.14 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by stephenjbarr on 2008-05-07
I went through the steps outlined on kubuntu.com (add the backports repository, use adept-manager, etc.) and I have kde4 installing as I type. Well, the packages are downloading anyway. Things seem to be going smoothly so far. 

-stephen

---

### Post by Zorael on 2008-05-08
Are you sure it's the 4.04 version? I mean, KDE4 has been available since day one of Hardy (well, likely day -n in the development process), just not the latest version.

---

### Post by Bobbins069 on 2008-05-08
I think I am just going to reinstall Kubuntu 7.10 then make sure i have all my repositories, then i will upgrade to 8.04 and work from there. Also is it still possible to install Gnome after you have kde4?

---

### Post by Xiong Chiamiov on 2008-05-08
Yes, you can have GNOME and KDE4, just as you can have KDE3.5 and KDE4 both installed.  Running a
```

sudo dpkg-reconfigure gdm

```
will allow you to choose which display manager is the default (for the login screen), and when logging in you can choose which *dm you'd prefer to use.

---

