---
title: "Panel problems in Hardy"
date: 2008-04-21
forum: Desktop Effects &amp; Customization
---

### Post by dannytatom on 2008-04-21
I'm having two problems with the gnome-panel (screenshot attached).

1)  Everytime I reboot, the panel goes back to the bottom with everything unorganized (quick launch icons, date, etc are all out of order and not where they were before rebooting), and also the panel is placed at the bottom on restart, instead of top.  When I try and put it at top, I have to expand it, place it, then unexpand it.  

2) The space where the panel SHOULD be (up top) holds whatever image was just there, instead of showing the wallpaper or whatevers behind it.

[http://tablefork.net/dny/Screenshot.png](http://tablefork.net/dny/Screenshot.png)** <- Screenshot**

---

### Post by rune0077 on 2008-04-21
How have you set the panel to the top? If you have just dragged it there, you may have to actually set it by right-clicking on it, select "Properties" and set "Orientation" to top.

---

### Post by dannytatom on 2008-04-21
That's how i'm setting it.  When I restart, right click and select top, it changes back to bottom after a second or two(not the panel, the option, the panel never moves.)  I have to expand it, put it top, then unexpand it.

Hope it's clearer now :x

---

### Post by dannytatom on 2008-04-22
anyone?  :/

---

### Post by rune0077 on 2008-04-22
Maybe it would help to just create a new panel, set it to the top from the beginning, make it exactly like you want it to be, and then delete the old one. Just a thought, though.

---

### Post by lausianne on 2008-05-04
This looks like a bug to me. I had no problem with the main panel yet, but an additional panel that used to be on the bottom suddenly moved to the top and I could not change the orientation.
One of the above posts inspired me to expand the panel first, then change the orientation. That worked. I think expansion and orientation should be independent, shouldn't they?

Another problem for me is that the icons (trash bin etc.) on the additional panel are right in the center of the panel and the window list icons are cramped on the left side of the other small icons -- when the panel is not expanded. 
Supposedly icons can be moved with the middle button which I don't have on my laptop ...

These panels are a basic feature of Ubuntu, I hope these bugs will be fixed soon. Thanks!

Cheers, Ralf.

---

### Post by rune0077 on 2008-05-04
> **lausianne said:**
> This looks like a bug to me. I had no problem with the main panel yet, but an additional panel that used to be on the bottom suddenly moved to the top and I could not change the orientation.
One of the above posts inspired me to expand the panel first, then change the orientation. That worked. I think expansion and orientation should be independent, shouldn't they?

Another problem for me is that the icons (trash bin etc.) on the additional panel are right in the center of the panel and the window list icons are cramped on the left side of the other small icons -- when the panel is not expanded. 
Supposedly icons can be moved with the middle button which I don't have on my laptop ...

These panels are a basic feature of Ubuntu, I hope these bugs will be fixed soon. Thanks!

Cheers, Ralf.

You should be able to move the icons just by right-clicking them and select "move". If the option is greyed out, you first need to uncheck "Lock to panel".

---

### Post by lausianne on 2008-05-04
Thanks for the reply. Right clicking and moving works.

After the last reboot the panel had jumped to the top again. But now the icons are nicely arranged on the right end of the expanded panel.
Getting closer ...

---

### Post by mat28590 on 2008-05-15
Alt + F2
run gconf-editor
apps -> panel -> toplevel
select the panel
increase the  value until the panel is at the bottom 
:)

---

### Post by mlnease on 2008-05-23
> **mat28590 said:**
> Alt + F2
run gconf-editor
apps -> panel -> toplevel
select the panel
increase the  value until the panel is at the bottom 
:)
Hello, All,

I've been having the same problem in Hardy (otherwise fabulous).  I had it for a while in Dapper and it finally resolved--I don't know or can't recall how or why.  Anyway since I'm dual-booting Dapper and Hardy now, I thought I go back and look at the (working) Dpper configuration from gconf-editor and compare the same in Hardy.  Screenprints are are attached, comparing bottom and top panel settings in Dapper (working) and Hardy (non-working).  Hope this will be of some use to someone.

mike

---

### Post by pjones0404 on 2008-05-24
i am having the exact same issue. 

i like to have the top panel unexpanded. how ever when i change this setting and restart or log out. when i log back in it is at the bottom of the screen with the launchers scrambled. 

In order to get it back to the top of the screen i have to expand then move.   however if i then unexpand the issue repeats when i restart. If i leave it expanded it stays no problem. I wish i could determine what it is that is causing the problem.

---

### Post by 5m0k3 on 2008-05-31
If push comes to shove, you can simply open "gconf-editor" and navigate to "/apps/panel/global/" and check the "locked down" option when you have everything in the order and position you desire. 

If you wish to make any changes to your panels at a later time, you'll have to disable this to do so.  It will prevent things from getting scrambled in the meantime, however.

---

### Post by sawtoothX on 2008-06-08
I am having a similar problem; I want the gnome panel on the bottom of the screen, on top of the window selector panel. I move it, arrange it, and on each restart, the gnome panel goes on top of the window selector. That _doesn't_ happen when restart just the xserver (i.e. CTRL+ALT+BACKSPC). 

I think another problem is relevant: After I set it up and I restart, my keyboard layout gets messed up also. The keyboard shortcut to change the layout from En to Gr doesnt work and neither does manually selecting the layout work. (The flag changes but I still cannot type in Greek). 

I think my xorg.conf gets "reset" someway after each restart. I have read similar posts but nothing helped. Even If i manuallly edit xorg.conf, it still gets messed up after a restart. I had ubuntu 7.10 and it was just fine. I upgraded to 8.04 and I got all these annoying problems. I then tooked the risk and did a clean instal of 8.04, hoping this would make things better. It worked quite fine for a couple of days and then...

Does anyone thing these two problems are originating from the same source?

---

### Post by BilliShere on 2008-06-17
oooo this has to do with your sessions maybe. i was having a similar problem and then i unclicked remember previous session, set gnome panel to restart within the session manager. and then set the default startup list. it worked flawlessly.

---

