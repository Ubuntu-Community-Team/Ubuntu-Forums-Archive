---
title: "need my wireless icon back !"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by tomaasj on 2007-07-07
Need help please,

realized that after custumizing the top panel that most probably I removed the icon 
(top right) which I click on to see if I'm still connected to the wireless network (it also shows the other networks available).  How do I get it back ?

Tomaasj

:(

---

### Post by hyperair on 2007-07-07
Open your Sessions Manager (System->Preferences->Sessions) and make sure that you have something to do with NetworkManager there, and checked. If it's there but unchecked, check it, otherwise add a new entry, with "nm-applet --sm-disable" for its command.

---

### Post by Alex&amp;Linux on 2007-07-07
Hey dude!
Im sure you could right click on your toolbar and "add to panel"
Chose network monitor, and later right click on that badboy and in the properties, should be able to change to a wireless interface!

There is also a handy command line tool that shows a wealth of information regarding wireless networking (ssid's in range, rssi, jitter, signal strength ect.), though I cant remember the command!

If anyone could bring that to my attention, that would be awesome!

---

### Post by tomaasj on 2007-07-07
Hey,

I got the network manager on the panel, but this is not the manager like the original (Feisty).  Right-clicking does not give me the wireless interface.  I cannot find the interface showing the several networks in my vicinity and or activating or chosing the network I want to access.  Session manager is OK.  I am in the process in tutorial and tips to make my desktop have an OS X look.  Can you give me further hint how to restore the icon ?

Tomaasj

---

### Post by hyperair on 2007-07-08
@Alex&Linux: The command's ```
iwlist wlan0 scan
``` though you should replace wlan0 with your appropriate interface name. Mine's called wlan0. You can discover the network interface name by typiing ```
iwconfig
``` and it'll show you all the interfaces, and which ones have wireless.

@tomaasj: sigh, looks like it's time to bring up a screenshot. I'll attach two screenshots here, one is with the Sessions window open, and the Network Manager option highlighted there. The second one is what is shown when you click edit. If you cannot find a Network Manager option there, just click add and copy whatever values are from the second screenshot.

---

### Post by tomaasj on 2007-07-08
Hi Hyperair,

I appreciate your help.  I did everything you explained.  I included the screenshot of my desktop after opening the network icon on the upper right corner.  Sofar so good.  But what I meant was that before I started to customize my desktop, when I opened the network manager icon I had a totally different and much simpler interface.  Visible were all the networks in the vicinity and I could easily switch bewteen them and they also were identified with their "regular " names not the cryptic ones I have now (see screenshot).  Can you advise me on this ?


Tomaasj

---

### Post by hyperair on 2007-07-08
Tomaasj, that's what's called the Network Monitor applet, not the same as the Network Manager applet I was talking about. I forgot to mention, but you'll have to restart, or just logout and log back in, or just run this command in your run dialog: ```
nm-applet --sm-disable
```

Also, make sure that ```
pidof NetworkManager
``` in the terminal yields some kind of number. Otherwise, the icon still won't show anyway. If there's no output from "pidof NetworkManager" then you must run ```
sudo NetworkManager
```, and check "pidof NetworkManager" yet again. If that still doesn't have any output, then run ```
sudo NetworkManager --no-daemon
``` and post the output.

---

### Post by tomaasj on 2007-07-08
Hey Hyperair,

Please find included two screenshots.  Within the terminal I added the commands.

typing "nm-applet --sm-disable" gave me a blinking cursor.  I also added "pidof NetworkManager".  I also  typed "nm-applet --sm-disable" in the Alt F2 window and got my prompt back in the terminal.  Then I continued with the other commands and got a return (4977, see screenshot).  Still no network manager applet visible ?

What is what I do wrong or simply do not get ?

Tomaasj

---

### Post by hyperair on 2007-07-08
Wait, so your icon refuses to come back no matter what you do? What about "pidof nm-applet". Wait, you said you accidentally removed something from your panel right? Try adding the notification area applet. See if that works.. unless you already have it there?

---

### Post by tomaasj on 2007-07-08
Hey Hyperair,

you are right, the notification area applet was what I was looking for.  Indeed I removed it while customizing my desktop.  EXCELLENT !!!

Really appreciate your help and patience !


Tomaasj

---

### Post by hyperair on 2007-07-08
Good to hear. I didn't really figure it out until I took some time staring at your panel.

---

### Post by flamacue on 2007-09-18
> **tomaasj said:**
> the notification area applet was what I was looking for.  Indeed I removed it while customizing my desktop.
Thanks for this thread, it helped me too.  :)

Just a little extra info, for anyone who had trouble deciphering the above, like I did:  the "Notification Area" applet is listed under the Utilities section, with the "i" icon (like "info", I guess).  It is shown in the 2nd attachment to post #8 of this thread.

I was stuck on that for a while, because the icon I needed to add didn't match the one I was missing!

@tomaasj:  perhaps you should mark this thread "Solved"?

---

