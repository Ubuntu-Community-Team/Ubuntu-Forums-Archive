---
title: "Setting up Ubuntu as web browsing terminal"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Fireweaver on 2006-08-23
I have an interesting scenario involving setting up Ubuntu on a new machine.  

I have set up Ubuntu on my home machine and have been using it quite happily for some time now, enjoying the wealth of capabilities the OS enjoys along with it stability and ease of use.  As a result, when a co-worker stated that he needed to set up a low cost computer to allow customers to browse the web while they wait, I immedeately suggested Ubuntu as an approachable, open-source alternitave to an expensive OS.

The idea was accepted, but now I am faced with customisng an install of Ubuntu so as to disable the broad range of functions which I like it for.  Specifically, the new machine should

-Be able to browse the web via a TCP/IP connection auto-configured through DHCP
-Immedeately launch a web browser upon booting up
-allow users to begin using it without entering a login or password
-dissallow users from launching any programs other than the web browser
-dissallow users to change any critical settings or save any files
-dissallow users from going to "adult" oriented websites
-be as resistant to spyware and viruses as is feasable.

I've gotten as far as creating a new user account which does not have write access to any folders and is automatically defaulted to on login, but the rest of the problems have me scratching my head.  Any suggestions would be appreciated.

Thanks in advance!

---

### Post by Tomosaur on 2006-08-23
[This link](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-other-kiosk-configs.html) may prove useful. Running firefox is as simple as adding it to the 'sessions' menu.

---

