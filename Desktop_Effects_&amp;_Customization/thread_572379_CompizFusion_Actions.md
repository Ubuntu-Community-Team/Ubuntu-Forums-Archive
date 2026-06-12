---
title: "CompizFusion Actions ?"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by Drakkor on 2007-10-10
I remember with Beryl, there were keyboard action keys to permit different effects, I 
see no such thing with CF......I can rotate cube , paint fire, negative and such, but for 
some of the other effects , I have no idea of what keys to press ! Is there some list
somewheres ? :confused:

---

### Post by Sqwishy on 2007-10-10
You probobly have the compiz config settings manager proggie under system>>prefrences>>compiz config...
Run that and it'll tell you. For alot of features you'll hafta turn em on yourself and using that'll let you do it.

---

### Post by Drakkor on 2007-10-10
For me the System>Preferences>CompizConfig Settings Manager does absolutely nothing.
Actually, I get all the settings in System>Preferences>Appearance.>.Visual Effects tab>Custom>Preferences to get to the CompizConfig,lol :)
But,as in this example, unless I knew from Beryl to hit Cntrl/Alt/and drag the cube around,
how would one know ??

---

### Post by Forlong on 2007-10-10
Weird. You are missing the Actions tab.

What output gives:
```
dpkg -l | grep compizconfig-settings-manager
```

---

### Post by avik on 2007-10-10
I noticed the same thing happened to me after a particular upgrade.  It was fine before that, but now there's no way to change the keybindings for many of the features.

By the way, for me at least, the output of that command is empty.

---

### Post by Forlong on 2007-10-10
avik, did you use some script to install Compiz?

---

### Post by Drakkor on 2007-10-10
Here's my output:
drakkor@drakkor-desktop:~$ dpkg -l | grep compizconfig-settings-manager
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
drakkor@drakkor-desktop:~$

---

### Post by Forlong on 2007-10-10
Same as me... and what about
```
dpkg -l | grep compiz
```
please use the forum's CODE tag (# button)

---

### Post by Drakkor on 2007-10-10
```
dpkg -l | grep compiz
```

---

### Post by avik on 2007-10-10
> avik, did you use some script to install Compiz?

Yes, I used: [http://ubuntuforums.org/showthread.php?t=485284]("http://ubuntuforums.org/showthread.php?t=485284").

It was fine the first time.  Then when I updated, this came up.

> Same as me... and what about
```
dpkg -l | grep compiz
```


```

rc  compiz-gtk                                 0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
rc  compiz-plugins                             0.3.6-1ubuntu13                            OpenGL window and compositing manager - plug

```

Though I doubt in my case it makes a difference, as I didn't install from the repos.

---

### Post by mjwood0 on 2007-10-10
You're running an older version of Compiz.  Perhaps getting to a newer version will help things.

---

### Post by Drakkor on 2007-10-10
It still rocks,though,lol :)

---

### Post by Forlong on 2007-10-10
> **Drakkor said:**
> ```
dpkg -l | grep compiz
```
Erm.. I'd call that an unusual way to post an output but OK.
The only difference seems to be that you have that "Compiz Gnome Manager" installed.


> **avik said:**
> Yes, I used
Then this not the right thread for you. You are using the latest git version of ccsm which has a different structure. I would have to boot into another install to check but as far as I remember the keybindings have been moved to another place of the manager.

---

### Post by Forlong on 2007-10-10
> **mjwood0 said:**
> You're running an older version of Compiz.  Perhaps getting to a newer version will help things.
Sorry but what are you talking about? That's the latest _stable_ stuff you can get. It's in Gutsy and that hasn't even been released yet.

Please don't tell people to update to development versions.

---

### Post by Drakkor on 2007-10-10
It still rocks !!

---

### Post by mjwood0 on 2007-10-10
> **Forlong said:**
> Sorry but what are you talking about? That's the latest _stable_ stuff you can get. It's in Gutsy and that hasn't even been released yet.

Please don't tell people to update to development versions.

Please don't post incorrect information.

According to [the official web site]("http://compiz.org"), version 0.4 is the latest stable release.  I didn't say it wasn't the latest stable in deb format, and you didn't either.  There is such thing as stable, non packaged releases.

---

### Post by avik on 2007-10-11
> **Forlong said:**
> Then this not the right thread for you. You are using the latest git version of ccsm which has a different structure. I would have to boot into another install to check but as far as I remember the keybindings have been moved to another place of the manager.

Okay, thanks for addressing that issue.  I looked all over for keybindings, but the closest I found was either the generic keybindings not specific to any plugins, or (strangely enough) checkboxes which seem to have no effect.  I'll see how future updates affect this.

---

### Post by Forlong on 2007-10-11
> **mjwood0 said:**
> Please don't post incorrect information.
0.6 is the latest stable release: [http://lists.freedesktop.org/archives/compiz/2007-October/002696.html](http://lists.freedesktop.org/archives/compiz/2007-October/002696.html)

---

### Post by mjwood0 on 2007-10-11
I stand corrected.

Odd that 0.6 doesn't show up on their web site though.  

Anywho, time to re-install tonight!

---

### Post by Drakkor on 2007-10-11
Hmm......... 9 updates this morning most having to do with compiz, but still no actions tabs.

---

### Post by Whiffle on 2007-10-17
Alrighty then.  I have this same problem.  The interesting part is I have two computers, both running fully updated versions of Gutsy, with the exact same compiz packages.  One of them has the Actions tab, the other does not.  I've deleted *all* configuration files for my test user and checked, they don't come back, so its got to be some file somewhere else in the system thats junking it up.  Any ideas?

---

