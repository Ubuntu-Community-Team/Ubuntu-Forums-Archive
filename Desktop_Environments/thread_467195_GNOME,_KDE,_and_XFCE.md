---
title: "GNOME, KDE, and XFCE?"
date: 2007-06-07
forum: Desktop Environments
---

### Post by ciscoookid on 2007-06-07
Hi all, I was wondering, and I know this is possible in Fedora 7, if I can have KDE and XFCE installed as well as GNOME? 

If that is possible, could someone please tell me how to do it? 

Thanks

---

### Post by ajgreeny on 2007-06-07
Install kubuntu-desktop and xubuntu-desktop with synaptic, or preferably aptitude.  If you use aptitude and then decide you don't want one or both of them, aptitude will remove everything rather than just the meta-package.

Once you have them installed you can chose which to run at the login screen.

---

### Post by ciscoookid on 2007-06-08
Okay. Well, it would work except for a few things. I put in the commands, and it tells me to 

"Media change: please insert the disc labeled
 'Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter"

so, naturally, I put in the DVD, press enter, and it tells me the same thing. I try it again and again, but it still won't install. What do I do?!

---

### Post by diatribe on 2007-06-08
you're running ubuntustudio?  you may have to add the regular ubuntu repositories into your sources.list; i've not downloaded ubuntustudio; so I'm not sure

---

### Post by allix on 2007-06-08
> **ciscoookid said:**
> Okay. Well, it would work except for a few things. I put in the commands, and it tells me to 

"Media change: please insert the disc labeled
 'Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter"

so, naturally, I put in the DVD, press enter, and it tells me the same thing. I try it again and again, but it still won't install. What do I do?!

Disable the cdrom in synaptics repositories-dialog and then reload the repos. Synaptic will now fetch packages directly from ubuntu-servers.

---

### Post by ciscoookid on 2007-06-09
> **ajgreeny said:**
> Install kubuntu-desktop and xubuntu-desktop with synaptic, or preferably aptitude.  If you use aptitude and then decide you don't want one or both of them, aptitude will remove everything rather than just the meta-package.

Once you have them installed you can chose which to run at the login screen.

Okay, so I did that. When I log in, it automatically loads GNOME. I have Beryl set up as a startup program, and when I switch to KWin, I see no real changes in the system except the window decoration. Is there something else I should know?

---

### Post by PhatStreet on 2007-06-09
> **ciscoookid said:**
> Okay, so I did that. When I log in, it automatically loads GNOME. I have Beryl set up as a startup program, and when I switch to KWin, I see no real changes in the system except the window decoration. Is there something else I should know?
Select your environment from Sessions in the logon screen.

---

### Post by ciscoookid on 2007-06-09
> **PhatStreet said:**
> Select your environment from Sessions in the logon screen.

I figured that out as soon as I rebooted.. I feel like a jackass. Thanks everybody for your help.. I'm gonna go cry myself to sleep now..

---

