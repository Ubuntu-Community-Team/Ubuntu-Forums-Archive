---
title: "Empathy Notifications / Indicator Applet"
date: 2009-11-02
forum: Desktop Environments
---

### Post by undoIT on 2009-11-02
I decided to give Empathy a try since it is now the default chat app. There seems to be a lot lacking in comparison to Pidgin. The biggest issue I have is that the notifications are practically non-existent. I'd like something noticeable when somebody has sent a message.

I'm not sure if the notification balloon is not popping up when somebody sends a message or if it happens that I have always stepped away from my computer when somebody sent the message. There is no indication whatsoever that I have an incoming message. So, I click on the Indicator Applet and there is a message from somebody in there. Is there any way to configure the Indicator Applet so that it flashes or does something remotely notification-like when there is an unread incoming message? I don't see any configuration options.

Also, if I have a chat window minimized and somebody sends a message, there is only a change to talk balloon icon, rather than green circle. This is hardly noticeable and incoming messages are going unread for long periods of time. Is there a way to make the taskbar menu item flash or something?

And, I don't use Evolution email client. Is there a way to put Thunderbird in the Indication Applet and replace Evolution?

---

### Post by Bruce H on 2009-11-03
In your Contact List, go to Edit->Options. Open the Notifications tab. Select "Enable bubble notifications" and "enable notifications when the chat is not focused". For the flashing indicator in the task bar, select "Use message indicators". 

There is also a Sounds tab where you can enable various system sounds for events such as incoming IMs.

---

### Post by undoIT on 2009-11-03
Thanks Bruce. I enabled the not focused option and I'll give that a try. I think maybe when I saw that I figured that all possible notifications would be enabled because enable bubble notifications is a top level item and it was already checked.

---

### Post by undoIT on 2009-11-03
The not focused option solves the problem of the hard to notice notification when a chat window is minimized. However, the whole notification system is still based on the balloons, which only last for 5 seconds or so. If I step away from the computer or look out the window for 10 seconds, I may receive a new message but would have no way of knowing that it is waiting for a response. This is a major usability issue.

---

### Post by undoIT on 2009-11-08
Is there any way to have the chat window open (either focused or unfocused) when somebody initiates a new conversation? The indicator applet is really useless because it doesn't indicate anything. It just sits there as a static envelope and is nothing more than a drop down menu. It actually hides the notifications.

Perhaps Empathy and the Indicator Applet have some benefits from a developer's perspective, but I am having a hard time finding usefulness as a user. I'm not complaining just to complain, but I'm hoping to see these two applications improve. The thing is, when you switch back and forth between chat clients (i.e. Pidgin and Empathy) you end up losing all your chat logs. This is a drag because sometimes you need to go back and reference existing conversations. I'd rather not switch back to Pidgin, but Empathy with it's very lacking configuration options is in my opinion not ready for prime-time and shouldn't have been included as the default chat client yet.

---

### Post by undoIT on 2009-11-09
Okay, so I just now noticed that the indicator applet turns a slight shade of grey if there is something waiting in the queue (i'm using a dark theme). It would be great if there were some configuration options.

1. It would be useful to have an option to make the indicator applet blink or do something more noticeable. Often I'm so engrossed with what I'm working on, I don't even see that there is an incoming message in the queue and I end up missing an important message from somebody.

2. Another useful addition would be the ability to click the notification balloon when there is an incoming Empathy message and have it open or focus the chat window. It's a bit of a drag to have to click the little envelope icon and then select the queued item for every new incoming message.

3. When contacts login, they are listed in the indicator applet. This is confusing because it is mixed with incoming messages. Only incoming messages should be listed there. Really, there is no need to notify me that a user logged in during those times that I clicked open the indicator applet menu.

4. How about integration with Thunderbird and the option to remove Evolution? I don't use Evolution and sometimes accidentally click it when I'm trying to get to Empathy.

---

### Post by vipseixas on 2009-11-09
I just uninstalled the indicator-applet and switched back to Pidgin. It is impossible to use this new i-will-not-call-your-attention notification system.

> **undoIT said:**
> 
1. It would be useful to have an option to make the indicator applet blink or do something more noticeable. Often I'm so engrossed with what I'm working on, I don't even see that there is an incoming message in the queue and I end up missing an important message from somebody.

They say it is against Gnome HIG: [https://bugs.launchpad.net/indicator-applet/+bug/450398](https://bugs.launchpad.net/indicator-applet/+bug/450398)

> **undoIT said:**
> 
4. How about integration with Thunderbird and the option to remove Evolution? I don't use Evolution and sometimes accidentally click it when I'm trying to get to Empathy.

I know there is a Thunderbird plugin that does this magic, but I do not have the link right now. If you search the thunderbird plugins you might find it.

---

### Post by undoIT on 2009-11-09
Okay, so I'm not the only one bothered by the indicator applet. I think it is a design flaw that it is theme dependent and so subtle. It is hardly noticeable in dark themes when there is a notification. How difficult would it be to add the option for the indicator applet to blink when there is a message waiting?

Unfortunately, as Gnome progresses, I am liking Ubuntu less. And, I am finding that I prefer the default applications more and more in Kubuntu (Amarok vs Rhythmbox, Kate vs Gedit, Digikam vs Fspot, Kopete vs Empathy, etc etc, not to mention the overall more attractive aesthetics). There are some things I do like better in Gnome vs KDE (i.e. the archive manager, system monitor applet etc) but the scales keep getting stacked for KDE. It is too bad that Ubuntu / Kubuntu are not equally supported and that Canonical decided on Gnome as the flagship desktop environment.

That's the beauty of Linux. Lots of options. I may install KDE-based distros on both of my laptops next upgrade cycle.

---

### Post by vipseixas on 2009-11-11
> **undoIT said:**
> Unfortunately, as Gnome progresses, I am liking Ubuntu less. And, I am finding that I prefer the default applications more and more in Kubuntu (Amarok vs Rhythmbox, Kate vs Gedit, Digikam vs Fspot, Kopete vs Empathy, etc etc, not to mention the overall more attractive aesthetics). There are some things I do like better in Gnome vs KDE (i.e. the archive manager, system monitor applet etc) but the scales keep getting stacked for KDE. It is too bad that Ubuntu / Kubuntu are not equally supported and that Canonical decided on Gnome as the flagship desktop environment.

I prefer Gnome's overall look'n'feel, but unfortunately you are right, Gnome applications are getting behind KDE ones. But I am using other GTK apps instead of the Gnome defaults, like Exaile for playing music and Emesene for MSN protocol (and Pidgin when I want to use Gtalk).

I personally do not like KDE but my brother just replaced Ubuntu for Kubuntu for the same reasons and he is very happy with it.

---

### Post by JoelOl75 on 2010-01-17
> **undoIT said:**
> Okay, so I'm not the only one bothered by the indicator applet. I think it is a design flaw that it is theme dependent and so subtle.


You can remove and add any app you want to the indicator applet.

Hint:

/usr/share/indicators/messages/applications

This directory takes .desktop startup files.

Hint...Hint....


Also you can just ditch it and run any app in the tray (closing will not kill)

System>Preferences>Startup Applications> Add a new one.

Name it whatever:

In the command box type almost verbatim (replace the obvious)

sh -c "sleep 20;exec alltray -na /path/to/app"

Of course you need to install alltray (apt-get install alltray)

---

### Post by undoIT on 2010-01-17
> **JoelOl75 said:**
> You can remove and add any app you want to the indicator applet.

Hint:

/usr/share/indicators/messages/applications

This directory takes .desktop startup files.

Hint...Hint....


Also you can just ditch it and run any app in the tray (closing will not kill)

System>Preferences>Startup Applications> Add a new one.

Name it whatever:

In the command box type almost verbatim (replace the obvious)

sh -c "sleep 20;exec alltray -na /path/to/app"

Of course you need to install alltray (apt-get install alltray)

I don't want to get rid of it. I just wish it would do something more obvious than turn a slightly darker shade of grey when I have an incoming message that I have not responded to yet, or at least have some sort of configuration options in that regard.

---

### Post by ld1duck on 2010-02-04
It's hard to believe that there is no way to configure a flashing icon for messages received.  Gnome default applications are definitely falling behind KDE in usability and functionality.  It would be great if there were more support for Kubuntu.

---

### Post by Steve H on 2010-05-02
> **JoelOl75 said:**
> You can remove and add any app you want to the indicator applet.

Hint:

/usr/share/indicators/messages/applications

This directory takes .desktop startup files.

Hint...Hint....


Also you can just ditch it and run any app in the tray (closing will not kill)

System>Preferences>Startup Applications> Add a new one.

Name it whatever:

In the command box type almost verbatim (replace the obvious)

sh -c "sleep 20;exec alltray -na /path/to/app"

Of course you need to install alltray (apt-get install alltray)

Thanks! Finally got rid of Empathy!

---

### Post by DaymItzJack on 2010-05-02
It'd be nice if there was an option to just show the damn message instead of making you actually wait for it and click to see it.

---

### Post by vek on 2010-05-03
I really need that icon to blink.  I have a rather high resolution dual monitor set up and there's no way I'm going to see a tiny little yellow star appear at the bottom corner of the dock when someone is frantically sending me messages "where are you?  Why won't you respond?"

I've had to resort to turning off the feature and using pidgin with its own blinky icon and sounds and stuff, which is the worst possible case if you're interested in usability of a new feature (user turns it off).

---

### Post by ming0 on 2010-05-04
I'm similarly shocked that there are zero user options for this. Furthermore, if I have a chat window open, getting a new chat will not open a fresh tab in the chat window--I have to manually click the notification area to open the new chat. 

I finally gave up and switched to pidgin, which has its own quirks, but seems to be working much better for me.

---

### Post by phreadom on 2010-05-04
I feel I need to put in my 2 cents as well...

I have to say that Empathy has really been the #1 ***major*** disappointment in Ubuntu 10.4 so far.

The account configuration options feel lacking... when my Wifi connection was interrupted, all my accounts went off-line and wouldn't reconnect when my connection came back up. I couldn't find an easy way to tell them to reconnect, so I had to go into account options and manually disable and re-enable them all. (I have quite a few)

Another big pain is that I am an admin in some of the XMPP chats I'm in (such as for the website I work for), and Empathy has decided that I don't need to see the admin/moderator/user status of any of the users, and there is no way for me to enable this that I can find.

This extends to IRC where I also can't see any of the operator statuses etc.

On top of that, as others have said, the notification system is ***worthless***.

I had incoming messages sitting around for 14 hours before I noticed because Empathy not only didn't put them in my chat window, where they belong, but showed no sign to me of having been messaged. It was by sheer chance that I happened to stumble upon those missed messages.

Talk about taking a huge step backward.

I'm generally pretty pleased with Ubuntu 10.4 and have only noticed one other small gripe so far... but Empathy is a tremendous disappoint... to the point where I really see no option but to remove it and move back to Pidgin because Empathy is essentially completely unusable to me due to so many major shortcomings. :(

I hate to feel like I'm being too harsh... but chatting is something I basically do all day everyday, including as part of my job... and when this core aspect of my day is rendered unusable as almost the very first thing I dive into in the new Ubuntu release... it leaves a very sour taste in my mouth.

---

### Post by obscenic on 2010-05-10
YES! FINALLY FOUND SOME MINIMAL CUSTOMIZATION!

I had to dig this up because evolution just totally disappeared from the applet one day....

Head on over to /usr/share/indicators/messages/applications

In there you'll find the applications that are listed under the messages icon. You can add and remove them.  Each entry is a text file. The format is just 1 line, and the file should be named the same as the application ie "evolution".
Format: 

```
/usr/share/applications/evolution.desktop
```

etc... You can head on over to /usr/share/applications to check out the name of the application you're trying to add if you're trying to add one that disappeared.

---

### Post by thewump on 2010-06-03
Agreed. Notification FAIL.  IM is supposed to be "OI!!!!!" and it is "pst..."

K

---

### Post by fabounet on 2010-06-04
in the Messaging-Menu of GLX-Dock, the icon will animate when a new message arrives (or the icon will get the star, it's an option) ;-)

---

### Post by Sn3ipen on 2010-06-12
I have been using Empathy for some time now and installed latest version of Pidgin and i it's much better than Empathy. Wonder why they changed it in the first place?

---

### Post by noob555 on 2010-06-13
I agree with much of this thread.  

I think the major problem is with the indicator applet and the Me menu.  

[LIST]
[*]Why are they separate when both are required to run empathy properly?  The applet lets me know that I have a new message (if I can see it) and it lets me sign into chat.  And the Me menu lets me change my status and sign out.  So I have to have both to do even the most basic stuff.
[*]Why is the indicator applet attached to the volume control?  And why can't I easily separate them?  These two things have _*nothing*_ to do with one another.  
[*]Why doesn't the applet work with Thunderbird?  That seems both obvious and easy to accomplish.[/LIST]
All I need is an independent volume control, a new mail indicator that works with Thunderbird, and a new chat indicator that's a little more noticeable than moving from light gray to dark gray.  It seems obvious, but all of the workarounds seems lacking in one way or another. Hmmm... :(

---

### Post by undoIT on 2010-06-13
Yes, I agree that making the Me menu and the Mail/Chat indicator separate was a bad decision. The whole point of the Indicator applet was to consolidate the taskbar, but now it takes up more space and is more confusing.

To make the envelope icon more noticeable when there is a new message, try using the Ubuntu-Mono theme available with Lucid, instead of Humanity. Then the little envelope will turn green. It is poor design that the color of the indicator is tied to the icon theme and can't be customized within Empathy, but at least that is a work around until Ubuntu addresses these issues.

---

### Post by slash86 on 2010-06-13
please delete this.

---

### Post by xenzero on 2010-08-06
> **thewump said:**
> Agreed. Notification FAIL.  IM is supposed to be "OI!!!!!" and it is "pst..."

K

This says it all.  +1

---

### Post by denham2010 on 2010-08-07
I totally agree that Ubuntu seems to be going backwards.

1. What do volume control and email/im have in common? Separate these applets please.

2. What do im and shutdown/log out have in common? Remove shutdown from me menu.......

3. What happened to user freedom in UNE (has gone very windows/apple....ish with the lockdown)?

4. I do not wish to have my weather applet with the clock. separate these applets please.

This is just my opinion, but Ubuntu seems to be removing user choices and adding lockdown...which is much to windows/apple....ish for my liking.

There are many other issues I have developed with Ubuntu, over the last couple of releases, to many to list here.....

Watching 10.10 very closely, and sizing up other distros just in case......

---

### Post by sathyashrayan on 2010-11-06
Group,
  Before version 10.10(10.4) I could get an indication in my envelop with a star so that i can sense that some has messaged me and its in queue. After the upgrade to 10.10 this does not seems to be working. But today there was an update in kernal image. These indicator seems to be working.

I hope the flash streaming problem might also be solved too..

---

### Post by RomanIvanov on 2012-10-23
try [http://askubuntu.com/questions/198670/is-there-any-way-to-show-amount-of-missed-empathy-messages-in-the-launcher-icon](http://askubuntu.com/questions/198670/is-there-any-way-to-show-amount-of-missed-empathy-messages-in-the-launcher-icon)
to ease a problem.

---

