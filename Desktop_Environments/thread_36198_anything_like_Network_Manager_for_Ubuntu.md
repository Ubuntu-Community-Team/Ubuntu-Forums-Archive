---
title: "anything like Network Manager for Ubuntu?"
date: 2005-05-22
forum: Desktop Environments
---

### Post by testingubuntu on 2005-05-22
Hi all I travel quite a bit so I'm not usually connected to the same wireless network. 
When I'm home i can connect to my wireless AP  without a hitch.  I went to y brothers house last night and couldn't connect ot his AP.  I tried creating a new location and entering all that warm fuzzy stuff. It just wouldn't connect. In Fedora Core, there is a application called NetworkManager.  It allows you to connect to any wireless or wired network my simply entering the required info. it doesn't use the wireless tools or any config files. it uses the regisrty og gconfiguration editor to save all the required info.  So my questions is Id there a application like this for Ubuntu? 

here is the link
[http://people.redhat.com/dcbw/NetworkManager/howitworks.html](http://people.redhat.com/dcbw/NetworkManager/howitworks.html) 
here is a link to see it 
[http://www.fedorajim.homelinux.com/pages/router-set-up.html#LinuxPC](http://www.fedorajim.homelinux.com/pages/router-set-up.html#LinuxPC)

---

### Post by f.prisson on 2005-05-22
> I tried creating a new location and entering all that warm fuzzy stuff. Did you try to generate different profiles in System -> System Management -> Network or what caused trouble?

---

### Post by anders.ostling on 2005-05-22
Hi

there is a deb package named netapplet that resembles NM. The most obvious difference is that you have do manually switch to your wireless. Works fine for me, I have a wired connection at work (auto on of course) and a wireless at home (can select it it from a panel menu, just like NM). You can also configure other WIFI nets if you have the ESSID and wep key. Actually it will scan for network and present them in the dropdown menu together with a padlock (for protected networks). Anyway, try it. Until NM is ported to Ubuntu it will do the job for me ...

Anders

---

### Post by Ainvar on 2005-05-25
NetApplet looks like a frontend for the network profiles in gnome which seem to really blow a$$ everywhere. When I am at work I want to have a profile for a static IP and then a profile for a DHCP Profile for when I am not at my desk. Then at home I want to have a profile for both wired and wireless where I use static and then a profile for a buddies house that is dhcp with a diffrent wep key.


Now I am able to create the profile and I am able to switch from one to the other pretty easily except for the static profiles which like to loose there gateway IP addresses.

This makes it pretty useless to me since I have to always manually add the gateways to the profile I am using instead of just easily switching from one profile to another.


If there is a better  way please let me know but the searches I did on this forum came up with nothing of use for me.

---

