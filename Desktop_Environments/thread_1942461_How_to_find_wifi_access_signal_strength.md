---
title: "How to find wifi access signal strength?"
date: 2012-03-17
forum: Desktop Environments
---

### Post by unckybob on 2012-03-17
When I put the cursor over icons in the system tray, sometimes a little yellow window comes up that displays information. Is there a name for those little yellow windows?

There is a little "broadcast" icon in the system tray that shows signal strength. Sometimes when I rest the cursor over it, it shows the signals strength. Sometimes when I rest the cursor over it, it does nothing.

Is there some way I can make the signal strength show up, or is there some other way to get it to display?

---

### Post by Frogs Hair on 2012-03-17
Post your Ubuntu version because options vary.

---

### Post by Cheesehead on 2012-03-17
Network Manager broadcasts the signal strength (and other information) to other applications in the system using a process called dbus. dbus is a way for different applications to exchange information. The wireless icon application listens for that information using dbus. It can also directly request the information instead of waiting for a broadcast.

If the icon isn't showing signal strength, it can be due to a couple causes. Most often, you may just not waiting long enough for the information exhange to complete. Delays of up to a second can occur for several reasons (like the CPU is busy doing something else, or the wireless card is busy streaming a movie). Less often, it may be due to a bug in the wireless firmware. Least often, it may be due to a bug in Network Manager.

Any dbus-aware application can pull the same information, so there are lots of ways to display it. You can also use the "iwlist [interface] scanning" command, or display it in your desktop background using Conky.

How often do you want this information?
Do you want it in human-readable or machine-readable format?
Do you have a specific purpose in mind for this info, or just curiosity?
Do you want it displayed or hidden?

---

### Post by Yellow Pasque on 2012-03-17
```
iwconfig
```

---

### Post by bogan on 2012-03-18
Hi!, **unckybob**,

In my 10.04 installation and in 11.10 when logged in to Gnome Classic, the WiFi icon in the Topbar ( Network Manager ) always shows the  signal strength as a percentage, when the connection is 'active' and the mouse cursor is placed over it - sometimes with a delay of a fraction of a second, as a previous Poster mentioned.

When there is no connection, or when logged in to 11.10 Unity 3D 'Ubuntu' it shows nothing.

'iwconfig does not show a comparable '%Strength' but "Link Quality" as a ratio, and "Signal level" as a negative dBm figure { whose significance is beyond me to understand }.

At this moment, with no actual data flow, the WiFi Icon shows "....Connection Active: (82%)"; whilst 'iwconfig' or 'iwlist scan' show 'Signal level' = -52dBm; and  'Link Quality' = 58/70 { ==83% }.  [**Edite**d: Figures were reversed.]

Edit: Repeating with the same network, but on another Desktop, gave:  'Link Quality' = 100/100 and 'Signal level' =98/100 ! - first time I have seen 100%, or other than a negative value for the later.

Chao!, **bogan.**

---

### Post by unckybob on 2012-03-18
Thanks for all the response.

I'm running 11.04 (natty).

I just bought one of these USB wifi devices and I'm interested how it works and what these signal strengths are. I assume that the stronger the signal strength the better.

I think the "iwconfig" command is exactly what I was looking for. I assume the 'Link Quality' ratio is the same thing as the 'signal strength' that is reported from the system tray icon. 

Funny thing that it doesn't report the signal strenght always (on my machine anyway). I can leave the cursor over it for several minutes and nothing happens.

---

### Post by Ubuk2008 on 2012-09-30
> **Temüjin said:**
> ```
iwconfig
```

This was quite helpful. Thanks, to the thread-starter and this poster! :)

---

