---
title: "Nothing happens with Compiz in Gutsy."
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by viergeame on 2007-11-09
I recently upgraded to Gutsy from Feisty.  I had Compiz-Fusion running perfectly on Feisty, but now that I have upgraded Compiz doesn't seem to do anything.  Since I used it before I upgraded, I already have the settings manager, and I looked through it and all the settings are just as they were before I upgraded.  I looked on the system monitor though, and it doesn't show Compiz as running.  I thought it was supposed to run on startup?  

Also, I'm not sure if this is related, but when I open the system > preferences > appearance menu, I can't do anything in it.  If I click on any of the tabs or anything in the window nothing happens.  I'm not sure if the window is frozen or if it's something else causing it.  This happens every time I open the appearance window, but not with any others.

---

### Post by Zorael on 2007-11-09
Did you use Treviños eyecandy repository in 7.04? Its Compiz is "not compatible" with the one in Gutsy's repositories. So you'll want to remove it from your software sources, completely remove everything compiz-related in Synaptic, and then reinstall.

```
$ sudo apt-get remove compiz* libcompiz* libdeco* emerald* libemerald*
```
...that'd be the terminal way.

---

### Post by viergeame on 2007-11-09
I didn't use Trevinos repositories.  It sounded like it was giving an awful lot of people problems so I used the amaranth (sp?) one.  Am I still going to need to reinstall?

---

### Post by Zorael on 2007-11-09
It's likely the same kind of conflict as with Treviño's. :>

Try completely removing it and installing, yes. You won't lose your profile.

---

### Post by viergeame on 2007-11-09
I reinstalled it and it still doesn't work.  All my settings are still there, which is nice, but I don't get any of the effects.

Also, any idea on the appearances menu problem?

---

### Post by maddog_326 on 2007-11-10
I don't know much but I got mine to work with _advanced desktop effects Settings_. Just go to add and remove section and copy and paste that.

---

### Post by viergeame on 2007-11-10
I finally got into my appearance menu, it turns out it was just lagging for a really long time.  I ended up leaving it for like 10 minutes or so before it would let me do anything.  I tried to turn on the effects and the screen flashed a bit and then I got an error saying the effects couldn't be enabled.  Compiz Fusion worked for me in Feisty, why won't it work now in Gutsy?

---

### Post by Zorael on 2007-11-10
Hmm. If you enter this command, does it output the following?
```
zorael@azrael:~$ apt-cache policy compiz-core
compiz-core:
  Installed: 1:0.6.0+git20071008-0ubuntu1.1
  Candidate: 1:0.6.0+git20071008-0ubuntu1.1
  Version table:
 *** 1:0.6.0+git20071008-0ubuntu1.1 0
        500 http://se.archive.ubuntu.com gutsy-updates/main Packages
        500 http://security.ubuntu.com gutsy-security/main Packages
        100 /var/lib/dpkg/status
     1:0.6.0+git20071008-0ubuntu1 0
        500 http://se.archive.ubuntu.com gutsy/main Packages
```

Pay special attention to the **Installed** line and compare. Just to see you've got the proper official package installed.

Furthermore, while certainly more complicated, you could start using the settings manager (custom? I don't use Gnome, so I don't know the details). If you don't have it, you need to install the **compizconfig-settings-manager** package.

Lastly, does entering 'compiz --replace &' in a terminal output anything of interest?

---

### Post by viergeame on 2007-11-11
When I put "compiz --replace &" in a terminal I get...
```
 nikki@ubuntu:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

apt-cache policy does give me the same output as yours, and I already have the settings manager installed..

---

