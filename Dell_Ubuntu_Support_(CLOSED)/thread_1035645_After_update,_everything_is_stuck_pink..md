---
title: "After update, everything is stuck pink."
date: 2009-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pacman29 on 2009-01-09
I just ran the system update and rebooted my Dell Mini 9. Now all of my windows are pink. When I change the colors in appearance preferences, it only changes to different shades of pink. Has anybody else had this problem?

---

### Post by armandh on 2009-01-10
mini9 with fully updated 8.10 no such problem

---

### Post by yakker.yak on 2009-01-10
Sounds to me like a hardware/bios issue.

Did you ever upgrade the Bios from the default?

---

### Post by ugm6hr on 2009-01-10
No.

Mine works fine.  Symlinked "~/.mozilla/firefox" to "~/.mozilla/web browser" to maintain my FF profile.

---

### Post by Servetus on 2009-01-11
I've got the same thing. Also, it looks like Yahoo crapped all over the "Web Browser". Home page, toolbar and default search engine have all had their settings reset to Yahoo services. 

The most annoying bit is what you describe, the appearance settings won't let you change the Window Border color from "Yahoo Red" in an apparent attempt to brand all of our Linux machines.

I'm going to switch my apt repository from Dell's Yahoo sellout crapfest.

---

### Post by ugm6hr on 2009-01-11
I am still using my default install, with the standard dell / canonical repo.  I didn't have any of these pink / red issues.

Perhaps just try removing the yahoo bar:
```
sudo apt-get remove yahoo-toolbar-extension
```

As described elsewhere, your bookmarks / FF settings will have changed: [http://ubuntuforums.org/showthread.php?t=1036290](http://ubuntuforums.org/showthread.php?t=1036290)

---

### Post by Servetus on 2009-01-11
> I didn't have any of these pink / red issues.

It depends on what Appearance Theme that you are using but all of the standard themes such as "Glossy" and "Clearlooks" are now permanently red.

---

### Post by ugm6hr on 2009-01-11
> **Servetus said:**
> It depends on what Appearance Theme that you are using but all of the standard themes such as "Glossy" and "Clearlooks" are now permanently red.

My Mini defaulted to Human - which behaves just fine.

---

### Post by klange on 2009-01-11
It's more of a dark red, but "same here". Window border colors are stuck red, among other issues (anyone else getting really bad 2d performance?)

---

### Post by utnubu777 on 2009-01-11
Hi, 
experiencing the same issue. Dell mini9 - running the ubuntu like it came out of the box. I ran the update today. After the reboot all my firefox settings were reset and my bookmarks are gone, too! All windows title bars are Pink. I tried to change the color but was not successful. It stays pink. And I hate pink! 
I think I'll need to get away from the Dell/Yahoo branded Ubuntu.

---

### Post by ugm6hr on 2009-01-12
> **utnubu777 said:**
> After the reboot all my firefox settings were reset and my bookmarks are gone, too!

[http://ubuntuforums.org/showthread.php?t=1036290](http://ubuntuforums.org/showthread.php?t=1036290)

---

### Post by ArKay on 2009-01-12
Running 8.10 and did the update yesterday. 130 some odd updates actually. No problems here. (yet)

---

### Post by njpatel on 2009-01-12
Hey guys,

This is a hardy gcc + metacity problem. Some of the compiler optimisations do funny things and cause this weird issue. Our metacity has a patch to fix this problem, but it seems that you do not have that version.

Can you please do a `apt-cache policy metacity` and paste the output.

Thanks,

Neil

---

### Post by klange on 2009-01-12
> **ArKay said:**
> Running 8.10 and did the update yesterday. 130 some odd updates actually. No problems here. (yet)

This is an issue with the updates for the Dell Hardy lpia-optimized distro.

> **njpatel said:**
> Hey guys,

This is a hardy gcc + metacity problem. Some of the compiler optimisations do funny things and cause this weird issue. Our metacity has a patch to fix this problem, but it seems that you do not have that version.

Can you please do a `apt-cache policy metacity` and paste the output.

Thanks,

Neil

It's not an issue with Metacity, it's a gnome-settings issue, as it also happens with gtk-window-decorator (our [compiz's] GTK decorator).

The updates to the Dell distro broke quite a bit, it seems. Might be time to finally move to Intrepid-lpia.

---

### Post by njpatel on 2009-01-12
> **WindowsSucks said:**
> 
It's not an issue with Metacity, it's a gnome-settings issue, as it also happens with gtk-window-decorator (our [compiz's] GTK decorator).

The updates to the Dell distro broke quite a bit, it seems. Might be time to finally move to Intrepid-lpia.

This is an issue with metacity & gcc, specifically libmetacity (which gtk-window-decorator uses to draw afiak). The gnome bug can be found at [1]. The issue seems to be fixed with the latest stable gcc.

As mentioned, we need to determine which metacity the OP has installed and hopefully we can figure out the way for them to grab the updates.

Thanks,

Neil

[1] [http://bugzilla.gnome.org/show_bug.cgi?id=478886](http://bugzilla.gnome.org/show_bug.cgi?id=478886)

---

### Post by Servetus on 2009-01-12
> Can you please do a `apt-cache policy metacity` and paste the output.

```

metacity:
  Installed: 1:2.22.0-0ubuntu4.netbook2
  Candidate: 1:2.22.0-0ubuntu4.netbook2
  Version table:
 *** 1:2.22.0-0ubuntu4.netbook2 0
        500 http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
        100 /var/lib/dpkg/status
     1:2.22.0-0ubuntu4 0
        500 http://dell-mini.archive.canonical.com hardy/main Packages
```

Thanks Neil!

---

### Post by ugm6hr on 2009-01-12
> Can you please do a `apt-cache policy metacity` and paste the output. 

I don't think it's that.

Mine looks identical, but I have no problems.

---

### Post by njpatel on 2009-01-12
> **ugm6hr said:**
> I don't think it's that.

Mine looks identical, but I have no problems.

Agreed, this is the first time I've seen it since integrating that patch.

/me bows down to WindowsSucks and checks gnome-settings again.

I'll let you know if I find anything.

Thanks,

Neil

---

### Post by pacman29 on 2009-01-12
Hey, I'm glad to see it's not just me. Sorry it took so long to get back. Here's the paste 
metacity:
  Installed: 1:2.22.0-0ubuntu4.netbook2
  Candidate: 1:2.22.0-0ubuntu4.netbook2
  Version table:
 *** 1:2.22.0-0ubuntu4.netbook2 0
        500 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
        100 /var/lib/dpkg/status
     1:2.22.0-0ubuntu4 0
        500 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages

Also, I'm not sure it was the Yahoo toolbar because that was the first thing to go when I got the computer. 
As mentioned previously, the problem only occurs when using the "non-human" versions of Clearlooks, Glider and Glossy. I just switched to Mist in the meantime.

---

### Post by ugm6hr on 2009-01-12
> **pacman29 said:**
> As mentioned previously, the problem only occurs when using the "non-human" versions of Clearlooks, Glider and Glossy. I just switched to Mist in the meantime.

I think the theme must have been updated.  I have checked my system - and those themes are pink on mine too (I have used Human since I got mine).

I would suggest just changing Theme to Human for now:
System -> Preferences -> Appearance
Select "Theme" tab
Select "Human" (or any of the Human-x) themes
Close

---

