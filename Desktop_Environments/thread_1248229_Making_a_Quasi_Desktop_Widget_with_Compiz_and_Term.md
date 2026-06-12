---
title: "Making a Quasi Desktop Widget with Compiz and Terminal"
date: 2009-08-23
forum: Desktop Environments
---

### Post by SteveONCSU on 2009-08-23
I've got a little widget I created using terminal and compiz.  I've got 'top' running in a terminal window with a special profile created to make it transparent.  With compiz I remove the window decorations and position it in the same place.  This runs at startup too.

Here is a screenshot: [http://overtonwebdesign.com/images/desktop.jpeg](http://overtonwebdesign.com/images/desktop.jpeg)

I really enjoy having this in the background.  My goal is to make my desktop very active with lightweight utilities like this.  My next task is getting 'sensors' parsed pretty enough and display here as well.  I'll also put dmesg or something similar to monitor recent log activity.

This is what I need help on....

I need to make my widget static so it cannot be clicked and it will remain static even when I click the hide windows button in the lower left corner.  I've looked around compiz settings but maybe I missed something.  The goal is to make it completely untouchable by anything.

If anybody has any ideas on how to parse the output from 'sensors' or show just important events from the logs I would be very appreciative as well. :P

---

### Post by SteveONCSU on 2009-08-24
I got part of my small project answered:

To get the recent log messages I'll create the same type of widget but issue the tail command:
> tail -n 20 -f /var/log/messages

To get the sensors displayed properly, I need to configure sensors through sensors.conf.  This article explains quite nicely: [http://www.linuxjournal.com/article/6712](http://www.linuxjournal.com/article/6712)

---

### Post by SteveONCSU on 2009-08-24
I was able to answer my own question, the setting is under the General tab in CCSM, first tab.  Uncheck the 'Hide Skip Taskbar Windows'.

---

