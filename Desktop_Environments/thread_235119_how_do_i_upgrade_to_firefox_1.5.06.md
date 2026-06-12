---
title: "how do i upgrade to firefox 1.5.06?"
date: 2006-08-12
forum: Desktop Environments
---

### Post by quonsar on 2006-08-12
no matter what i do the 'check for upgrades' menu item is grayed out, even if i run firefox sudo. wtf?

---

### Post by aysiu on 2006-08-12
> **quonsar said:**
> no matter what i do the 'check for upgrades' menu item is grayed out, even if i run firefox sudo. wtf?
Are you using the Ubuntu version or the Mozilla version?

---

### Post by orb9220 on 2006-08-12
You have to wait for the ubuntu repostories to make the update available.

You can get around that thru other means but also can cause problems down the line.

Besides 1.5.0.6 is nothing but a security hole fix on an obscure possible exploit. Chances are super slim so I am not worried about it.

You will not have the instant upgrade feature in firefox. If you can wait a week or so then it will become available thru synaptic.

---

### Post by quonsar on 2006-08-12
ok, super. had me very puzzled!

---

### Post by aysiu on 2006-08-12
> **orb9220 said:**
> If you can wait a week or so then it will become available thru synaptic. And if you cannot wait a week or so, then you should really be using Mozilla's Firefox instead of Ubuntu's Firefox.

[Manual installation instructions](http://help.ubuntu.com/community/FirefoxNewVersion)
[Installation script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

---

### Post by orb9220 on 2006-08-12
aysiu could you advise me if and why the Mozilla's Firefox is better and how I may replace the ubuntu one if that is the case.

Thanks!

---

### Post by aysiu on 2006-08-12
> **orb9220 said:**
> aysiu could you advise me if and why the Mozilla's Firefox is better and how I may replace the ubuntu one if that is the case.

Thanks!
Mozilla's Firefox is self-updating. So when a new release comes out, it can install the updates right away.

Ubuntu's Firefox is a package maintained by the Ubuntu developers. You have to rely on the developers updating it (which is usually a few days to a week after Mozilla's update).

---

### Post by jgcamp99 on 2006-08-12
I downloaded and installed Mozilla FF 1.5.0.6, it's still greyed out after installation/update just the same. I am updated from 1.5.0.5 to .6 per the "About Firefox" pull down from Help. The other thing in about:config on the address line of FF, I can change whether auto update is enabled, but it's still greyed out in the preferences as non-selectible. Then there's the drop down of the manual "check for updates" that is greyed out and doesn't work either. I know Ubuntu wants to control updatability with this, but those of us that want the latest update when available, should still be allowed to do this without going thru this hassle.

---

### Post by jgcamp99 on 2006-08-12
My last post, forget about that one, I found this to be yet another sudo vs root login issue.

As the default user that Ubuntu/I created @ initial installation, the items I indicated under Edit, Preferences and even the Help for the update feature will be greyed out.

gksudo firefox, however allows me to be able to have those items as selectable. Why, because I entered a power user password and am sudo user. 

As Root, all items are selectable as well, then again I didn't type gksudo firefox and whatnot.

At any rate, I did my upgrade to 1.5.0.6 as root, and when I'm the Ubuntu user, to update Firefox, I have to type gksudo, otherwise I have to be root to have it work. I see this as an issue that is created by the lock down of users. Ubuntu is controlling whether you get 1.5.0.6 automatically or not.  Just hold tight, the FF update should be available on the repository shortly.

---

### Post by kerry_s on 2006-08-12
I always replace mine from the mozilla site. I don't like the .deb version as it is slower than the one from the mozilla site. What i do is go to the get firefox page and download the linux version to my /tmp folder. Then in my /tmp folder i unpack it, Then i open root nautilus(sudo nautilus /usr/lib), i scroll down to firefox go into /plugins and copy all the plugins and paste them in the firefox/plugins i unpacked. Now i back out to /usr/lib and rename the firefox to firefox.old then i cut and paste the new firefox folder there. That's it you get the offical firefox that's faster and more stable. Just to note you can also do it with swiftfox by renaming the swiftfox folder to firefox and doing the same steps. I use to use swiftfox cause it is the fastest but i have problems with some extensions so i just use the regular one.

---

### Post by fragos on 2006-08-13
The only difference in Ubuntu Firefox, to my knowledge, is the automatic update.  It doesn't take very long to come and you can be assured that the Ubuntu team made sure there were no combatibility problems.  I'll for one will accept the wait.  I also consider the assumption that the "Ubuntu version" is slower as suspect.  Internet performance changes constantly up and down based on factors outside the control of Firefox.  For example the number of large downloads on a leg of the Internet used for your connection.  I don't question the observation, just the culprit.

---

### Post by azmrb on 2006-08-13
The mozilla firefox documentation indicates that the "Check for Updates" function will be greyed out if you don't have write prvileges in the directory where it is installed.  That is why I installed it under my home folder.

---

### Post by kerry_s on 2006-08-13
> **fragos said:**
> The only difference in Ubuntu Firefox, to my knowledge, is the automatic update.  It doesn't take very long to come and you can be assured that the Ubuntu team made sure there were no combatibility problems.  I'll for one will accept the wait.  I also consider the assumption that the "Ubuntu version" is slower as suspect.  Internet performance changes constantly up and down based on factors outside the control of Firefox.  For example the number of large downloads on a leg of the Internet used for your connection.  I don't question the observation, just the culprit.

For me i can see the difference in load time in fasterfox and the time it takes to connect to sites is also faster in the non-ubuntu firefox. It's not a connection issue for me. For me it's not a assumption, it's a fact, the non-ubuntu firefox is faster for me, it may be different for others.

---

### Post by fragos on 2006-08-13
Fasterfox is highly tuned and should be faster than stock.  I've made a number of configuration changes to my Ubuntu firefox that impact its performance.  Its a little like overclocking and removeing the margins that the manufacturer builds in for warrantte purposes.  If for example you disable IPv6 performance will improve but when and if some sites start to use IPv6 you'll have to back out your change.  Firefox works with both IPv4 and v6 so you don't have to know about which addressing scheme a site uses.  These things don't constitute design flaws, they're ease of use choices.

---

### Post by kerry_s on 2006-08-13
Hee,hee, I've done all those tweaks.
quote:
"Fasterfox is highly tuned and should be faster than stock."
 Your talking about the extension right-> [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/) that's what i use to see the load time and tweak my system, now it's alot easier then messing in about:config I always turn off ipv6 system wide as well as in firefox, i also use a hosts adblock so no matter what browser i'm useing i can weed outsome of that stuff that slows the internet down.

---

