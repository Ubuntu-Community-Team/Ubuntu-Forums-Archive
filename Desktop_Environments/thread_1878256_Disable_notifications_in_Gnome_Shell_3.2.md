---
title: "Disable notifications in Gnome Shell 3.2"
date: 2011-11-09
forum: Desktop Environments
---

### Post by volkerbradley on 2011-11-09
Is it possible to turn off Notification messages in the bottom right corner of the screen when using Gnome-Shell 3.2?
Right now I see a notify-send message for every phone call I have made with Google Voice.  I made 10 phone calls and I see 10 notifications right now. I also see that I have a mounted removeable device after I have clicked on the device in Nautilus.  I obviously already know that the device is mounted and don't need to see this notification.
I prefer not to see these messages.  Any way to keep them from appearing?

---

### Post by Copper Bezel on 2011-11-09
It turns out that checking on autorun-never in dconf-editor under org > gnome > desktop > media handling prevents the popups for Nautilus mounting drives. I haven't seen the messages for Google Voice - I've only made one call since upgrading. (Sorry!)

---

### Post by volkerbradley on 2011-11-09
Wished that I could find this.  I opened the dconf-editor which evidently seems also to be named the gconf-editor. I cannot find org and therefore cannont find gnome > desktop > media handling either.  What am I missing?

---

### Post by cbowman57 on 2011-11-09
dconf-editor & gconf-editor are two different apps.

If your system doesn't have dconf-editor installed you need to sudo apt-get install dconf-tools.

---

### Post by Copper Bezel on 2011-11-09
Eep. Sorry, yes, it's in the repos but not installed by default, and it didn't occur to me that you probably wouldn't have it already. Thanks for the correction.

---

### Post by volkerbradley on 2011-11-10
Thanks for pointing out the dconf-editor.
However, using the instructions provided, the Removeable Devices notification continues to show up for me.
I have included the screenshots of exactly what I did.
[IMG]http://173.14.158.29/.download/dconf-editor.png[/IMG]
[IMG]http://173.14.158.29/.download/Open_removeable_device.png[/IMG]
or
[IMG]http://173.14.158.29/.download/Mount_removeable_device.png[/IMG]
The unwanted Removeable Devices icon continues to show up whether I have clicked on Open or Mount.  Example below:
[IMG]http://173.14.158.29/.download/Removeable_devices.png[/IMG]
What am I missing?

---

### Post by Copper Bezel on 2011-11-10
I guess I misread you. I knew you were referring to the notification tray in reference to Google Voice, but I assumed you meant the center pop-up regarding the removable drives. I don't know of any way to permanently remove that tray item.

I don't think you would actually want to remove it, though. It stays out of the way unless you access the tray or jump to the Overview, and you need it to eject drives, anyway (not just the external HD, but flash drives, CDs, etc.)

---

### Post by volkerbradley on 2011-11-10
Thanks for responding
It's a personal preference I guess.  I definitely would like to turn this off.  Never have needed this notifier to disable external HD's, flash drives, CD's, etc.. I just do it with Nautilus.
Don't want to see 10 notifications either when I have made 10 phone calls with Google Voice.  Just produces a lot of clutter and multiple clicks are needed to get rid of the Notifications.

---

### Post by Copper Bezel on 2011-11-10
Well, agreed - the phone notifications are strange and bothersome, and I don't know how to prevent that. The removable drives thing, I can understand your preference (but it's at least working as designed, and it should only ever be one icon in the tray no matter what you have connected.)

Are you using Google Voice through the main web interface, through your Gmail inbox, or through a dedicated GTalk-compatible client?

---

### Post by volkerbradley on 2011-11-10
I open Firefox 8.0 and go to [https://www.google.com/voice/](https://www.google.com/voice/) which is automatically changed to [https://www.google.com/voice/#inbox](https://www.google.com/voice/#inbox).  I click on Call and put in the number or the name of the contact. This causes a notify send icon to appear and also a message in google mail stating that I have a call.  I click on Answer and then the phone rings the person's phone who I am trying to reach. After I have completed the conversation the notify-send icon remains.  Here is what things look like after I have made three calls:
[IMG]http://173.14.158.29/.download/Multiple_notifications.png[/IMG]

---

### Post by Copper Bezel on 2011-11-10
Can you just disable desktop notifications in the Google Talk Plugin, then (through Google Voice settings) or would that interfere with your ability to receive calls?

Edit: Incidentally, I'm also beginning to understand the frustration with the lone Removable Devices icon. I've never seen my tray with less than four items (Dropbox, clipboard manager, Jupiter, and Removable Devices) but when you don't have any need for the whole tray, it does seem like an irritating extra UI element. If we can get the calls thing sorted, would you also like to hide the tray completely? It didn't occur to me until now, but you can do so with a tweak to the Shell theme.

---

### Post by volkerbradley on 2011-11-11
> **Copper Bezel said:**
>  Would you also like to hide the tray completely? It didn't occur to me until now, but you can do so with a tweak to the Shell theme.
Yes, I would like to hide the tray completely.  That would be perfect.

---

### Post by markbl on 2011-11-11
> **volkerbradley said:**
> Yes, I would like to hide the tray completely.  That would be perfect.
Click on your name in the top right corner and turn notifications off?

---

### Post by volkerbradley on 2011-11-11
Yes, I had already turned of Notifications as you suggested.  
Unfortunately, this has no effect on the "Removeable Devices" and "notify-send" notifications.  They continue to appear. 
Also, I could find no documentation anywhere how to turn of the notification-send notifications within google talk or google voice.

---

### Post by Copper Bezel on 2011-11-11
I'm lost on the desktop notifications. I can turn them off in Gmail, under Settings, but the same thing option isn't present in Voice, and here's the funny bit: ostensibly, they only work in Chrome. But I think that's unrelated, because Chrome draws its own little notification window rather than using notify-send.

I don't like the idea of your invisible tray stacking up with a few dozen call notifications, but you can make this edit in the CSS. Find the bit that looks a bit like this and change the size to 0.

```
/* Message Tray */
#message-tray {
    color: #fff;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(0,0,0,0.0);
    background-gradient-end: rgba(0,0,0,0);
    height: **0px**;
}
```

---

### Post by volkerbradley on 2011-11-12
> **Copper Bezel said:**
> ...You can make this edit in the CSS. Find the bit that looks a bit like this and change the size to 0.

```
/* Message Tray */
#message-tray {
    color: #fff;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(0,0,0,0.0);
    background-gradient-end: rgba(0,0,0,0);
    height: **0px**;
}
```

Thanks for replying again.
For my own education, which CSS file do I edit?

---

### Post by Copper Bezel on 2011-11-12
Oh, sorry. It's gnome-shell.css under the shell theme's folder, whichever one you're using.

---

### Post by crdlb on 2011-11-12
The main issue is that GNOME Shell has changed the default semantics of notifications. They persist in the message tray unless the "transient" hint is set.

I guess it's google-talkplugin that is using notify-send?  If it calls notify-send and doesn't hardcode the path, you could make a ~/bin/notify-send containing:```

#!/bin/bash
/usr/bin/notify-send --hint int:transient:1 "$@"

```

If they did hardcode /usr/bin/notify-send, you could rename /usr/bin/notify-send and put a similar wrapper script in /usr/bin.

---

### Post by volkerbradley on 2011-11-13
> **crdlb said:**
> ...I guess it's google-talkplugin that is using notify-send?  If it calls notify-send and doesn't hardcode the path, you could make a ~/bin/notify-send containing:```

#!/bin/bash
/usr/bin/notify-send --hint int:transient:1 "$@"

```

If they did hardcode /usr/bin/notify-send, you could rename /usr/bin/notify-send and put a similar wrapper script in /usr/bin.
It tried entering the "/usr/bin/notify-send --hint int:transient:1 "$@" and received a message stating that I had not set the summary. Don't know anything about the summary.
Then did: ```

mv /usr/bin/notify-send /usr/bin/notify-send.bak

```
This seems to have achieved exactly what I want.  No more of those pesky notifications.  Hopefully, this will not result in some other unintended problem.

---

### Post by crdlb on 2011-11-13
> **volkerbradley said:**
> It tried entering the "/usr/bin/notify-send --hint int:transient:1 "$@" and received a message stating that I had not set the summary. Don't know anything about the summary.[/code]
It's supposed to be a wrapper script; the "$@" will be replaced by any arguments passed to the script. The idea is to make usage of notify-send contain "--hint int:transient:1" by default, which will prevent the messages from being left in the tray.

> Then did: ```

mv /usr/bin/notify-send /usr/bin/notify-send.bak

```
If you want to do that, you would be better off undoing that and removing the libnotify-bin package. Note that many applications use libnotify or the DBus API directly, and they will still work.

---

