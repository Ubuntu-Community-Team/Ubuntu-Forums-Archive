---
title: "xfce-panel, autostart.sh, anything?"
date: 2013-02-25
forum: Desktop Environments
---

### Post by JiuJitsu500 on 2013-02-25
So, earlier today I replied to a thread I started a couple days ago about AWN... and since I've been told it's dead and such - switched to Cairo like a boss which works about a thousand times better anyway and fixed three specific annoyances I had to manually fix with AWN at every restart anyway. Plus, it's more customizable and looks good. Reason number one though - the woman half of the house likes it and approves of the setup I gave her.

Except for one thing - the top panel.

I do not need it, everything is in Cairo and it autostarts and works excellent exactly like I needed it to. I thought as well that I knew how to remove the top panel. Turns out, not so much anymore. The old ways are not working. It's been a while for xubuntu, granted, but I'm on 12.04 and I haven't tried it since Lucid. I can disable it every time I boot up - but I cannot find an autostart.sh or any reference to xfce-panel in a script I can just comment out.

The system doesn't need it, nothing uses it and I have everything removed from it anyway and it just autohides all empty and lonely - it wants to die as it is. It's all a minor issue, but very annoying that I just can't find this thing anywhere.

Do I have to modify a script to kill it at every restart of xfce or can I comment it out of anything so it's gone forever?

---

### Post by Scott Goodgame on 2013-02-25
If you drop to a terminal and sudo nano /etc/xdg/xfce4/xinitrc and search <ctl>-w panel <enter>   for $panel .... it'll be around line 169ish and tabbed in a bit. Just put a # in front of it and save the file <ctl>-o <enter>   and exit <ctl>-x <enter>

That should stop it from loading in the first place.

Scott

---

### Post by JiuJitsu500 on 2013-02-25
Just tried it, commented out every instance of $panel and anything else relating to xfce-panel, but rebooted and still it persists. I was searching in the xdg and any conf files I could find in there too! Both in /.config and /etc.

Maybe I'll have to add a killall xfce-panel to that? Seems kind of redundant or circular...

If nothing else she can just deal with it :)

---

### Post by JiuJitsu500 on 2013-02-25
oh... let me correct myself.

I'm looking for xfce4-panel. I've been looking for both, but no luck yet. xfce4-panel is the target. I don't want to uninstall either or remove the package, laptop might blow up or send me back in time with guns or fire or food...

---

### Post by cortman on 2013-02-25
There may be some useful information [here]("http://askubuntu.com/questions/53996/running-xubuntu-without-panels").

---

### Post by LewisTM on 2013-02-26
The most straightforward way of preventing a program from executing is to remove its execute permissions
```
 sudo chmod -x /usr/bin/xfce4-panel
```
Works 100% of times ... until the binary gets replaced by an update, at which point you have to repeat. Or put the chmod command (without sudo) in you /etc/rc.local file.

Cheers!

---

### Post by Krytarik on 2013-02-26
> **cortman said:**
> There may be some useful information [here]("http://askubuntu.com/questions/53996/running-xubuntu-without-panels").
In addition to the accepted answer there, if you are using the "Xubuntu" session, as opposed to the "Xfce" one, you need to modify "/etc/xdg/**xdg-xubuntu**/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml". You can either just change the entry "xfce4-panel" to an empty string, i.e. "", or change it to "cairo-dock" straight away, this way you don't even need an entry in startup applications for it.

If you are following that outcommenting route, however, you'd need to outcomment (with "<!-- ... -->") the panel's section in *both* "/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml" *and* "/etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml", otherwise it would just fall back to the latter.

Obviously, I'd choose the first way, much less hassle and the additional option to run the dock of your choice directly through it.

Regards.

---

### Post by JiuJitsu500 on 2013-02-26
EUREKA!!!!!!!!

After a quick "sudo leafpad /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml" and outcommenting that xfce4-panel suggestion, all is working 100% as planned.

SOLVED, and thanks to all replies. Removing the executable from the binary is one thing I did, but like you said since it updates every now and then I'd have to keep doing that. It definately works for anything, but not the way I'd like. Now I know and should have thought to know that since I AM running the xubuntu-session and NOT strictly xfce, outcommenting that (and replacing it with cairo-dock) in THAT session fixes it.

Thanks again to all. Solved. Like a boss.

---

### Post by cortman on 2013-02-26
Great! Thanks for sharing your solution!
Good luck.

---

