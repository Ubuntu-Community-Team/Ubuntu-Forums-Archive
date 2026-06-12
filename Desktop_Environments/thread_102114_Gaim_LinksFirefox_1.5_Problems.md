---
title: "Gaim Links/Firefox 1.5 Problems?"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Othersider on 2005-12-11
Hi,

I've been running into two strange problems ever since I installed Firefox 1.5: 

1) Any link I click in Gaim opens to [www.arizona.edu](www.arizona.edu).  I have never been to U of A and am not affiliated with them at all.  Prior to this problem, I had never been to their site.

2) Whenever I open Firefox, it tries to load the page '134659245'.  My homepage is google.com/ig, and if I press Alt Home, I go to Google.  I don't have any proxies set up, so I'm not sure why this is happening.

I have no idea where to start on these problems and I appreciate everyone's help.  Thanks in advance :).

---

### Post by linkunderscore on 2005-12-11
haha thats kinda funny.

Gaim>Tools>Preferences>Browsers...

Tell me what you have in there.


same with Firefox 1.5
edit>Preferences> General tab> what does it say for your homepage


I assume that you have checked both of these, but I thought we could just start trouble shooting with the easy stuff.

---

### Post by Othersider on 2005-12-11
At the risk of sounding like an idiot, I see no "Browser" settings option in Gaim preferences.  Using version 1.5.0.  Screenshot of preferences [here](http://www.typpo.us/stuff/screenshots/prefs.png).

Firefox homepage is [http://www.google.com/ig](http://www.google.com/ig).

---

### Post by ahave2005 on 2005-12-11
[QUOTE=Othersider]Hi,

I've been running into two strange problems ever since I installed Firefox 1.5: 

1) Any link I click in Gaim opens to [www.arizona.edu](www.arizona.edu).  I have never been to U of A and am not affiliated with them at all.  Prior to this problem, I had never been to their site.[/QUOTE]

I've no idea what your problem is, but I have the same "problem" when Firefox sometimes for no apparent reason opens [www.microsoft.com](www.microsoft.com) .......... I've no idea why, but it seems strange.

I've also tried it a few times in Firefox; XP, before i switched to Ubuntu.

/ahave

---

### Post by grte on 2005-12-11
I've got a similar problem to this.  After updating to Firefox 1.5, links in GAIM won't open in the browser at all.  I don't have a browser option under edit -> Preferences, either.

---

### Post by The Warlock on 2005-12-11
[QUOTE=ahave2005]I've no idea what your problem is, but I have the same "problem" when Firefox sometimes for no apparent reason opens [www.microsoft.com](www.microsoft.com) .......... I've no idea why, but it seems strange.

I've also tried it a few times in Firefox; XP, before i switched to Ubuntu.

/ahave[/QUOTE]

If you just type in http into the address bar (or have a malformed URL that goes something like [http://http://www.example.com/](http://http://www.example.com/)) then it will go to Microsoft's page. This is because in Firefox, when you type something that isn't a URL into the address bar, it does a Google search for that and then brings you to the first result. The first result for "http" on Google is microsoft.com.

---

### Post by linkunderscore on 2005-12-11
thats really weird...:confused: 

I have this: 
[http://www.escapeportal.net/upload/2005-12-11-221648_1280x1024_scrot.png](http://www.escapeportal.net/upload/2005-12-11-221648_1280x1024_scrot.png)

What version of gaim do you have? I am running the 1.5 that came with Ubuntu.

I am also running Firefox 1.5. I am not getting these errors. 

Almost seems like a VIRUS!!!

---

### Post by Othersider on 2005-12-11
I have 1.5.0, the version that came with Ubuntu.  The Update Manager indicates my system is entirely up to date, and I have release notification enabled in Gaim.  Yet this Browsers node is missing from preferences.  Strange indeed =/.

---

### Post by grte on 2005-12-11
I'm running 1.5 as well, but no browser preferences.

---

### Post by linkunderscore on 2005-12-11
see if this gives you the browser option :

```
sudo apt-get install gaim-extendedprefs
```

Its the extended preferences plugin. Maybe that is why mine is different from all of yours?

---

### Post by grte on 2005-12-11
[QUOTE=linkunderscore]see if this gives you the browser option :

```
sudo apt-get install gaim-extendedprefs
```

Its the extended preferences plugin. Maybe that is why mine is different from all of yours?[/QUOTE]

'Fraid not.  I've already got the extended prefs, no change.

---

### Post by linkunderscore on 2005-12-11
Maybe remove then reinstall gaim? 
According to the gaim website you SHOULD have the Browser option.
[http://gaim.sourceforge.net/screenshots.php?file=prefs.png](http://gaim.sourceforge.net/screenshots.php?file=prefs.png)

---

### Post by grte on 2005-12-11
[QUOTE=linkunderscore]Maybe remove then reinstall gaim? 
According to the gaim website you SHOULD have the Browser option.
[http://gaim.sourceforge.net/screenshots.php?file=prefs.png](http://gaim.sourceforge.net/screenshots.php?file=prefs.png)[/QUOTE]

I've tried that as well, however, when I reinstall, my accounts are still on it.  Is there some file that I'm missing?

---

### Post by linkunderscore on 2005-12-11
[QUOTE=grte]I've tried that as well, however, when I reinstall, my accounts are still on it.  Is there some file that I'm missing?[/QUOTE]

use Synaptic and do a *"complete removal"*


that should remove all config files and any extra data

---

### Post by grte on 2005-12-11
[QUOTE=linkunderscore]use Synaptic and do a *"complete removal"*


that should remove all config files and any extra data[/QUOTE]

I did that...Same thing.

---

### Post by linkunderscore on 2005-12-11
:confused: :confused: Then I am all out of ideas. This is really strange, and I am not that experienced with linux/ubuntu/gaim/firefox to understand what could be causing this strange behavior. 

Hopefully someone with a little bit more expertiese can help you out. I'm sorry man :(

---

### Post by grte on 2005-12-11
[QUOTE=linkunderscore]:confused: :confused: Then I am all out of ideas. This is really strange, and I am not that experienced with linux/ubuntu/gaim/firefox to understand what could be causing this strange behavior. 

Hopefully someone with a little bit more expertiese can help you out. I'm sorry man :([/QUOTE]

No problem.  It's not a big deal, nothing I can't live with.  Thanks for trying.

---

### Post by linkunderscore on 2005-12-16
hahaha I think i found your problem 

[http://www.ubuntuforums.org/showthread.php?t=104266](http://www.ubuntuforums.org/showthread.php?t=104266)


still don't know how to fix it but this appears to be  the issue.

---

### Post by Othersider on 2005-12-20
**Problems fixed** by changing shortcut and preferred browser command from 'firefox %u' to 'firefox %s'.

---

### Post by three_sixteen on 2005-12-20
[QUOTE=ahave2005]I've no idea what your problem is, but I have the same "problem" when Firefox sometimes for no apparent reason opens [www.microsoft.com](www.microsoft.com) .......... I've no idea why, but it seems strange.

I've also tried it a few times in Firefox; XP, before i switched to Ubuntu.

/ahave[/QUOTE]

Well, its not really for no apparent reason(as far as I know).  But if you type an invalid URL into the address bar it goes there.  Its either a sick joke by the firefox developers or someone at ICANN really, really likes microsoft.   I don't know so much about the latter though.

---

### Post by _simon_ on 2006-01-11
[QUOTE=Othersider]**Problems fixed** by changing shortcut and preferred browser command from 'firefox %u' to 'firefox %s'.[/QUOTE]

Worked for me!

---

### Post by steveneddy on 2006-06-12
[QUOTE=_simon_]Worked for me![/QUOTE]

Make sure that the launcher is %u and the line in "prefered applications" section is %s.

One more bean and still counting!

---

### Post by jeffvc on 2006-07-17
If anyone is still encountering this problem, I've now fixed it on my system.  

My system has been installed for a while (I've been upgrading it since Breezy), and I think this may have caused the issue.

When I went to System > Preferences > Preferred Applications, Web Browser was set to "Custom" ("mozilla-firefox %s").  I believe that an older version of firefox used this command.  However, when I try this on the command line, I get:

```
jeff@skellington:~$ mozilla-firefox

run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin.
```

I'm assuming that applications (e.g. Gaim) are trying to start Firefox,  getting this error, and failing silently.

At any rate, I simply changed my settings to "Firefox" ("firefox %s"), and suddenly links were working once again.

---

