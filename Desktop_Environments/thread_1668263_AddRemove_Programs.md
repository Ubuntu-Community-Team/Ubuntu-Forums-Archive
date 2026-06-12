---
title: "Add/Remove Programs"
date: 2011-01-16
forum: Desktop Environments
---

### Post by graylinux on 2011-01-16
Hi 
 
Ubuntu 10.04
 
I've just upgraded all the way up from 7.04 to 10.04.....
 
I now have Firefox 3.6.14. When I go to a site which requires Flash I'm to told to upgrade my Flash version.. I've done this twice but it still does not play and continues to tell me that I need to update... 
 
Whilst trying to diagnose this I went to Applications-Add/Remove .... but that failed with 
 
ERROR Could not launch Add/Remove...
 
Failed to exeute child process "usr/bin/gnome-app-install" (no such file or directory)
 
I looked in /usr/bin and indeed there is no gnome-app-install??
 
Anyone know what's happening here please?
 
Thanks
 
P.S.
 
My login user is set to be an administrator...and I have show-hidden-files set

---

### Post by issih on 2011-01-16
Add/Remove was replaced with the ubuntu software centre (which you should have in your main menu)

I'd try removing flash completely and then readding it myself.

---

### Post by coffeecat on 2011-01-16
> **graylinux said:**
> I've just upgraded all the way up from 7.04 to 10.04.....

Did you go directly from 7.04 to 10.04, or did you go 7.04 > 7.10 > 8.04 > 10.04? If you went directly from 7.04 to 10.04, this might explain your problems. A direct upgrade like that is not supported. The only supported upgrades that jump releases are LTS > LTS, for example 8.04 > 10.04.

You say you still have Add/Remove in your menu. Add/Remove was deprecated in favour of Software Centre in either 9.10 or 10.04 - I can't remember which. You should be able to find Software Centre in the menu where Add/Remove was, but if Add/remove is still there it sounds as though the upgrade has failed.

---

### Post by graylinux on 2011-01-16
Oh I see.... thanks ... do you know how I might remove the Add/Remove option from the Applications menu? I think it will save confusion of other users of the machine...
 
Thanks

---

### Post by graylinux on 2011-01-16
Hi 
 
Sorry just spotted your query about upgrade path.
 
I followed the EOLupgrades instructions on Ubuntu.com.... *think it was as you noted...  *7.04 to 7.10 to 8.04.3 LTS to 10.04 if i recall correctly.
 
cheers

---

### Post by coffeecat on 2011-01-16
Do you have both Software Centre and Add/Remove in the menu? If so, right-click on the menu in the panel and choose 'edit menu'. You should then be able to disable the Add/Remove entry.

As an alternative to Software Centre, don't forget that you have Synaptic in System > Administration. It's less user-friendly than SC, but more powerful.

**EDIT**: by the way, if you went 7.04 > 7.10 > 8.04, you would not have been able to update 7.04 or 7.10 before doing a release upgrade. If so, this might lead to other problems. If you experience a lot of problems with this system I would suggest thinking about cutting your losses and doing a fresh install of 10.04. The 10.04.2 point release is due near the end of this month.

---

### Post by graylinux on 2011-01-16
I really, really hope not.... it's taken over 30 hours of total stress to get where I am now... I don't think my heart could take any more..... :)
 
I'm having all sorts of problems though... I want to unisntall Firefox but it does not appear in either Package Manager or Ubuntu s/w centre ....

---

### Post by coffeecat on 2011-01-16
> **graylinux said:**
>  I want to unisntall Firefox but it does not appear in either Package Manager or Ubuntu s/w centre ....

Why? Are you having problems with it?

---

### Post by graylinux on 2011-01-16
Hi and thanks for your assistance...
 
I was having difficulty with Flash... When I went to any page needing Flash, Firefox told me to install Adobe Flash Player x.x.x ... I did this several times but to no avail. As suggested tried to install Adobe FP outiside of Fireox... which I did using Ubuntu S/W Centre... still no joy even though Adobe 10 appeared in my list of installed packages. 
 
I decided to uninstall / reinstall Firefox (3.5) to see if that would cure it... but no Firefox in either Ubuntu S?W Centre or Synaptic P/Mngr.... 
 
I then decided to forget Firefox and to download Chrome... I tried this from Ubuntu S/W Centre but despite clicking the button several times nothing happened... light-activity on my modem indictated no download .... 
 
Since then, I went to Synaptic... successfully installed Chromuim... also, hey presto! Firefox appeared in the packages...  have now managed to de-install Firefox   
 
If I recall, there's a manual 'apt' call that updates the dpkg system? Mayne it just needs a kick now and then?
 
I' going to re-install FFox now to see if it will play Flash....

---

### Post by graylinux on 2011-01-16
Hi and thanks for your assistance...
 
I was having difficulty with Flash... When I went to any page needing Flash, Firefox told me to install Adobe Flash Player x.x.x ... I did this several times but to no avail. As suggested, tried to install Adobe FP outiside of Firefox... which I did using Ubuntu S/W Centre... still no joy even though Adobe 10 appeared in my list of installed packages. 
 
I decided to uninstall / reinstall Firefox (3.5) to see if that would cure it... but no Firefox in either Ubuntu S?W Centre or Synaptic P/Mngr.... 
 
I then decided to forget Firefox and to download Chrome... I tried this from Ubuntu S/W Centre but despite clicking the button several times nothing happened... light-activity on my modem indictated no download .... 
 
Since then, I went to Synaptic... successfully installed Chromuim... also, hey presto! Firefox appeared in the packages...  have now managed to de-install Firefox   
 
If I recall, there's a manual 'apt' call that updates the dpkg system? Mayne it just needs a kick now and then?
 
I' going to re-install FFox now to see if it will play Flash....

---

### Post by graylinux on 2011-01-16
Hi and thanks for your assistance...
 
I was having difficulty with Flash... When I went to any page needing Flash, Firefox told me to install Adobe Flash Player x.x.x ... I did this several times but to no avail. As suggested, tried to install Adobe FP outiside of Firefox... which I did using Ubuntu S/W Centre... still no joy even though Adobe 10 appeared in my list of installed packages. 
 
I decided to uninstall / reinstall Firefox (3.5) to see if that would cure it... but no Firefox in either Ubuntu S?W Centre or Synaptic P/Mngr.... 
 
I then decided to forget Firefox and to download Chrome... I tried this from Ubuntu S/W Centre but despite clicking the button several times nothing happened... light-activity on my modem indictated no download .... 
 
Since then, I went to Synaptic... successfully installed Chromuim... also, hey presto! Firefox appeared in the packages... have now managed to de-install Firefox 
 
If I recall, there's a manual 'apt' call that updates the dpkg system? Mayne it just needs a kick now and then?
 
I'm going to re-install FFox now to see if it will play Flash....

---

### Post by graylinux on 2011-01-16
Ok It's official... I give up.... I've installed/re-installed FFox(3.6), installed Adobe Fplayer 10 and even installed the 'Adobe Flash Player Installer' for Firefox.... and still it will not play Flash...
 
It's Chromium for me..... thanks again for your help

---

### Post by Krytarik on 2011-01-16
Chromium is apparently more powerfull than the current Firefox release. I've tried it recently. Personally I would choose for me to stick with it, were there better support by extensions.

However, did you check in Firefox if the flash plugin is activated ("Tools -> Add-ons -> Plugins"? Look also for a symlink to "/usr/lib/adobe-flashplugin/libflashplayer.so" or "/etc/alternatives/firefox-flashplugin" in the plugins folder of firefox/mozilla, "/usr/lib/firefox-3.6.*/plugins" or "/usr/lib/mozilla/plugins". On my system, also 10.04, but fresh install, I have a symlink from mozilla to alternatives.

Another way to test is to create a new user profile in Firefox, by disabling the current, rename "/home/USER/.mozilla/firefox/*.default".

---

### Post by graylinux on 2011-01-17
**[COLOR=#3366cc]Guten Morgen![/COLOR]**
 
Hi and thanks for your suggestions... I've checked those out and still it refuses to play flash. Curiously, in my plugin manager indicated that 'Shockwave Flash' is enabled... I guess that is another branding for the Adobe Flash Plug-in?
 
Once again, I completely de-installed Adobe and Firefox (including manual deletion of any/all directories left in place even after de-installation) and re-installed the lost.... but still no joy
 
When I go to the BBC iPlayer site (for example), first I get a message saying the flash plug-in has crashed. If I attempt to play anything I get a prompt saying I need to upgrade to Adobe Flash x.x.x .. I follw that link and download the APT for ubuntu 9+... then the insaller tells me I already have it loaded!!! I've checked the various symlinks again too
 
I've spent two whole days trying to fix this... time to move-on to Chrome!
 
Vielen Danke once more for trying to help - cheers

---

### Post by VanillaMozilla on 2011-01-17
Wow, what a mess.  You've made a lot of changes, and there's a lot that's messed up.  Let's take it systematically.

0. You can test Flash [here.]("http://www.adobe.com/software/flash/about/")  If it passes that test, then you have it and it's working.



Now let's check your computer setup.  I suggest that you don't skip steps, even if you have done them before.

1. Applications > Ubuntu Software Center.  Type *flash* in the search box.  Now click on "Adobe Flash plugin".  It should show it as installed.  If you look in the Synaptic Package Manager and type *flash* in the search box, flashplugin-installer and flashplugin-nonfree should be installed.  You should have 10.1.102.65ubuntu0.10.10.1.  If it isn't, install it or update it.

2. In the Firefox menu, Tools > Add-ons > Plugins.  This may show Shockwave Flash 10.1 r102 installed and enabled.  You should not have two different versions.  Also look for Gnash and let us know if you have that.  You should have only one Flash plugin.  If it isn't enabled, enable it and restart Firefox.  (I'm not sure if you need this--the plugin names are a mess--but let's check anyway and see what you have.)  Also type about:plugins [that's about colon plugins -- this forum displays the colon as a smiley face] in the Firefox url address box.  This will show all the plugins.

3. In the Firefox menu, Edit > Preferences > Content > Enable JavaScript.  (Flash will not run without JavaScript.)

4. Make sure you are not blocking Flash with an extension such as NoScript, YesScript, or FlashBlock (there are also others that do this).  You can check extensions with Tools > Add-ons > Extensions.

5. If Flash still isn't working, you may have to create a new profile for Firefox.  Search here for Profile Manager:  [http://kb.mozillazine.org/](http://kb.mozillazine.org/) .  (Site is down right now and I can't search.)

6. Check Synaptic Package Manager > Sections > All.  Type gnash in the the search box.  You might need to make sure that browser-plugin-gnash and swfdec-mozilla are not installed.



In addition, you described multiple issues that suggest that your system might be quite messed up (for example, Firefox most definitely *is* in the Ubuntu Software Center and in the Synaptic listings).  To straighten out your system you might want to start a separate thread in the updates forum.  Other people know this better than I, but for now, I suggest:

1. Check Synaptic for broken packages.  Custom Filters > Broken.  (I'm not sure if this is sufficient.  You have to specially set up a custom filter, but if you do find any broken packages, fix them.)

2. Also check your update settings.  System > Updates > Ubuntu software tab and Updates tab.  Sometimes problems fix themselves if you allow it.

---

