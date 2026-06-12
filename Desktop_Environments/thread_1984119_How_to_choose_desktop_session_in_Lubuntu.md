---
title: "How to choose desktop session in Lubuntu"
date: 2012-05-21
forum: Desktop Environments
---

### Post by nigelhinton on 2012-05-21
Hello,

Just started using Lubuntu and it got me out of pickle as an upgrade to Ubuntu meant no Wine working for my key app and no TV too!

Lubuntu gave me both of these OOTB for which I am eternally grateful.


Need to install Fluxbox as I like it's immediate configurability and also will overcome the documented bug whereby Task Bar crashes when used with PCmanFM and several LibreOffice spreadsheets. (really disruptive).

Tried to install tint2 as a short-term fix but this just screwed up my taskbar area.

With Ubuntu just select a desktop using the login screen and then reboot.  Can't find similar with Lubuntu. Tried to set up in etc/xdg/xsession/Lubuntu/desktop.conf but not worked.

Is there a configuration guide for Lubuntu which covers how to select alternative desktops as per gdm in Ubuntu?

Any help gratefully received (I'm not technical but not afraid to use the CLI).

---

### Post by nothingspecial on 2012-05-21
Question moved to it's own thread.

---

### Post by nigelhinton on 2012-05-22
what does this mean?

is it meant to be useful?

---

### Post by nothingspecial on 2012-05-22
> **nigelhinton said:**
> what does this mean?

is it meant to be useful?

Moving your question out of a gigantic thread that had nothing to do with your issue was supposed to be useful, yes. :)

---

### Post by nigelhinton on 2012-05-22
> **nothingspecial said:**
> Moving your question out of a gigantic thread that had nothing to do with your issue was supposed to be useful, yes. :)

Supercilious - if it was in the wrong place then tell me and I'll remember for the future rather than provide petty, useless 'quotes'.
Sarcasm is usually the retreat of the social inadequate.


If you are 'moderating' this forum then you don't set a very receptive tone - particularly for those new to the forum.

It's a simple question which I'll repeat:  

How to change desktop in Lubuntu, particularly for Fluxbod because I've searched for a solution over the last couple of days to no avail and I don't want to keep rebooting when Lubuntu performs its taskbar bug.

If there is anyone with a SENSIBLE response, be pleased to hear it.

---

### Post by ankspo71 on 2012-05-22
Fluxbox can be started by logging out of Lubuntu to get to the login screen, then choose fluxbox in the session menu (the desktop selection menu) in the login screen, then proceed to log back in. 

Once you have logged in to your chosen desktop, your current desktop selection should then be automatically remembered by the system the next time you restart your computer.

The reason why a moderator moved your question was to help your question get seen by many more people, and to prevent possible distraction from the original thread. If your question was left in the original thread, then only the people interested in reading the other thread would have seen your question. So whenever we have a new question, it is better for us to click on the "new thread" button which begins a new separate topic, as opposed to clicking on a "new reply" button which continues a conversation in an existing topic. The new thread button is displayed on the forum pages that list available topics to read, and the new reply button is displayed when we are reading topics.

Hope this helps.

---

### Post by Rodney9 on 2012-05-22
**Tint2 Tutorial** - 

[https://code.google.com/p/tint2/wiki/Configure](https://code.google.com/p/tint2/wiki/Configure)

[http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/](http://crunchbanglinux.org/forums/topic/16997/how-to-latest-tint2-code-and-new-tint2-additions/)


**Fluxbox Guide**

[http://tinyurl.com/7yf5o6s](http://tinyurl.com/7yf5o6s)


Rodney

---

### Post by nigelhinton on 2012-05-24
Thanks Rodney,

I should have seen that straight away as it's pretty obvious really!

Before setting up Fluxbox, I'll try the tint2 solution around LXDE 'cos apart from the LibreOffice/taskbar issue, Lubuntu works really well for me.

Thanks again.

Nigel

---

### Post by nigelhinton on 2012-05-27
Rodney,

I'm still contemplating moving to Fluxbox but am wondering whether to dump Lubuntu early before I expend effort sorting out:

1)  An OS/Desktop that can't run basic office apps such as LibreOffice without freezing the taskbar is pretty shoddy.  I've lost data as a result of this 'feature' and there doesn't seem to be a solution under review except to work around using tint2 or going to another windows manager such as fluxbox.

2)  It appears that deleting applications is 'non-standard' as I've tried to purge gnumeric using a purge command as well as attempting to remove using Synaptic but it still appears on menus and more importantly remains the default spreadsheet.  I could alleviate this by attempting to change the mime defaults somewhere so that if I select on a spreadsheet it launches libreOffice calc. 

I would have thought is is logical for the app to disappear if you do either of these two things (purge or Synaptic delete) but this does not happen.  I understand that Gnumeric is in some Lubuntu 'meta-package' which may mean it has to be done in some other way, but frankly I don't give a stuff - just want to easily delete apps.

I'm sure there are fixes and work-arounds but the two problems above indicate that Lubuntu is not really sound.

If there is a valid reason why Lubuntu does not do these things logically, then it's probably best I look at another distro.

Is Lubuntu really 'desk-ready'?

Nigel

---

### Post by nigelhinton on 2012-06-04
**Lubuntu/LXDE had some problems:**

1)  Libre locked taskbar and frequently corrupted working files giving a 0 byte file - totally unworkable

2)  Couldn't get rid of Gnumeric - appeared on menus after purge and defaulted to Gnumeric when clicking on a spreadsheet file - unworkable

3)  Erratic Windows opening - sizing indiscriminate (probably could be fixed with some LXDE reconfiguration but Fluxbox fixed anyway)

4)  Erratic Network Manager (used with 3G mobile dongle).  Probably to do with nm-applet in taskbar/notification area.  Unworkable.


[B]Changed to Fluxbox:
[/B]

1)  Eradicated the Libreoffice taskbar problem - faultless

2)  Gnumeric menu references disappeared and now defaults to Libreoffice when opening spreadsheet - perfect!

3)  Windows open perfectly

4)  Network Manager (applet in Fluxbox notification area) now works faultlessly.

Also marginal increase in performance.

CONCLUSION:  wouldn't touch the Lubuntu/LXDE combo with a barge pole and suggest that it has some serious flaws.

Fluxbox installation now almost perfect.

Only outstanding issue is getting GTK themes to work with Fluxbox but have done this before with Ubuntu/FLuxbox so don't anticipate problems.

Will add some applets such as volume control later.

---

### Post by nigelhinton on 2012-06-24
**Default desktop manager not work properly as standard in Lubuntu:**

If you change the desktop manager on log-in to eg Fluxbox, the next time it boots up it defaults to the 'default' desktop Lubuntu/LXDE.  Very annoying as you then have to log out and login again, switching to Fluxbox.

I re-installed lxdm and it now retains the last chosen desktop as the default until such time as you actively change it.

---

