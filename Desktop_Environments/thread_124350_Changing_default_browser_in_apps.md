---
title: "Changing default browser in apps?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Garyu on 2006-02-01
When I installed Ubuntu Breezy it worked great. Everything. But I have made changes, and somewhere I screwed something up.

I just noticed that when I click on links in apps (like in Evolution e-mail or in GAIM) the link goes purple as if I would have visited it, but no browser will open. The only thing I did that I think might have influenced this is that I upgraded Firefox to version 1.5 using the Automatix script. 

So, I'm guessing that my apps are trying to open the old Firefox to show links, but it isn't there anymore. So how do I change my default browser to Ff 1.5? 

(I'm only guessing that this is the problem, but the links used to work fine before and I'm not sure when they stopped working)

---

### Post by az on 2006-02-01
Can you try temporarily removing (moving or renaming) your /.mozilla directory?  Maybe the firefox config is borked?

---

### Post by pld on 2006-02-01
I was running into a similar problem with thunderbird.

If i tried to click on a URL link in an email, it would only open new links in my older firefox (1.0.7), not 1.5

I did NOT use a script to install, I just downloaded the file and installed it into my user home directory:
/home/myname/firefox

However, IF I already had ff open, then links clicked on would open in a new tab in ff 1.5.

I made the mistake of also un-installing ff1.0.7, and then NO links would work.

So here is what I tried:

1. re-install ff using apt.  (apt-get install firefox).
2. Make the following changes in the /usr/bin/mozilla-firefox startup script:

Find:
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"

And change the paths to the ones relevant to your newly installed ff1.5.  In my case it looked like this:
MOZ_DIST_BIN="/home/myname/firefox"
MOZ_PROGRAM="/home/myname/firefox/firefox"

This way, any app that uses a link would now open the link in my new ff1.5 installation, no problem.

This _seems_ to have fixed my problem so far, but I don't know if perhaps I am breaking something by doing this.

---

### Post by Garyu on 2006-02-02
well, thank you for your tips, but I found an even easier way of doing it, provided by the super-duper-nice guys in the Ubuntu team. :D 

I just went to **System --> Settings --> Preferred programs**. The browser was set to invoke on the command *"mozilla-firefox %s"* but when I tried to run that in a terminal an error was reported. So I just checked the properties of my Firefox program starter and saw that the command line should be only *"firefox %s"*. So I just changed that in the **Preferred programs** box and presto - everything works great. :cool:

EDIT:
when I think of it, this isn't the first time I have solved something on my own. maybe I should just start thinking more and do a little less posting on the forums. but on the other hand, I really like reading the input of others, even when I do find my own answers... :)

---

### Post by xurizaemon on 2006-02-08
Cool ... but how do I get KDE apps (eg Kopete) to play nice with Firefox / Thunderbird? :confused:

---

### Post by arnieboy on 2006-02-08
[QUOTE=Garyu]When I installed Ubuntu Breezy it worked great. Everything. But I have made changes, and somewhere I screwed something up.

I just noticed that when I click on links in apps (like in Evolution e-mail or in GAIM) the link goes purple as if I would have visited it, but no browser will open. The only thing I did that I think might have influenced this is that I upgraded Firefox to version 1.5 using the Automatix script. 

So, I'm guessing that my apps are trying to open the old Firefox to show links, but it isn't there anymore. So how do I change my default browser to Ff 1.5? 

(I'm only guessing that this is the problem, but the links used to work fine before and I'm not sure when they stopped working)[/QUOTE]
nie to know you found the solution but you would have found it in the automatix thread itself:
[http://ubuntuforums.org/showpost.php?p=692440&postcount=1595](http://ubuntuforums.org/showpost.php?p=692440&postcount=1595)

---

