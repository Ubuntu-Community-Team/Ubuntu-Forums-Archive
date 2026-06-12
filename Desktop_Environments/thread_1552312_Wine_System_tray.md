---
title: "Wine System tray"
date: 2010-08-13
forum: Desktop Environments
---

### Post by jarviser on 2010-08-13
I have been pulling my hair out trying to find out why the Wine System Tray suddenly started appearing in its own little window when running Netmeter, cluttering up the desktop. I searched the web in vain, back many tears, most people saying they couldn't understand it when it happened to them.

Then I realized that the last thing I did was to stop Cairo Dock (the novelty had worn off!) and to move the Gnome Panel to the BOTTOM of the screen in place of Cairo.  I suspected this was making the Wine System tray homeless.

So I moved the Gnome panel back to the TOP, restarted Ubuntu, stopped and restarted Netmeter and the Netmeter icon appeared back in the panel where it belonged.

Would I be correct in thinking that Wine System Tray will only stay in the panel if the panel is at the top of the screen?

---

### Post by jarviser on 2010-08-13
Hmmm wasn't that. It just came back again.

If anyone knows why my Wine System tray has gone solo and set itself up on the desktop instead of in the panel, please let me know. Thanks in advance.

[IMG]http://www.jarviser.co.uk/jarviser/miscpics/winetray.png[/IMG]

---

### Post by Alere123 on 2010-08-14
I don't know but I've had the same problem

Worked it out!! you need the notification area on you top panel: right click on the panel, click add to panel and then search for notification area and add it then close wine apps and the re open

---

### Post by jarviser on 2010-08-14
I think you could be right. It's back where it should be now. Problem is the notification area does not show up if it's empty. I had 3 of them at one time!
 I just need to know why my notification area seems to drop off the panel!  I reckon it's something to do with Pidgin or Skype or some app I played with recently. 
I just did a re-install of 10.04 keeping all my . files in my home partition intact (so I don't have to re-install MS Office etc) and see what happens.  

Currently netmeter shows in the panel notification area as it should.

I will not mark this solved until I am happy it stays that way, but thanks again.

EDIT:  Seen the link - Cool desktop m8!

---

### Post by Alere123 on 2010-08-14
Hmm yea it doesnt show unless you have programs up which can be confusing buti dont know how to mak it stay that way sorry

and the desktop isnt mine but mine is basiclly the same just with a bottom and top panel instead of a dock :L

---

### Post by jarviser on 2010-08-21
Marked Unsolved - it just comes back when it thinks fit. One day it's there, next day it's gone. Seems random.

EDIT:

I wonder if it's because Netmeter (in Wine) is in the start-up applications and sometimes it starts before Gnome Panel has had chance to start?

---

### Post by schtufbox on 2010-08-21
> **jarviser said:**
> Marked Unsolved - it just comes back when it thinks fit. One day it's there, next day it's gone. Seems random.

EDIT:

I wonder if it's because Netmeter (in Wine) is in the start-up applications and sometimes it starts before Gnome Panel has had chance to start?
Give it a delayed start, see if it makes a difference.

---

### Post by jarviser on 2010-08-21
Thanks but I don't see any delay option in the startup applications menu.

---

### Post by Alere123 on 2010-08-22
To delay you'd have to start it manually I think

---

### Post by ashimjgec on 2012-09-26
> **jarviser said:**
> Hmmm wasn't that. It just came back again.

If anyone knows why my Wine System tray has gone solo and set itself up on the desktop instead of in the panel, please let me know. Thanks in advance.

[IMG]http://www.jarviser.co.uk/jarviser/miscpics/winetray.png[/IMG]

Greetings all... May be its too late, coz its late 2012 and the last post is of 2010, but I am sharing my solution.
I have found a solution that worked for me. Actually the orientation of "Notification Area" in Gnome panel is "right". Means every icon will be placed on the right-side. so you need to give some space to the right side of notification area to be able to display notification icons. The thing I did to make easier for understand is make one small panel and placed the "Notification area" applet in the panel and to the very right-side. And you can see from the screen shot, I am running no-ip windows software via wine and its also added in the startup list.
[IMG]http://imageshack.us/a/img684/8104/screenshotxpi.jpg[/IMG]

---

### Post by howefield on 2012-09-26
Old thread back to sleep.

---

