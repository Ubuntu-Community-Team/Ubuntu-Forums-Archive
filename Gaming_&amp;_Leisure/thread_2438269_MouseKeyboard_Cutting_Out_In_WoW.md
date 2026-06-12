---
title: "Mouse/Keyboard Cutting Out In WoW"
date: 2020-03-08
forum: Gaming &amp; Leisure
---

### Post by turtlemode on 2020-03-08
So I noticed when I'm gaming that my keyboard often does not register key presses. It usually only happens when I'm already holding down a couple keys and then try to press down another, but every once in a while it will fail to register a first press as well. Then I noticed my mouse does the same thing. I verified the issue with both my Razer Huntsman Elite and Keycool KC-84. Haven't tried a different mouse.

This doesn't seem to happen when I'm using my computer for normal stuff, but let's say I'm playing WoW. I'm holding down W, D, and right click. I go to press the 4 on my mouse to cast a spell or the tab key on my keyboard to target something and I have to press it three or four times to get it to register. This is extremely annoying and it is very common. Basically unplayable in PvP and annoying to say the least in PvE. It does seem like the more keys I'm holding down, the more often it happens.

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID b58e:9e84 Blue Microphones Yeti Stereo Microphone
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1058:1230 Western Digital Technologies, Inc. My Book (WDBFJK)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 1e71:1714 NZXT NZXT USB Device
Bus 001 Device 004: ID 0bda:0321 Realtek Semiconductor Corp. USB3.0 Card Reader
Bus 001 Device 003: ID 1532:0226 Razer USA, Ltd Razer Huntsman Elite
Bus 001 Device 002: ID 1532:0067 Razer USA, Ltd Razer Naga Trinity
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I did start off with a minimal install, so could there be any packages that I missed that could effect this? Would it possibly be a Wine thing? I installed the game with Lutris and have left all the settings at the default.

I installed OpenRazer and Polychromatic and the issue persisted.

---

### Post by mastablasta on 2020-03-09
could be a wine thing. try a native game see if it still happens. 

i haven't noticed this issue though i do not have a keyboard supporting rollover.

to see if it's a linux issue it should also be present in libre office writer for example. try typing...

---

### Post by turtlemode on 2020-03-09
Ya it doesn't seem to be a problem while I'm playing Rocket League, and that's basically constantly holding down multiple keys.

---

### Post by mastablasta on 2020-03-10
it might be worth getting some data out of this and then reporting to wine. would be great to see this corrected. 

might be interesting to also see if the issue persist in proton.

---

### Post by turtlemode on 2020-03-13
No issues in ESO. So no issues with Proton as far as I can tell. Going to download Mordhau now and try that too, but I suspect it won't have any problems.

---

### Post by turtlemode on 2020-03-16
Alright I got it figured out. After trying a couple games in Steam (Proton) and not having any issues, I decided to check Lutris and Wine forums and see if i could find anything. Well, Wine wouldn't let me do a search on their forum for some reason, so I went to Lutris instead.

I went to the [World of Wacraft page at Lutris.net]("https://lutris.net/games/world-of-warcraft/") and did a ctrl+f for "keyboard". Luckily, the very last post on the page had someone with the same problem as me (though a slightly different description). He said the ge-protonified runner works perfectly.

So I went to select that as my Wine version, but it wasn't present. I couldn't remember how to install more runners, so I did a couple more hours of searching and eventually found it on [the EA forums in a post for mouse clicks not working in Mass Effect]("https://answers.ea.com/t5/Technical-Issues/Mass-Effect-Andromeda-mouse-click-not-working/td-p/8226182/page/2"). Probably would have been much faster if I would have searched for how to install runners instead of specifically how to install ge-protonified.

Went back into Lutris. Selected gr-protonified as my Wine version. Booted up WoW. And it seems to be working perfectly now.

---

