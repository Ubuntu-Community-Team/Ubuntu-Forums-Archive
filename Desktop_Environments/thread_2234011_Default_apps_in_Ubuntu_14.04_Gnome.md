---
title: "Default apps in Ubuntu 14.04 Gnome"
date: 2014-07-11
forum: Desktop Environments
---

### Post by RogerDavis on 2014-07-11
I want to change some default apps to something other than is listed as options.  

However, there is no "other" or "browse" option, just the list that doesn't include my app.

I don't know if this is due to my use of Gnome or not.

How do I either add my app to the list, or input it's name and location, or ???

---

### Post by monkeybrain20122 on 2014-07-11
How did you install these applications? If you install them from third party you may need to make your own .desktop files. For an application to show up in your system as a launcher icon (doesn't matter which DE) there has to be a .desktop file, usually in /usr/share/applications if you install from the repository or a ppa.  If not you may need to make one yourself and put it in .local/share/applications. You can go to /usr/share/applications and open one with an editor to check out the template.

---

### Post by RogerDavis on 2014-07-12
This is how I installed it, I think... it's been a few days.
------------------------
$ echo -e "deb [http://downloads.sourceforge.net/projec](http://downloads.sourceforge.net/projec) ... ozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
$ sudo apt-get update
$ sudo apt-get install seamonkey-mozilla-build
---------------------

Does this indicate that I need to make my own .desktop file?

And all I need to do is to drop it into  .local/share/applications  ?

Thanks!

---

### Post by monkeybrain20122 on 2014-07-12
I don't know about this one, but do you find a .desktop file like moziila-seamonkey.desktop, seamonket.desktop, mozilla-build-seamonkey.desktop or some variations in /usr/share/applications?

(either open the file manager, click on "computer" and navigate to /usr/share/applications or in the terminal type

```
cd /usr/share/applications
ls
```

and check the output.)

---

### Post by kansasnoob on 2014-07-12
Are you using GNOME Shell?

If so you should just be able to search for seamonkey in the dash and then pin it to the launcher if you wish.

---

### Post by RogerDavis on 2014-07-12
I am using Gnome.  

I'm away from the computer until Monday, I can try that then.

I think I understand that I can drag the SeaMonkey icon to the place where the list shows, and it will be added, then I can select it as the default browser?  If I'm wrong, can you be more specific about exactly how to do this?

Thanks!

---

### Post by kansasnoob on 2014-07-12
> **RogerDavis said:**
> **[COLOR="#FF0000"]I am using Gnome[/COLOR]**.  

I'm away from the computer until Monday, I can try that then.

I think I understand that I can drag the SeaMonkey icon to the place where the list shows, and it will be added, then I can select it as the default browser?  If I'm wrong, can you be more specific about exactly how to do this?

Thanks!

But in 14.04 there's the potential of 4 different GNOME sessions; GNOME Shell, GNOME Classic, GNOME Flashback (Metacity), or GNOME Flashback (Compiz). So we need to know what Gnome session you're actually running :)

---

### Post by RogerDavis on 2014-07-12
It's Flashback Metacity, I'm pretty sure.  If changes are persistent, I can log into any of them to accomplish what I need.

Thanks!

---

### Post by kansasnoob on 2014-07-13
Sorry, I was confused until I saw your other thread:

[http://ubuntuforums.org/showthread.php?t=2233684](http://ubuntuforums.org/showthread.php?t=2233684)

If you ask [here]("http://ubuntuforums.org/forumdisplay.php?f=251") *nanotube* may have an answer for you. He's helped me several times.

---

