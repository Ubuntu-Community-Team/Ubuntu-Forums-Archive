---
title: "How to make kmail open links in Firefox?"
date: 2009-06-08
forum: General Help
---

### Post by owkaye on 2009-06-08
So far I haven't found a single solution to the problem of making kmail open links in Firefox in Ubuntu 9.04.  Does someone here actually know how to do this?

---

### Post by CanonKen on 2009-06-08
> **owkaye said:**
> So far I haven't found a single solution to the problem of making kmail open links in Firefox in Ubuntu 9.04.  Does someone here actually know how to do this?
Is there no option in System>Preferences>Preferred Applications?

---

### Post by owkaye on 2009-08-17
> **CanonKen said:**
> Is there no option in System>Preferences>Preferred Applications?

No there is not, and after more than two months I still do not have a solution.  All I want to do is make kmail open links in Firefox WITHOUT having File Browser open files in Firefox too.

Is there a way to do this?

---

### Post by gastly on 2009-08-17
Try this:
System Settings->Default Applications->Web Browser
and change it to 'firefox' :)

---

### Post by owkaye on 2009-08-17
> **gastly said:**
> Try this:
System Settings->Default Applications->Web Browser
and change it to 'firefox' :)

It's already set to Firefox.  Anyone else?

---

### Post by oldos2er on 2009-08-17
Are you running Kmail under Gnome or KDE?

---

### Post by Tipped OuT on 2009-08-17
> **owkaye said:**
> It's already set to Firefox.  Anyone else?

I guess it's just the way KDE is integrated to use "K" applications. :|

---

### Post by philinux on 2009-08-17
[http://www.google.co.uk/search?q=make+kmail+open+links+in+Firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=make+kmail+open+links+in+Firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Second hit looks very promising.

[http://ubuntuforums.org/showthread.php?t=60610](http://ubuntuforums.org/showthread.php?t=60610)

---

### Post by owkaye on 2009-08-17
oldos2er,

Thanks for helping me in the other thread.  I'm runing kmail in gnome so here is the correct solution for anyone else who has this problem and finds this thread:

1- Install kdeartwork and systemsettings.

2- Go to Applications > System Tools > Default Applications > Web Browser > Default Component then make this setting:  "Open http and https URLS in the following browser: Firefox"

That's all there is to it.

:)

---

### Post by douglas_slac on 2009-09-09
Ok, well I had problems... actually when I first install kmail it seemed to work fine, and I could get links to open in Firefox, so all was good.

Then I installed elinks because I wanted a console browser, and http links in kmail stopped working.  This was because it was now trying to use elinks as the default browser, and trying to use konsole as the default terminal.  So, I installed konsole, but using elinks as the default browser wasn't acceptable.

The above notes didn't really help or work for me.  So, what seems to work for me so far was:

1. install kdeartwork, systemsettings and konqueror.
2. Now run Applications -> System Tools -> System Settings
3. Now click Personal -> Default Applications -> Web Browser
4. Here you can choose run in browser, and fill in "firefox".

Also I was having problems with screen updates in kmail, and here under web browser, you can also choose the window manager.  If you clink on window manager, it shows that kmail was using the default kwin.  You can choose here to switch to Metacity (Gnome).  Switching to this, with the default use of Gnome in Ubuntu, helped in the use of kmail, and the window updates work correctly now.

---

### Post by OMR on 2009-10-10
> **owkaye said:**
> oldos2er,

Thanks for helping me in the other thread.  I'm runing kmail in gnome so here is the correct solution for anyone else who has this problem and finds this thread:

1- Install kdeartwork and systemsettings.

2- Go to Applications > System Tools > Default Applications > Web Browser > Default Component then make this setting:  "Open http and https URLS in the following browser: Firefox"

That's all there is to it.

:)

THANK YOU for this solution it works for me, I hate Konqueror, hopefully this helps others as I also run Kmail in Gnome and this problem was driving me CRAZY Thanks at least for ME this problem is solved.

---

### Post by freacert on 2010-01-24
Installed Wine today, and now Kmail wants to open url with winebrowser...:confused:
Sending the url to some var place, opens up firefox (before it was Opera), and takes the main part of the url away and puts a file/// instead... 

> **douglas_slac said:**
> 
1. install kdeartwork, systemsettings and konqueror.
2. Now run Applications -> System Tools -> System Settings
3. Now click Personal -> Default Applications -> Web Browser
4. Here you can choose run in browser, and fill in "firefox".



i will try, but a lot of work of something simple as assigning your default browser....

ubuntu 9.10 wine 1.1.31-0ubuntu3 (and also wine1.2-gecko, maybe the clue is there?), will check some things out when wine has stopped working...

---

### Post by freacert on 2010-10-08
after fresh install had to fix it again. 

No need to download kdeartwork, only systemsettings is enough. Run it in a terminal, just type systemsettings as it will not appear in aplications, and follow the above instructions. Everything fine and back to normal :)

---

### Post by AlanB66 on 2011-06-24
> **freacert said:**
> after fresh install had to fix it again. 

No need to download kdeartwork, only systemsettings is enough. Run it in a terminal, just type systemsettings as it will not appear in aplications, and follow the above instructions. Everything fine and back to normal :)

thank you!!!!!

---

