---
title: "Help with browser bugs ;)"
date: 2009-03-03
forum: General Help
---

### Post by mrl777 on 2009-03-03
Hello,

I have questions: is it possible for someone to gain access to the Linux through a plug-in or add-on inside, let's say, Firefox, or SeaMonkey?

If such is the case, then to what extent can they get into your system?  Can they load new code, overwrite software modules or change security features?  Can they trash your hard disk or re-flash your BIOS?

Can they execute code that can write into other parts of the system beyond the browser's directory structures?

I need to know this because I suspect that my system has been compromised, but it could be that I've experienced some random glitches.  For example SeaMonkey just popped up a window stating that it could not access a security feature and that it could be that my disk is full (it's not) or some files are write protected.  This was while accessing an SSL page.  I closed the browser and restarted it and the problem went away.  The question is, has the problem actually gone away or am I just being fooled into thinking that it has gone away.  I checked into the browser's security settings and the SSL stuff is on, but that doesn't mean that SSL is actually working.

I'm using SeaMonkey because I think something got into Firefox (possibly through a plug-in or add-on).  But that's another story.

---

### Post by cdenley on 2009-03-03
Any application which works with data retrieved from the internet could potentially be exploited to execute arbitrary system code as the user running the application, if it doesn't process the data correctly. Such vulnerabilities are not very common, though. Web browsers, such as firefox, are most likely to have a security vulnerability due to it actually running code (javascript) from external sources, sometimes even with non-free plugins (flash). This is why using the noscript addon is highly recommended. It prevents javascript or flash from running until you tell it to trust the site.

If an attacker does manage to execute arbitrary code, then they could potentially alter any files or directories you have write access to. If they manage to escalate to root privileges, they can alter anything they want, including the hard disk itself.

I'm not sure if it is possible to modify any BIOS from within Linux. Most browser exploits only result in a corrupt firefox profile. There may be security restrictions to prevent hijacked browsers from doing anything too malicious, but I'm not sure.

---

### Post by bodhi.zazen on 2009-03-03
Moved to general help.

Although I understand you are having problems, we need a better description of what is wrong.

First, there is no reason you should start by assuming you have been cracked, you may have a bug or mis configured application, hardware failure, or any number of issues.

This is not to say that Linux is invulnerable, it is just you should investigate a little more before you assume you have been cracked.

The most common browser cracks are, IMO, from java script as java script is cross platform.

See : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

Most of these exploits do not affect the system.

Last, if you are cracked, and people can run arbitrary code, all things are possible. That is what is meant by "arbitrary", although to affect system files a cracker would need to escalate privileges.

this is where apparmor comes into play, you can (and probably should) confine any and all applications that are network aware.

See :

 [[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

There are links on that thread to apparmor profiles.

I posted my profiles here (no guarentee mine are any good mind you ;)

[http://bodhizazen.net/adblock/aa-profiles/](http://bodhizazen.net/adblock/aa-profiles/)

---

### Post by magog45 on 2009-03-06
I understand what he is talking about, after my last update of the Hardy Heron release whenever I start Seamonkey I get the can't initialize SSL thus I can't sign in to any pages that require it. Strangely Firefox works fine and once I have accessed a page with Firefox then seamonkey seems to work fine. I do weekly updates only on Sundays so I am assuming that it was something in the last update.

---

