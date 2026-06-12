---
title: "[SOLVED] New Dell - Firefox addons won't install"
date: 2008-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Flyers2391 on 2008-09-10
I received my new computer yesterday and spent of good part of last night trying to figure out what is wrong.  I have deleted my firefox profile, copied my old profile and reinstalled firefox all with no luck.  
When I try to install any addon from synaptic or addons.mozilla.org they are listed as needing a firefox restart - everytime.
The only way I could get my past add ons running was to copy my old profile.  When I copied my old profile over, my past installed extension came over but I need to install a VPN connection for work (and would like to fix whatever the issue is at heart so I can install other extensions in the future).  I don't believe it's a rights issue because I installed Wine already without a problem.  

I don't want to install a fresh Ubuntu because I don't want to lose the DVD playback and video driver

Inspiron 530
Intel Core 2 Quad Processor Q6600 (8MB L2 cache,2.4GHz,1066FSB)
2GB Dual Channel DDR2 SDRAM at 800MHz- 2DIMMs
ATI Radeon HD 2400 PRO 128MB
250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache
Ubuntu 8.04 with DVD Playback

---

### Post by swegner on 2008-09-10
It's hard to say exactly what your problem is, but it's very possible that something's corrupted in your Firefox profiles or related.  It would be safe and easy to simply remove the Firefox user configuration folder, and start over from there:

> mkdir ~/backup && mv ~/.mozilla ~/backup/.mozilla

This will move the entire ~/.mozilla folder to a backup location.  This folder also contains profile data for other mozilla products, such as Thunderbird.  If you need to restore settings, you can simply move the folder back into your home directory.

Also make sure Firefox isn't open when you execute this command.

---

### Post by Flyers2391 on 2008-09-11
Alright I will try that next ... I guess I should reinstall firefox after that and see where I get?

---

### Post by swegner on 2008-09-11
You shouldn't need to reinstall Firefox at this point.  This will essentially erase all of the user-settings that Firefox can see.  Assuming Firefox was installed automatically with Ubuntu from the repositories, everything should be OK with it.

Let me know how it goes.

---

### Post by Flyers2391 on 2008-09-11
Thanks!  That worked for most plugins (so a step in the right direction) but for some reason the VPN plugin still won't work.  I get:

> Cannot automatically install the SSL-VPN plugin.

For security considerations, this browser requires that the plugin installation must be explicitly initiated by the user.

Click here to install the plugin. 
I click and it relaunches the download which stops downloading partially through, any ideas?  It has worked fine on my old 8.04 install with Firefox 3

---

### Post by swegner on 2008-09-11
Hmm, I'm not familiar with the plugin you're trying to install.  Do you have the link to a website that uses it?

---

### Post by Flyers2391 on 2008-09-11
it's an F5 firepass ... the one I'm trying to use right now is behind a login screen so you won't be able to get to the plugin

---

### Post by swegner on 2008-09-12
It doesn't look like anything I've ever used before, but I was about to find some simple instructions for it.  Here's what it says on the website:

> The plug-in installation process tries to use 'su' or 'sudo' utilities to elevate user privileges to perform the installation. Sometimes, due to policy restrictions, these privileges are unavailable. In this case, you can download the plug-in and other components, and install them manually.

So, it might be the case that the plugin can't access administrator rights.  At this point, I can think of two options:

1) Try to install it manually.  The website gives instructions that look very easy to follow here: [http://it.emory.edu/showdoc.cfm?docid=7429](http://it.emory.edu/showdoc.cfm?docid=7429) .  This is probably the safest and easiest solution-- try this first.

2) Run Firefox as an administrator.  Since the plugin is trying to use sudo or su, it might be best to simply run the browser under sudo.  Note that this will give Firefox elevated priveleges, and could be a security risk.  Execute the command, try to install the plugin, and then exit out of Firefox entirely.  In a terminal, type:
```
sudo firefox
```

Hope that helps

---

### Post by Flyers2391 on 2008-09-12
Thanks for all the help ... I tried to run sudo firefox and that still didn't work.  Now, I have to run sudo firefox to get my profile to appear.  All my bookmarks and saved passwords are gone :(

---

### Post by Flyers2391 on 2008-09-12
> **swegner said:**
> It doesn't look like anything I've ever used before, but I was about to find some simple instructions for it.  Here's what it says on the website:



So, it might be the case that the plugin can't access administrator rights.  At this point, I can think of two options:

1) Try to install it manually.  The website gives instructions that look very easy to follow here: [http://it.emory.edu/showdoc.cfm?docid=7429](http://it.emory.edu/showdoc.cfm?docid=7429) .  This is probably the safest and easiest solution-- try this first.

2) Run Firefox as an administrator.  Since the plugin is trying to use sudo or su, it might be best to simply run the browser under sudo.  Note that this will give Firefox elevated priveleges, and could be a security risk.  Execute the command, try to install the plugin, and then exit out of Firefox entirely.  In a terminal, type:
```
sudo firefox
```

Hope that helps

alright, after moving on from losing my profile while not su, I just moved the .mozilla folder and started from where I was at when I last backed up my profile.

I tried the VPN from other computer but changed my useragent to the same as mine on this computer and got the same result.  I will wait until they release a newer version and consider my problems fixed for now, thanks for the help

---

