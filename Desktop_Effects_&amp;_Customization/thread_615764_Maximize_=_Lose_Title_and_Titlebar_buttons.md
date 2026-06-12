---
title: "Maximize = Lose Title and Titlebar buttons"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by meuge on 2007-11-17
Hi

I just set up a new Gutsy install on an Inspiron 1521 for a friend, and when I maximize windows (with Compiz Fusion enabled), the title of the window disappears and so do the titlebar buttons (minimize & close). The titlebar is still there, so I can right-click and choose "unminimize" to get back to normal. 

Please help

---

### Post by bluewres on 2007-11-17
I also have this problem, it appears that when I maximize the title bar only shows up as a white space even though you can still click the areas where minimize and close buttons should be and get the appropriate responses.

---

### Post by carlos1992 on 2007-11-17
try downloading the compiz manager (CCSM) from the add/remove section and select the windows border maybe is that or is a Bug

---

### Post by cam381 on 2007-11-17
I might have the same thing. Please post screenshot. Thanks.

---

### Post by bluewres on 2007-11-18
I have ccsm, and that's essentially the problem either I turn on window decorations and I get what's pictured in the attached png or I turn it off and have no window borders at all.

---

### Post by lsutiger on 2007-11-18
I think you need a window manager (emerald). [Try this thread]("http://ubuntuforums.org/showthread.php?t=615824")

---

### Post by bluewres on 2007-11-18
well now that I am using emerald....
Same Situation
(Though I like the pretty red border on non-maximized windows haha).

Is it possible it has to do with my graphics card? I have a Radeon RV100 QY [Radeon 7000/VE]

---

### Post by lsutiger on 2007-11-18
are you using emerald --replace to start emerald?

---

### Post by bluewres on 2007-11-18
yes... I did that.

---

### Post by cam381 on 2007-11-18
Yea that's definitely what I have, any tips?

---

### Post by bluewres on 2007-11-18
Sorry Cam381, I still have no idea on how to fix it.  If anyone has some new suggestions please post.

---

### Post by cam381 on 2007-11-18
Thank You.:)

---

### Post by carlos1992 on 2007-11-18
It's really weird but maybe you have gtk2 engine bug  maybe is that or i really don't know xD but maybe you should Google a lil bit

---

### Post by AlesUbu123 on 2007-11-23
Does this help anyone? [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/91850/comments/4") 
Restart compiz afterwards. My maximised windows run fine now. 

I think this could be ATI specific...

Otherwise check this link
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/89741]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/89741")

C'ya,
Ales

---

### Post by bluewres on 2007-12-13
well as an update I have discovered that the side decorations of the windows also go white to the edge of the screen.  Essentially when I maximize the title bar goes away and I see no side decorations and when I just put the window wide enough so that the sides are both within a certain proximity of the screen's edge it will go white all around the window (interestingly enough that proximity changes based on how large the side decorations are).  I am using emerald also.

Help would be greatly appreciated, or at least a plausible in depth explanation as to why this is happening.

---

### Post by ceas2k on 2008-05-02
Glad to have found this!

Did the > You can create /etc/drirc file with the following contents:
<option name="allow_large_textures" value="2" /> bit and restarted x-server, it now works.

Computer is an old ThinkPad A31, 1.40GHz P4, ATI Radeon Mobility M7 running Hardy 8.04LTS, upgraded from Dapper LTS.

---

