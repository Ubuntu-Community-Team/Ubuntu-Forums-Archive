---
title: "Screen resolution problem"
date: 2005-06-07
forum: Desktop Environments
---

### Post by arunsub on 2005-06-07
I have Dell P991 monitor. Once every few days, the screen resolution changes to 600*480. It sometimes goes back to the original resolution 1280*1024 if i reboot and most of the times it doesn't. I then have to reconfigure the x-server to change the resolution since it doesn't show any other option in the preferences - screen resolution option. What could be the reason?

 :-x

---

### Post by skoal on 2005-06-07
Hmm...

If you have access to another video card, you might want to drop that one in there and see if you can reproduce the same "error".  If not, it could be an indication that the mobo on the Dell monitor needs some loving.  I had to get a technician replace my mobo on a monitor a while back since some overheating cooked it's innards.

Anyway, your sympton sounds like either the video card or monitor mobo is not able to hold a certain sync frequency (ie. the high ones @1280x1024) over time, for whatever reason.

just a guess...

\\//_

---

### Post by arunsub on 2005-06-07
I don't have that problem with Windows XP (It's a dual boot machine). I also have speed fan installed in Windows XP which till now showed me all components under treshold temperature. I have Gkrellm installed and that didn't show any high temperature. I think it has something to do with Ubuntu installation/GNome rather than mobo problem. 
btw it's a new mobo i bought 3 months back.

---

### Post by skoal on 2005-06-07
I wasn't talking about the cpu mobo but the mobo inside your monitor.  I guess most people aren't aware that they have a mobo inside their monitor.

Anyways, does the monitor just all of a sudden lose sync and change back to 640x480? or does it only change back to 640x480 after a fresh reboot?

For your monitor, if you haven't done so already add these lines to your /etc/X11/xorg.conf file (under the Monitor section):

Section "Monitor"
[...]
        HorizSync       30.0 - 107.0
        VertRefresh     48.0 - 120.0
[...]

Do you have options like the ones below in your 'xorg.conf' file?

Section "Screen"
[...]
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
[...]

and for some reason these are disappearing? which is why you have to reconfigure your xserver?  what do you mean by reconfigure?

\\//_

---

### Post by arunsub on 2005-06-08
[QUOTE=skoal]I wasn't talking about the cpu mobo but the mobo inside your monitor.  I guess most people aren't aware that they have a mobo inside their monitor.

Anyways, does the monitor just all of a sudden lose sync and change back to 640x480? or does it only change back to 640x480 after a fresh reboot?

For your monitor, if you haven't done so already add these lines to your /etc/X11/xorg.conf file (under the Monitor section):

Section "Monitor"
[...]
        HorizSync       30.0 - 107.0
        VertRefresh     48.0 - 120.0
[...]

Do you have options like the ones below in your 'xorg.conf' file?

Section "Screen"
[...]
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
[...]

and for some reason these are disappearing? which is why you have to reconfigure your xserver?  what do you mean by reconfigure?

\\//_[/QUOTE]

I'm sorry. I thought you were talking about the CPU mobo. I don't think it's a problem with the monitor because as i said, if i use windows xp, i don't have any problem. i can keep the monitor on all day. The problem happens with Ubuntu when i boot. It doesn't change when the system is on. It changes while/after booting. It goes away sometime when i reboot and it doesn't sometimes. When it doesn't then i go and reconfigure my x-server. Xorg.conf has all those entries.

---

