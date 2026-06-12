---
title: "Add skype in Messaging menu (Ubuntu 10.04)"
date: 2010-05-18
forum: Desktop Environments
---

### Post by fantom4ik on 2010-05-18
So to add skype in Ubuntu messaging menu must:
1. Install Skype 
```
sudo aptitude install skype
```
2. Open /usr/share/applications/skype.desktop
```
sudo gedit /usr/share/applications/skype.desktop

```
3. Add row
```
StartupNotify=true

```
4.Save and close file
5.Create and open new file /usr/share/indicators/messages/applications/skype
```
sudo gedit /usr/share/indicators/messages/applications/skype
```
6. Add row
```
/usr/share/applications/skype.desktop
```
7. Save and close
8.Restart or Log Out

---

### Post by luceerose on 2010-07-06
Should we also add;
/usr/share/applications/skype.desktop
to the
~/.cache/indicators/messages/seen-db.keyfile
file ???

---

### Post by shinzo on 2010-07-19
What is the exact result? Only to integrate Skype to the Notification Menu or also get incoming messages integrated?

---

### Post by beavis5551 on 2010-07-21
> **shinzo said:**
> What is the exact result? Only to integrate Skype to the Notification Menu or also get incoming messages integrated?

AFAIK result is only to integrate skype to the notification menu.
New messages from skype will pop up in the skype icon - not in the notification menu.

cheers,

beavis

---

### Post by shinzo on 2010-07-21
Ok, then it works on Ubuntu Lynx. A Skype-Button is integrated in the Notifier. And a click on it starts Skype. But when Skype is already running, it just tries to start Skype a second time.

I don't know if that's exactely like intended or just because I screwed up my Notifier while integrating Skype on my own. But I would prefer if a click on the Skype-Button would open the already running version and not open a new one every time. 


Greets.

---

### Post by antimirov on 2010-07-28
I'm wondering how to undone this. Now I have a Skype icon in messaging list, but it's not very useful. I removed all changes I've made, but the icon is still there. Will restart help, has anyone tried?

---

### Post by hugo87 on 2010-10-29
> **antimirov said:**
> I'm wondering how to undone this. Now I have a Skype icon in messaging list, but it's not very useful. I removed all changes I've made, but the icon is still there. Will restart help, has anyone tried?

```
killall gnome-panel
```

---

### Post by DirtyPC on 2010-10-29
> **antimirov said:**
> I'm wondering how to undone this. Now I have a Skype icon in messaging list, but it's not very useful. I removed all changes I've made, but the icon is still there. Will restart help, has anyone tried?
Go to terminal, killall gnome-panel

Edit: Sorry, didn't see the post above

---

### Post by fay_tonpou on 2010-10-31
> **shinzo said:**
> Ok, then it works on Ubuntu Lynx. A Skype-Button is integrated in the Notifier. And a click on it starts Skype. But when Skype is already running, it just tries to start Skype a second time.

I don't know if that's exactely like intended or just because I screwed up my Notifier while integrating Skype on my own. But I would prefer if a click on the Skype-Button would open the already running version and not open a new one every time. 


Greets.

you can write a launcher to check if it's already running : add this at /usr/local/bin/skype

```
#!/bin/bash

nbi=$(pgrep -c skype) 
if [ $nbi -ge 2 ];then
    echo "skype is already running"
else
    /usr/bin/skype
fi
```

---

### Post by joshrodgers on 2011-06-15
> **shinzo said:**
> Ok, then it works on Ubuntu Lynx. A Skype-Button is integrated in the Notifier. And a click on it starts Skype. But when [Skype integration]("http://www.3gcgroup.com/") is already running, it just tries to start Skype a second time.

I don't know if that's exactely like intended or just because I screwed up my Notifier while integrating Skype on my own. But I would prefer if a click on the Skype-Button would open the already running version and not open a new one every time. 


Greets.

I had the same issue in screwing up the notifier while integrating skype. Did u figure out anyhthing to not open a new one?

---

### Post by SaintDanBert on 2011-11-02
> **joshrodgers said:**
> I had the same issue in screwing up the notifier while integrating skype. Did u figure out anyhthing to not open a new one?

In the proposed run-once script consider:

**echo** will write to STDOUT from the shell

**notify-send** will create a pop-up on the desktop for something launched while the desktop is running.
```

# --expire-time milliseconds to leave display on screen
# first string -- appears as a title in the pop-up. I chose "Run-Once"
# second string -- whatever your message wants to be
notify-send --expire-time=3000 "Run-Once" $msg

```
See the man-page for **notify-send** for more details.

While this does nothing to intgrate app-lets running in the top panel notification area, it does help things feel more integrated with the desktop.

Cheers,
~~~ 0;-Dan

---

