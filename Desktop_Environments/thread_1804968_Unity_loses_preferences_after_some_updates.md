---
title: "Unity loses preferences after some updates"
date: 2011-07-15
forum: Desktop Environments
---

### Post by mola_samas on 2011-07-15
I've installed ubuntu 11.04 about 3 day ago. Everything was ok and I installed some software these days and didn't reboot. Today I've rebooted and my windows file systems didn't mount right away.

Besides that, the upper bar of the interfaces starts following the color scheme defined but as soon as I click on it, the layout crashes and it becomes different from the rest. I don't mind the color chage (even being impossible to mantain a standart among other bars) but, joining this with the file systems problem, I believe it something a little more deep in Unity configs. 

Where should I look for these configurations and how I revert them?

thx

EDIT: I typed "unity" in the terminal and I got the following message:

> ** (<unknown>:2422): DEBUG: Unity accessibility initialization
** (<unknown>:2422): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1366x768

** (<unknown>:2422): DEBUG: PanelController:: Added Panel for Monitor 0
** (<unknown>:2422): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:2422): DEBUG: PlaceEntry: Applications
** (<unknown>:2422): DEBUG: PlaceEntry: Commands
** (<unknown>:2422): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:2422): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:2422): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:2422): DEBUG: Setting to primary screen rect: x=0 y=0 w=1366 h=768
** (<unknown>:2422): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:2422): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2422): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2422): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2422): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2422): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2422): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2422): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

In fact, it was larger, but when unity crashes it stops to write on the file and I couldn't save the rest.

---

