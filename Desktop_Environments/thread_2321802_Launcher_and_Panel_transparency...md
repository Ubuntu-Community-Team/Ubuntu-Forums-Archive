---
title: "Launcher and Panel transparency.."
date: 2016-04-24
forum: Desktop Environments
---

### Post by CVGH on 2016-04-24
Hi,

I'm trying to get my launcher to have a transparent background.
The panel is ok but I can't get the launcher background transparent.

Unity/Ubuntu Tweak nor CCSM seem to have any effect..

What am I missing?

Thanks!

---

### Post by mc4man on 2016-04-24
Try setting the Launcher Opacity to 0.0000 & the Background Color > Opacity to 3, leave the Background color at #000000

---

### Post by CVGH on 2016-04-26
Hmmm............

In CCSM I was able to make the Panel transparent but the launcher background is solid black...

---

### Post by mc4man on 2016-04-26
> **CVGH said:**
> Hmmm............

In CCSM I was able to make the Panel transparent but the launcher background is solid black...
While I don't do as in screens this is as transparent as I can get both. There is a flaw in that the Background Color opacity affects the panel opacity so to keep a transparent panel the BC opacity has to be very low. 
(- If the BC opacity is set to 0, (default),  then the launcher gets colored even when set to transparent based on average of your Background image. A low BC also creates a transparent Dash which can be undesirable... 

The launcher opacity is set in screen to 0.0000 & is pretty much transparent though another flaw is the dark shadow at the top.

---

### Post by CVGH on 2016-04-26
Huh,

For some reason that does not work here. 

Thanks!

---

### Post by mc4man on 2016-04-26
> **CVGH said:**
> Huh,

For some reason that does not work here. 

Thanks!
I guess that begs the question - What release of Ubuntu are you using?

---

### Post by CVGH on 2016-04-28
14.04.4

---

### Post by mc4man on 2016-04-29
> **CVGH said:**
> 14.04.4

Log into a guest session, open ccsm & see if it works there

---

### Post by CVGH on 2016-04-30
No change. Can make panel background transparent but not the launcher....

---

### Post by CVGH on 2016-05-01
So I've set the launcher to auto-hide so I don't notice it so much....

Thanks!

B.

---

### Post by saiboo on 2016-09-11
> **CVGH said:**
> I'm trying to get my launcher to have a transparent background.
The panel is ok but I can't get the launcher background transparent.


Hi, I just fixed this, maybe you have the same situation:

```
saiboo@home:~$ gsettings get org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ low-graphics-mode
```

leads to _*true*_.

In that case, you need to change such param:

```
saiboo@home:~$ gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ low-graphics-mode false
```

ubuntu 16.04 LTS, YMMV

---

### Post by CVGH on 2016-10-09
```
[COLOR=#000000][FONT=&amp]gsettings get org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ low-graphics-mode[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Response is "false" [/FONT][/COLOR]

---

