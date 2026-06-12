---
title: "Pinning Grooveshark to taskbar gives flash error."
date: 2014-07-20
forum: Gaming &amp; Leisure
---

### Post by tatsujb on 2014-07-20
Flash is recognized on the normal firefox but not on the pinned grooveshark app. what do I do? [ATTACH=CONFIG]254854[/ATTACH]

it seems there is no further flash version to install in the Appstore and following the link and selecting APT for ubuntu opens up the Appstore to not found.

---

### Post by tatsujb on 2014-07-20
OK seems i've gone further : [http://askubuntu.com/questions/11/how-do-i-install-adobe-flash-player](http://askubuntu.com/questions/11/how-do-i-install-adobe-flash-player)

in Appstore I unistalled flash i checked both canonical software sources waited for it to apply then when to the "cannonical partners section" and installed flash 11.

this did not fix the issue. but now install link from adobe works. trying it now.

---

### Post by oldrocker99 on 2014-07-20
Do you have synaptic installed (it may not have come with your install)? Just so you know, it's the most useful and powerful way to access the vast array of packages available for Ubuntu (whose repos are top-notch AFAIC). It's easy to use and has an excellent search feature.

---

### Post by tatsujb on 2014-07-21
> **oldrocker99 said:**
> Do you have synaptic installed (it may not have come with your install)? Just so you know, it's the most useful and powerful way to access the vast array of packages available for Ubuntu (whose repos are top-notch AFAIC). It's easy to use and has an excellent search feature.
no I didn't.

now i do.

did new ubuntu install

here's what I did.

[LIST=1]
[*]first boot 
[*]update and upgrade via terminal 
[*]add cannonical repos to AppStore 
[*]update again switch from X.org driver to nvidia 
[*]reboot 
[*]uninstall flash via Appstore 
[*]follow grooveshark link : [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) (it points to 11.2 not just 11) used apt package option. 
[*]first install the transitional dummy package ttf-dejavu and non-free TTF options 
[*]then installed it which automatically added the "GTK+control panel for adobe flash player plugin version 11 (adobe-flash-properties-gtk)" option 
[/LIST]

flahs works everywhere except the grooveshark app. :(
[ATTACH=CONFIG]254881[/ATTACH]anything missing?

---

### Post by tatsujb on 2014-07-21
apparently this is all due to Ubuntu's fresh-out-of LTS state : [https://bugs.launchpad.net/ubuntu/+source/unity-webapps-grooveshark/+bug/1309426](https://bugs.launchpad.net/ubuntu/+source/unity-webapps-grooveshark/+bug/1309426)

I guess i have to wait for a fix from ubuntu. same problem happens on youtube and a bunch of other sites.

---

