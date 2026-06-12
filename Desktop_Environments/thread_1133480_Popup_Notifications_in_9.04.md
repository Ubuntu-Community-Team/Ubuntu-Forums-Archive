---
title: "Popup Notifications in 9.04"
date: 2009-04-23
forum: Desktop Environments
---

### Post by docjones2 on 2009-04-23
On the whole I like 9.04, the differences between it and the previous version are subtle but very welcome (ie I can now use WPA encryption because there are no more driever troubles!) except for one.  The Popup Notifications.

I hate them.

On the GUI settings application, the section pertaining to the popup notifications does not give the option to disable them.

How do I disable this feature?  It is particularly annoying (and compromising to my privacy) when I have pidgin running and every single message I receive is displayed as a popup notification.  Pidgin does not offer any GUI options for disabling popup notifications, but this is besides the point, since I just want them to stop completely.

Any good advice?

---

### Post by netJackDaw on 2009-04-23
I absolutely and totally agree that this new feature must be customizable. So far I am not as fed up with them as you seem to be docjones2. In some cases it is even a matter of privacy to be able to turn them off.

At tip to the distros: do not act as if you know better what your users want than they do themselves.

Add easy reachable settings for notifications and the ability to turn them off.

---

### Post by XeiaieX on 2009-04-23
I have not used JJ yet, but from what I have seen, the notifications appear to resemble that of Growl on OS X. I think I will love them!

---

### Post by docjones2 on 2009-04-23
> **netJackDaw said:**
> 
At tip to the distros: do not act as if you know better what your users want than they do themselves.


I have seen several instances of devs pompously criticizing users' criticism.  I hope this will not happen here...  The "Pop-up Notifications" item of the System>Preferences drop down menu was by default hidden on my installation, and when unhidden, it offered no way to disable the feature.  This implies that developers know this feature may be unwelcome but for whatever reason want it to be present.  I sincerely hope this doesn't become a classic case of the "silly end user doesn't know the first thing about a good desktop environment" response to serious criticism.  I can go on this for days, what's really important is...

I just want to know a quick and easy way to disable these notifications.  I am open to editing config files or whatever other type of file need be edited, I actually prefer it this way.

Thank you

---

### Post by mcduck on 2009-04-23
> **XeiaieX said:**
> I have not used JJ yet, but from what I have seen, the notifications appear to resemble that of Growl on OS X. I think I will love them!

More like Growl with zero configuration options. :/

Something like Growl would be very nice. What we have now is pretty but gets quite easily very annoying.

---

### Post by x58 on 2009-04-23
I have notification too, but it not bother me. I had before sound notification, but now it is gone.Anybody know how I can have back sound notification if somebody writes me at Pidgin? Thanks

---

### Post by hesjnet on 2009-04-23
Do you know if theese notifications also work with other IM client? not just Pidgin. I'm using Emesene.

---

### Post by Ramptu on 2009-04-23
I had the same gripe about the pidgin pop-ups every time I got IM or someone logged off/on. I got it turned off on my 9.04. I believe I turned off lib notify plugin under tools>plugins> and unchecked libnotify. You could try that.

---

### Post by ninjapirate89 on 2009-04-23
> **hesjnet said:**
> Do you know if theese notifications also work with other IM client? not just Pidgin. I'm using Emesene.

I use Emesene but I haven't had the chance to completely test compatibility with the new notifications. I know that when you get a new email Emesene will show the notification.

Edit -> Actually I think I had to use a plugin to get the notifications to work with it.

Edit2 -> One of my contacts finally signed on and the notifications do work with Emesene when you get a new message.

---

### Post by scottuss on 2009-04-23
> **hesjnet said:**
> Do you know if theese notifications also work with other IM client? not just Pidgin. I'm using Emesene.

Shameless plug: I'm running a poll on my website to see what applications people would like to see have the new notifications. Results will get posted on here, and forwarded to the developers of the projects to suggest that they implement it.

---

### Post by stringarray on 2009-04-23
I want to disable them too, especially for pidgin incoming messages. How do I do it?
:(
:confused:

---

### Post by Dougie187 on 2009-04-23
The notifications are a plugin in pidgin. You can turn them off if you want. I think the plugin is called Libnotify or something like that. Just go in there and you can select things that you want to get a notification about. It's not amazingly customizable, but it's not terrible either, especially since it is easy to turn off.

---

### Post by Eemeez on 2009-04-24
For I long time I have had a problem with my charger for laptop. It works few seconds (chareges), the stops (and the computer will say, that it's on battery power). After few seconds it charges again (on AC power).

So the problem is, if the power manager is turned on, it will show me a notification in every 2 seconds. It makes impossible to work with system.

At the moment I disabled the power manager, but I would like to be able to see, how much battery I have left, so it would be better, if I could change the settings for notifications. e.g what to show and what not.

---

### Post by wynneth on 2009-04-24
> **docjones2 said:**
> 
How do I disable this feature?  It is particularly annoying (and compromising to my privacy) when I have pidgin running and every single message I receive is displayed as a popup notification.  Pidgin does not offer any GUI options for disabling popup notifications, but this is besides the point, since I just want them to stop completely.

Any good advice?

Judging by my experience, it would seem that if you want to disable the new notifications you simply need to remove the notify-osd package. For some reason I didn't get the package by default on upgrade and still had notification-daemon so I was still seeing the old notifications. I have some opposite results on my end tho, as pidgin doesn't show ANY notifications via the ubuntu notify. LOL.

---

### Post by Judgegeo on 2009-04-24
> **Eemeez said:**
> For I long time I have had a problem with my charger for laptop. It works few seconds (chareges), the stops (and the computer will say, that it's on battery power). After few seconds it charges again (on AC power).

So the problem is, if the power manager is turned on, it will show me a notification in every 2 seconds. It makes impossible to work with system.

At the moment I disabled the power manager, but I would like to be able to see, how much battery I have left, so it would be better, if I could change the settings for notifications. e.g what to show and what not.

How about using Conky to display remaining battery? =)

---

### Post by Eemeez on 2009-04-24
> **Judgegeo said:**
> How about using Conky to display remaining battery? =)
Thanks. I think I will add it to Conky.

---

### Post by Judgegeo on 2009-04-24
> **Eemeez said:**
> Thanks. I think I will add it to Conky.

[http://ubuntuforums.org/showpost.php?p=7091994&postcount=6557](http://ubuntuforums.org/showpost.php?p=7091994&postcount=6557)

Nice little script for battery =).

---

### Post by Eemeez on 2009-04-27
> **Eemeez said:**
> For I long time I have had a problem with my charger for laptop. It works few seconds (chareges), the stops (and the computer will say, that it's on battery power). After few seconds it charges again (on AC power).

So the problem is, if the power manager is turned on, it will show me a notification in every 2 seconds. It makes impossible to work with system.

At the moment I disabled the power manager, but I would like to be able to see, how much battery I have left, so it would be better, if I could change the settings for notifications. e.g what to show and what not.

Can somebody suggest, how can I get rid of the power manager. I removed it from startup menu, but it comes back in certain times. For example, if I hit the VLC to full screen, again the power manager is on, and the notifications start to blink.

---

### Post by xienoph on 2009-04-27
I don't mind the notification ... as long as they're at the bottom right corner of the screen. 

Right now it's at the top right of the screen. I tried using System > Preference > Pop-Up Notification to change the position to bottom right, and it turns out that it's already set to Bottom Right. Changing the position to any of the other corners don't seem to do anything, based on the Preview. Am I missing something here? Why isn't it changing position?

---

### Post by hobophobik on 2009-04-27
I don't seem to be able to see "Pop-Up Notification" in my system preferences menu, and there is no option to show it in when using "Edit Menu".

How do I make this visible?

---

### Post by oweise on 2009-04-28
The menu item seems to be hidden in preferences by default. You can make it visible by editing your panel menu (Right-Click on Menu->Edit menu).

It has exactly two settings (roughly translated from german): 
- display style ("ubuntu" and "standard")
- position

None of them seem to have any impact. I get the same black notfications in the top right corner no matter what I set here.

I strongly appreciate a centralized notification system in ubuntu, but agree that it definitely needs more customization options to be well accepted. Growl is a good orientation for what a powerful notification system can offer.

---

### Post by handle1790 on 2009-05-18
> **Ramptu said:**
> I had the same gripe about the pidgin pop-ups every time I got IM or someone logged off/on. I got it turned off on my 9.04. I believe I turned off lib notify plugin under tools>plugins> and unchecked libnotify. You could try that.

That worked! Thanks! 

:popcorn:

---

### Post by jaburr on 2009-05-19
Thanks for the plugins/"libnotify popups" tip -- I was annoyed by the Pidgin popups too.

JB

---

### Post by kozian on 2009-06-20
I have a new 9.04 installation.
Seems like notify-osd makes this awesome notifications, but "pop-up notifications" in Administration menu is a "notification-daemon" feature

What to do:
Uninstall notify-osd, Install notification-daemon if not and kill notify-osd.

Now i'm using "old school" notifications on 9.04 :p

---

### Post by alexxroche on 2009-12-23
> The Popup Notifications.I hate them.

I don't hate them, but I would like to be able to turn them off. The Popup config has theme and location but no, "don't bother using up CPU and slowing gnome down with this thing."

Even better would be per-application, (i.e. I don't need an alert for volume control but I might not mind so much for rhythmbox.

alexx

---

### Post by alexxroche on 2009-12-23
# I tried 
killall notification-daemon
ps auwxf|grep notification-daemon|grep -v grep # to see if it was still running
#[ 
killall -9 notification-daemon 
#or
kill -9 $(ps ux|grep notification-daemon |grep -v grep|awk '{print $2}')  
# for those really stubborn processes (try without -9 first!)
#]
#and when that seemed to work I did
sudo apt-get -y remove notification-daemon
#and I also did
sudo apt-get -y remove notify-osd pidgin-libnotify # but I don't think that last one is needed

---

