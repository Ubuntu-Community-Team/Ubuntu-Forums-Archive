---
title: "A few basic how-to linux questions"
date: 2006-02-08
forum: Desktop Environments
---

### Post by stanleys on 2006-02-08
I've been using Ubuntu in and out but there's still a few very basic things that I don't know how to do.

 - I installed NetworkManager to help me manage my WiFi connections, but how can I make it start automatically on every reboot?

 - How do I change the default application for a particular filetype? ex. make XMMS the default app for mp3

 - What is the proper way to upgrade Apache2.0 to Apache 2.2?

 - I have the Logitech MX510, is there any gui interface to configure the extra buttons?

---

### Post by Theely on 2006-02-08
[QUOTE=stanleys]I've been using Ubuntu in and out but there's still a few very basic things that I don't know how to do.

 - How do I change the default application for a particular filetype? ex. make XMMS the default app for mp3
[/QUOTE]

I can only help you on this question, but its better then no help at all!

In either the Prefs or Admin menu there should be a Prefered Apps selection. You should be able to make your changes there.

Also, I don't know if its already included in the Ubuntu packages but XMMS use to need a special mp3 codex to play them that had to be downloaded and installed on their own. Like I said though, I don't know if that the case for Ubuntu.

---

### Post by bluevoodoo1 on 2006-02-08
[QUOTE=stanleys]
 - How do I change the default application for a particular filetype? ex. make XMMS the default app for mp3[/QUOTE]

Right click on an MP3.  go to properties > open with > click XMMS. All other MP3s should now open with XMMS.

---

### Post by dcstar on 2006-02-08
[QUOTE=stanleys]I've been using Ubuntu in and out but there's still a few very basic things that I don't know how to do.
.......
 - I have the Logitech MX510, is there any gui interface to configure the extra buttons?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

Also do a forum search on your wireless question, there are answers for that somewhere.

---

### Post by SickTwist on 2006-02-09
[QUOTE=stanleys]I've been using Ubuntu in and out but there's still a few very basic things that I don't know how to do.

 - I installed NetworkManager to help me manage my WiFi connections, but how can I make it start automatically on every reboot?

 - How do I change the default application for a particular filetype? ex. make XMMS the default app for mp3

 - What is the proper way to upgrade Apache2.0 to Apache 2.2?

 - I have the Logitech MX510, is there any gui interface to configure the extra buttons?[/QUOTE]

To make NetworkManager automatically start when you log-in, click on System-->Preferences-->Sessions, "Startup Programs" tab and then "Add". Type "nm-applet" (without quotes) for the name of the startup command. Click "OK" and finally "Close".

---

