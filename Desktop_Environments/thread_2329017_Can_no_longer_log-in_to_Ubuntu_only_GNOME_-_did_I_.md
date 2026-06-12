---
title: "Can no longer log-in to Ubuntu only GNOME - ?did I &quot;break&quot; my distro?"
date: 2016-06-27
forum: Desktop Environments
---

### Post by thedoctor818772 on 2016-06-27
Good Morning. 

I wanted to try out GNOME 3 and so I added the GNOME 3 ppa to my list of ppas. However, when I went to reboot, and checked for options the only one I saw was the "footprint" for GNOME and not the icon for Ubuntu. If I click instead on the Guest log-in I get only the Ubuntu icon and not the GNOME one but when I log into the guest Ubuntu "side", I cannot connect to my wireless router. Please assist me as I am somewhat new to this and all I want/wanted to do is have the option to log-in to either GNOME or Ubuntu to try GNOME out and possibly keep both. I hope I have not broken my distro here.

Thanks,

-Michael Dykes

---

### Post by grahammechanical on 2016-06-27
Did you click on that gnome footprint icon? When we install an alternative desktop we get an icon on the password panel. It usually has a drop down menu listing the alternative sessions.

I am concerned that you added the Gnome 3 PPA. That is fine if we are running with Ubuntu Gnome but it is not the way to get Gnome 3 shell if we are running with Ubuntu. I certainly would not do it that way. But then again I would not add an alternative desktop in the first place. I would dual boot. Slightly less convenient but easier to get rid of.

If you are running Ubuntu Gnome then adding the Gnome 3 PPA does not bring in alternative log in options. At it didn't the last time I tried Ubuntu Gnome.

Regards.

P.S. anyone can get a session using the guest login option. We would not want anyone messing with our OS. That is why the guest session is very restricted as to what can be done when in it.

---

### Post by thedoctor818772 on 2016-06-27
I only got a password panel on the footprint icon and no Ubuntu icon showed up at all. As the pictures below indicate once I clicked on the footprint icon, the icon disappeared and so did the password panel. I then had to click on another portion of the (please excuse my terminology here) "welcome" screen to get the icon and the panel to reappear.






[ATTACH=CONFIG]269816[/ATTACH][ATTACH=CONFIG]269817[/ATTACH]

---

### Post by CantankRus on 2016-06-27
The only updates I can see for xenial In the gnome3 ppa are for nautilus and bluetooth.
Did you enable the GNOME3 Staging PPA?
> This PPA will be used to test uploads before they are uploaded to the main archive for the coming Release.

=== *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

**If they break your system, you get to keep both halves**.

Use ppa-purge to revert to official packages.
[**_[COLOR="#B22222"]HOW TO USE PPA PURGE[/COLOR]_**]("http://www.ubuntubuzz.com/2012/02/newbie-guide-how-to-use-ppa-purge.html")
***NB:** The ppa must still be enabled to use ppa-purge.

This will give you a list of enabled ppas in the right form to use with ppa-purge.
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*.list); do egrep -v '^#|^ *$' ${PPA_FILE} | grep "ppa.launchpad.net" | cut -d "/" -f4-5; done
```

---

