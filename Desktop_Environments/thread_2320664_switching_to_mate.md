---
title: "switching to mate"
date: 2016-04-16
forum: Desktop Environments
---

### Post by decrepit on 2016-04-16
before I upgrade to 16.04 I thought I'd have a look at mate, I've downloaded "mate desktop" from the repository’s, but how do I get into it?????
Do I need to download a desktop switcher as well, or more mate files?

---

### Post by grahammechanical on 2016-04-16
At the login screen above the password panel & on the right there should now be a Ubuntu icon. Click on it and a drop down menu should appear where you can select mate as the desktop session. It will become the default until you select Ubuntu in the same way.

Regards.

---

### Post by decrepit on 2016-04-16
Thanks Graham, I was looking for something like that, and have just rebooted to check again and it's still not there.
That's why I wondered if I need to download more stuff.
It only installed "mate-desktop", "mate-desktop-common" and "libmate-desktop-2-17" 
All of them are only described as librarys.

---

### Post by howefield on 2016-04-16
If you are installing the Mate desktop into your existing install, I believe the minimum that you would need is 

```
sudo apt-get install mate-desktop-environment-core
```

You will get progressively more of the environment if you install one or other of...

```
sudo apt-get install mate-desktop-environment
```
```
sudo apt-get install mate-desktop-environment-extras
```

I think to get the full Ubuntu Mate environment would need..
```
sudo apt-get install ubuntu-mate-core ubuntu-mate-desktop
```

---

### Post by decrepit on 2016-04-16
Thanks howefield, I think I see my problem now, the mirror I'm using doesn't seem to have all the mate stuff on it. I'll try another mirror tomorrow.

---

### Post by howefield on 2016-04-16
What's you starting point, which version of Ubuntu are you currently using ?

---

### Post by oldrocker99 on 2016-04-16
> **decrepit said:**
> Thanks howefield, I think I see my problem now, the mirror I'm using doesn't seem to have all the mate stuff on it. I'll try another mirror tomorrow.

Believe it or not, I've had great results from the TripAdvisor mirror, and it's complete.

I'd advise getting Ubuntu MATE, which has all the MATE goodness with no Unity. I'm running 16.04 beta 2, and it's nice and stable. Or you can wait a week or so for the official release.

---

### Post by decrepit on 2016-04-17
> **howefield said:**
> What's you starting point, which version of Ubuntu are you currently using ?

I'm running 14.04LTS, after almost 2 years I'm still not really comfortable with unity and it's dashpot. I used Gnome 2 since Fedora Core started, guess I'm too long in the tooth to change easily.
I'm using The Australian iinet mirror as most Linux stuff is a free download, but last night when I ran your script I got a message back saying packages not found.

So my next move will be an examination of other mirrors.

---

### Post by howefield on 2016-04-17
> **decrepit said:**
> I'm running 14.04LTS, after almost 2 years I'm still not really comfortable with unity and it's dashpot. I used Gnome 2 since Fedora Core started, guess I'm too long in the tooth to change easily.
I'm using The Australian iinet mirror as most Linux stuff is a free download, but last night when I ran your script I got a message back saying packages not found.

So my next move will be an examination of other mirrors.

You'd probably find that it isn't a mirror issue, many of the above packages wouldn't be available in any Trusty repository. There should be ppa that you can use, however I'd suggest downloading the current Ubuntu Mate daily and running from a Live DVD / USB. After all, you only want to have a look at it and get a feel for what it is about :)

---

### Post by decrepit on 2016-04-17
Thanks howefield, in that case I'll wait until 16.04 is fully released and download a DVD

---

