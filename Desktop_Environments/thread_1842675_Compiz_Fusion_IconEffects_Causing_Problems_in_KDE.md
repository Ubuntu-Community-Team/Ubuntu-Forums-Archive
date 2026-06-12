---
title: "Compiz Fusion Icon/Effects Causing Problems in KDE"
date: 2011-09-11
forum: Desktop Environments
---

### Post by Valkyr333 on 2011-09-11
Hi, everyone...

I just tried to get the "Burn" effect to work in my Ubuntu (Kubuntu) with Compiz Fusion. I followed a bunch of tutorials I found on YouTube and a few other sites to learn how to make the effect work. The only way I've found to get these effects to take effect in KDE is with the Compiz Fusion Icon's "reload window manager" option, and when I click that, the effects show up (and look boss-awesome.) Problem is, the following things also happen when I reload window manager:


[LIST]
[*]Two of my three Virtual Desktops Disappear.
[*]My "page glow" and all other effects controlled by System Settings> Desktop> Desktop Effects are automatically disabled.
[/LIST]
Although my other two virtual desktops disappear from accessibility, the wallpaper looks to be off-center as though it were rolling from desktop to another. If I right-click the desktop that's still showing on the console, and go to "configure virtual desktops," I see my three normal desktops listed, and a fourth one (without a name) is added. If I tell it to go back to having only three, then "apply" and close the configuration tool, nothing changes, but when I open it again the same thing is true (three normally named ones and an added, nameless fourth.) This is the case however many times I try to do that same thing. Despite it saying that those desktops are all there, my Desktop Cube won't roll over with the "Ctrl + Alt + <--" or "Ctrl + Alt + -->" commands I defined for it. If I log out and back in again, everything's back to normal until I use the "reload window manager" command again. I can tell something is conflicting with someone else (or that's what it "feels like" to me) but I don't know what those things are or how to fix them. Ideally I'd like to have all of the features I mentioned above working at the same time.

Can anyone provide any insight on this one?

---

### Post by sumski on 2011-09-20
Effects in systemsettings belong to KWin (KDE's window and compositing manager), and they can't be used at the same time as the Compiz (another window and comp. manager) ones

---

### Post by Copper Bezel on 2011-09-20
Yeah, you can control the virtual desktops in Compiz in the General Options plugin under Desktop Size, but there isn't an easy equivalent for the Glow.

---

### Post by Valkyr333 on 2011-09-21
Thanks for the info.

Is there any way I can get the "burn up" effect in KDE Desktop Effects? I figure there must be, even if it means figuring out how to program it myself someday. KDE is the more graphics capable interface, no?

---

### Post by sumski on 2011-09-23
There's no burn up effect in KWin, but i personally find KWin's effects more than enough

---

### Post by Valkyr333 on 2011-09-30
That's too bad about the Burnup effect-- it's utterly sexy when I use it in Gnome. I guess I'm just fussing over glitz and glamour, though. Besides lacking the Burnup effect, kWin's effects do the job well. I guess I'll just have to hope that someday they make a version of Burnup for kWin.

Since there seems to be no "perfect solution" for this right now, I'm gonna mark this as "solved." Thanks for your advice, everybody. =)

---

