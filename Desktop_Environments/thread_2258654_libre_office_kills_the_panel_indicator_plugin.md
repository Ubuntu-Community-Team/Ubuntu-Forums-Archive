---
title: "libre office kills the panel indicator plugin"
date: 2014-12-29
forum: Desktop Environments
---

### Post by paulnewall on 2014-12-29
I am using the ubuntu 14.10 remix from Linux Format magazine with xfce desktop.
When I start libre office, I get a notification that the indicator plugin stopped working.
I cannot get this plugin to work while libre office is running.
After I close Libre office I can reload the plugin.

Is this a problem generally with ubuntu 14.10?

---

### Post by ajgreeny on 2014-12-29
Assuming this is a fully installed version of Libreoffice in the Linux-Format version, can you check to see if "Enable systray Quickstarter" is enabled in LO; you will find it at the bottom of the **Tools->Options->LibreOffice->Memory** tab and I know from personal experience that enabling that can cause some strange and unexpected things to happen, eg in a previous version of Ubuntu it stopped any logout or shutdown dialogue from appearing or working.

I assumed that it was sorted now, and I find LO quick enough starting as well particularly if using the ppa  **Version: 4.3.5.2 Build ID: 430m0 (Build:2)**, but it is worth checking and disabling the quickstarter to check it out if it is enabled.

---

### Post by paulnewall on 2014-12-30
I looked at the "Enable systray Quickstarter" it was not enabled. I experimented with enabling and disabling it and it had no effect on the behavior.
I can live with it, and will eventually install xubuntu from scratch if the problem does not go away.

---

### Post by ajgreeny on 2014-12-30
I have never used one of those LXF multi-DE versions of Ubuntu as it worries me to have so many full versions all crushed into the same OS; perhaps this is not a valid worry, but that's just my view.

I do have some KDE apps on my Xubuntu trusty, such as kmymoney2 and digikam, simply because they have no equals in my view, and of course they pull in a lot of other kde/qt libs, etc etc, but not the full DE with the plethora of different DE applications that I have always imagined those LXF OSs have; maybe I'm wrong.

Sorry my trick didn't work.  Does the startup applications list of this LXF version have any unexpected services starting at boot that you could remove and test their effect on your problem?  I'm grasping at straws here, but just trying to help.

---

