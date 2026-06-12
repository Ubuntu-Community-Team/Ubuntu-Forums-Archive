---
title: "Mouse Cursor size will not increase"
date: 2018-07-11
forum: Desktop Environments
---

### Post by borg101 on 2018-07-11
I installed 18.04 LTS yesterday.  I installed Arc Dark theme today and went to increase my mouse pointer size as I'm on a 4k TV.  I changed it in dconf editor not knowing an option was added in universal access.  I rebooted, that didn't work.  I did some googling and found that there was an option in universal access.  That didn't work.  I then went back into dconf editor and set cursor-size and cursor-theme to default and rebooted.  I went back to universal access and tried increasing the size...nothing.  Then I went to command line and did "sudo update-alternatives --config x-cursor-theme" to make sure it was set to default.  It indeed was.  I am unsure on how to further proceed.  I have been at this for well over 5 hours now and am unsure how to proceed.  Any advice?  I did find other threads on this but they were all outdated or the current ones mentioned the solutions above, none of which worked.  I do apologize if I am double posting.

---

### Post by #&amp;thj^% on 2018-07-11
So this dose not work any more?
```
dconf write /org/gnome/desktop/interface/cursor-size 48
```

---

### Post by borg101 on 2018-07-11
> **1fallen said:**
> So this dose not work any more?
```
dconf write /org/gnome/desktop/interface/cursor-size 48
```
Nope. It did change the cursor size in dconf though....so it's writing it.  I just don't see any change.

Also, perhaps it's worth mentioning that the login screen cursor size is much smaller than my desktop cursor size.  My current desktop cursor size looks like the "smallest" option in universal access but my login screen cursor size is significantly smaller.

---

### Post by #&amp;thj^% on 2018-07-11
Well I just logged into Ubuntu and it worked for me????
```
lsb_release -a && apt policy nautilus
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic
nautilus:
  Installed: 1:3.26.3-0ubuntu4
  Candidate: 1:3.26.3-0ubuntu4
  Version table:
 *** 1:3.26.3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```
There has been a few weird results with current iso installer as I have just now seen yours is also recently downloaded is this correct?

---

### Post by borg101 on 2018-07-11
> **1fallen said:**
> Well I just logged into Ubuntu and it worked for me????
```
lsb_release -a && apt policy nautilus
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
nautilus:
  Installed: 1:3.26.3-0ubuntu4
  Candidate: 1:3.26.3-0ubuntu4
  Version table:
 *** 1:3.26.3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```

Bully for you?!!? lol.  It's not working for me though.  [ATTACH=CONFIG]280358[/ATTACH][ATTACH=CONFIG]280359[/ATTACH][ATTACH=CONFIG]280360[/ATTACH]

---

### Post by #&amp;thj^% on 2018-07-11
> **borg101 said:**
> Bully for you?!!? lol. 
I'll take that as a friendly gesture.
Good Luck

---

### Post by borg101 on 2018-07-11
> **1fallen said:**
> I'll take that as a friendly gesture.
Good Luck
Lol....it basically means "And?  Good for you." I meant no offense by it lol.  It's just that because something is working for one or many doesn't necessarily means it works for all.  Nothing I've tried has worked so far and I'm at a complete loss.  I'm not a noob to Ubuntu per se....my flavor is generally Mint, but there are a lot more HiDPI scaling issues with Mint 19 rather than Ubuntu 18.04 LTS.  I just realized the default screengrab app for Ubuntu doesn't include the cursor.

---

### Post by #&amp;thj^% on 2018-07-11
LOL I knew the meaning>>>And I'm not easily offended. LOL
I just get curious as a tester as to why something works for one or many and not for one or a few handful.
I asked if this was a recently downloaded .iso as there has been some strange abnormal artifacts being reported with newly installed systems.

---

### Post by borg101 on 2018-07-11
I downloaded the ISO last night.  I haven't installed much as I've been focused on getting the "look and feel" right.  I haven't changed many settings though, beyond switching the theme to Arc Dark.

---

### Post by ajgreeny on 2018-07-11
The problem may be related to the theme you have chosen as not all themes have cursor icons of all sizes; perhaps you need to search the theme folder to see what size options are present.

I had the same problem in an install on an HD monitor where only a very limited set of size options worked and all other chosen sizes did not make any difference to cursor size.  See the thread I started at [https://ubuntuforums.org/showthread.php?t=2392546](https://ubuntuforums.org/showthread.php?t=2392546)

---

### Post by #&amp;thj^% on 2018-07-11
> **ajgreeny said:**
> The problem may be related to the theme you have chosen as not all themes have cursor icons of all sizes; perhaps you need to search the theme folder to see what size options are present.

I had the same problem in an install on an HD monitor where only a very limited set of size options worked and all other chosen sizes did not make any difference to cursor size.  See the thread I started at [https://ubuntuforums.org/showthread.php?t=2392546](https://ubuntuforums.org/showthread.php?t=2392546)

Out of curiosity again, I installed the Ark-Dark Theme and adjusted the mouse size via: "dconf write /org/gnome/desktop/interface/cursor-size 48" and the changes work here. (Also with a logout and login )
I'm not sure what more I can add to help the OP.

---

### Post by Dennis N on 2018-07-11
What cursor theme are you using? You can't change size in Universal Access settings unless cursor is resizable. Not all cursor themes are resizable. The DMZ cursors are resizable (DMZ-White, DMZ-Black).  In Universal Access settings, you can also set Zoom and make _everything_ bigger. Different cursor themes are chosen in Tweaks.

---

### Post by borg101 on 2018-07-11
> **ajgreeny said:**
> The problem may be related to the theme you have chosen as not all themes have cursor icons of all sizes; perhaps you need to search the theme folder to see what size options are present.

I had the same problem in an install on an HD monitor where only a very limited set of size options worked and all other chosen sizes did not make any difference to cursor size.  See the thread I started at [https://ubuntuforums.org/showthread.php?t=2392546](https://ubuntuforums.org/showthread.php?t=2392546)

I think you were right.  I was exploring around in the themes and couldn't find anything.  So I thought what if I tried a different session.  Sure enough, I logged into communitytheme, which I had previously installed but not used, and it worked like a charm.  It was already set right and everything.  Thank you so much!

---

### Post by ajgreeny on 2018-07-12
My pleasure.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by l6griffin on 2018-10-22
I have a similar problem(s), the cursor size will change to larger and most the time it will show correctly on the desktop. In an application it can be default cursor, or a capital 'I' hard to see. I think someone has their coding wrong, and about to file a bug.

---

### Post by coffeecat on 2018-10-22
@l6griffin, if you need help, please start your own thread. The OP has not been back since a little after they declared their problem fixed.

Thread closed.

---

