---
title: "Check if interface down -&gt; put up"
date: 2006-02-24
forum: Desktop Environments
---

### Post by HumBug on 2006-02-24
Hi,

i got my wireless usb stick working quite allright with the latest ndiswrapper (1.10). However i use ubuntu as some sort of server and every few days it looses connection with the wifi access point. I can see that at that moment the wireless network interface wlan0 is down. If i just put it up again the connection works ok again.
Now my question is: is there a way to start a process at bootup to check every few seconds whether wlan0 is down and if so, put it up again?

---

### Post by TrendyDark on 2006-02-24
You can always just check it yourself: ifconfig wlan0

---

### Post by HumBug on 2006-02-24
Well, not really.
I use it as a server, so i am not behind this pc. When it looses connection i have to drive home and get behind the pc and manually set the wlan0 up again...
That's why i want a program in the background to do this automatically.

---

### Post by audax321 on 2006-02-24
I wrote an init script for someone a while ago that did this. Here is the thread: [http://ubuntuforums.org/showthread.php?t=89169](http://ubuntuforums.org/showthread.php?t=89169)

It basically runs as a background process that pings a website... if the ping fails it runs a user specified script specified with the bring_interface_up variable in the /usr/bin/internetd script (or you could replace it with a command in the actual code below it) that does what the user needs.

---

### Post by HumBug on 2006-02-24
Thanks, i was looking for something like that. I'll try it tonight and let you know how it goes.

---

