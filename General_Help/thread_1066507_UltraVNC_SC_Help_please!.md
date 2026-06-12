---
title: "UltraVNC SC Help please!"
date: 2009-02-10
forum: General Help
---

### Post by x C0MMAND0 x on 2009-02-10
Alright,

So I set up a custom UltraVNC Single Click app ([http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)), that is all good.

I set up port forwarding on my router to forward ip ports 5500 TCP to my pc's Ip address.  In my Single Click settings for the host/port, I used (ip.add.re.ss:5500) (ip from whatismyip.com).

I have tried using ```
wine ultravncviewer.exe -listen 5500
```

And also ```
vncviewer -listen -encodings "hextile copyrect"
``` (which I read somewhere is supposed to work).

I have had some of my friends test the app I made while I am listening on the proper ports, but I can not get it to work.

Has anyone else gotten UltraVNC SC to work using Ubuntu as the host machine?  Also, my friends have been trying to connect from Vista, but it is supposed to have Vista support.  You can't run the executable under wine so I cant test from a linux PC elsewhere, but my main idea is to use this to help my friends at college with their PCs as I'm the "techie go to" for my group of buddies.

Any help is greatly appreciated.

---

### Post by dixonstalbert on 2009-02-10
hello commando

I have ultravnc sc set up on ubuntu hardy.

I have a LAN at home so I made a helpdesk.txt with 2 entries; one that someone on the internet could use to link to my ultravnc, and one that someone on my home LAN could use. 

I set up my laptop with windows xp beside my ubuntu desktop and ran SingleClick on the laptop. 

By examining the logs on the 2 computers, and my router I could figure out where things were getting blocked.

I believe I installed Firestarter on my Ubuntu and disabled it during a connection and this got things working for me. (Firestarter gives nice log output of current connections and events which are helpful, but sometimes it does not play nice with NetworkManager and will often give you grief.)

I copied the shortcut to UltraVNC Viewer (listen mode) to my desktop and it worked with SingleClick without any modifications.

Here is the copy of the command line from the desktop launcher.

```
env WINEPREFIX="/home/dixon2/.wine" wine "C:\Program Files\UltraVNC\vncviewer.exe" -listen
```

here is my helpdesk.txt (I have my router set to give the static IP of 192.168.0.100 to my ubuntu desktop)

Hope this helps!

```
[TITLE]
UltraVnc SC

[HOST]
DOUBLE CLICK HERE TO CONNECT
-connect dixons.homeip.net:5500 -noregistry

[HOST]
DOUBLE CLICK HERE TO CONNECT
-connect 192.168.0.100:5500 -noregistry

[TEXTTOP]

[TEXTMIDDLE]

[TEXTBOTTOM]

[TEXTRBOTTOM]
 (empty to clean line)
[TEXTRMIDDLE]

[TEXTRTOP]
Ultravnc PC support
[TEXTCLOSEBUTTON]
Close
[TEXTBUTTON]
More Info
[WEBPAGE]
http://www.ultravnc.net

[BALLOON1TITLE]
Trying to connect
[BALLOON1A]
line 1
[BALLOON1B]
line 2
[BALLOON1C]
line 3
[BALLOON2TITLE]
Connected to
[BALLOON2A]
line test1
[BALLOON2B]
line test2
[BALLOON2C]
line test3
[DIRECT]

```

---

### Post by x C0MMAND0 x on 2009-02-11
Thank you very much.  I was able to connect INTERNALLY from an XP computer using my hosts ip 192.168.1.103, but I still have not had any of my friends able to connect externally. 

I set up port forwarding for port 5500 to my host computers ip, and I tried running the application without my firewall enabled on the router as a test, and I do not have guard dog or firestarter...

Im trying to diagnose why an external connection would not work.  It would have to be something with my router settings, right?  But what?

Thanks again for your help I REALLY appreciate it.  I have wanted to get this working for a very long time now...

---

### Post by x C0MMAND0 x on 2009-02-11
Any other ideas?

---

### Post by dixonstalbert on 2009-02-14
I agree with you; if you can connect from a SingleClick started from a computer on your LAN, you know your desktop setup should be okay and problem must be somewhere else.

I just asked a friend on the internet to try and connect to my computer. First he didnt understand how to use SingleClick; I had used the old generic SingleClick template  and he couldnt figure where to "double-click". Make sure other person is correctly starting it; they should have a little yellow and black icon in lower right corner when app is running 

Next, his ISP has an automatic firewall and he kept selecting "Quarantine" because that is what he always does with the pop-up message. I explained to him that in this case he should select "ignore".

After that, the connection worked okay.

Other things you might want to try.

1. Open port on your router that UltraVNC uses then with Firefox on your Desktop computer go to [www.grc.com](www.grc.com). Navigate through site to "Shields Up" which is a free port scanning service by a reputable company. Have it scan port 5500 (or whatever you have configured) to confirm nothing is blocking and port is open.

2. If you have wireless on your XP computer, see if there is unsecured wireless network in range and connect through it while you are testing your SingleClick setup. 

3. Since you know your Desktop setup is correct, connection problem must either be remote computer user not doing something right or a problem with your router. Check the Ultravnc forums for generic SingleClick connection problems or google name of your router and SingleClick

Hope this helps...

---

