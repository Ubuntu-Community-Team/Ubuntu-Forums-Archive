---
title: "need help.. using version 2.30.2"
date: 2010-11-10
forum: Desktop Environments
---

### Post by jjb945025 on 2010-11-10
hello. i reinstalled ubuntu 2.30.2 and now am able to open computer  janitor... now i have a different problem.. when i go to  system---->preferences or administration, isn't there supposed to be  an icon for the firewall? i remember there was in the last install. how  do i get it back there because i believe i had to do something in  terminal to get the icon there and cannot remember. also, when i clickon  tools in firefox, "stop private browsing" and "clear recent history"  are dulled out ( i cannot select either). am i already  browsingprivately? if so i didn't choose to be. i want to be able to  clear my browsing history and cannot..i also want to block incoming  traffic with the firewall  and cannot. any help would be greatly  appreciated. thanks again.   -joe

---

### Post by tom4everitt on 2010-11-11
> **jjb945025 said:**
> hello. i reinstalled ubuntu 2.30.2 

I think you may have confused the version number. 2.30.2 doesn't sound like an Ubuntu version. Check System->About Ubuntu to find out which version you are using. 
> 
and now am able to open computer  janitor... now i have a different problem.. when i go to  system---->preferences or administration, isn't there supposed to be  an icon for the firewall? i remember there was in the last install. how  do i get it back there because i believe i had to do something in  terminal to get the icon there and cannot remember. 

There are a number of utilities to manage your firewall in Ubuntu. At the core is always iptables, but there are several graphical interfaces to make it easier. One is Firestarter, which can be installed via

```

sudo apt-get install firestarter

```

(Or from Applications->Ubuntu Software Center in more recent Ubuntu versions.)

I'm not sure that's the one that used to be included by default, however (if there ever was one). 

Here is some more info (although slightly dated):
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/firewall-configuration.html)

On a general note, in System->Preferences->Main Menu, you can choose which icons are shown in the menus. I don't think you will find a firewall there before installing something, though.

> 
also, when i clickon  tools in firefox, "stop private browsing" and "clear recent history"  are dulled out ( i cannot select either). am i already  browsingprivately? if so i didn't choose to be. i want to be able to  clear my browsing history and cannot..

If "stop browsing privately" is grayed out, wouldn't that indicate you are not in private mode?

I'm not sure why clearing browsing history doesn't work. The brute way is to just delete the .mozilla/firefox folder in your home directory. That will also erase your bookmarks and other preferences, however.

---

### Post by jjb945025 on 2010-11-15
yea, i believe your correct about not being in private mode. i'm just gonna leave everything as is i guess, regarding that.      but thanks for all of your advice about it and the firewall.

---

### Post by wojox on 2010-11-15
2.30.2 is the Gnome version of Ubuntu your using. As far as Firefox what do you have Edit > Preferences > Privacy > Firefox will: Do what?

---

