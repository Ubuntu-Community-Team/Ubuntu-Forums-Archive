---
title: "Lightweight netbook environment: openbox Vs metacity"
date: 2010-12-27
forum: Desktop Environments
---

### Post by mrkazoodle on 2010-12-27
Hi

After installing UNR, I found the unity interface to be lacking advanced features, support on forums and tweaks.
So I installed the ubuntu desktop, but I kept maximus (and tweaked the list of apps which shouldn't be maximized, so I am pretty happy with maximus).

Since netbooks aren't as fast, I wanted to get a more lightweight desktop environment. I started with replacing Metacity with Openbox (since it seems to be quite popular).
I noticed that after logging in my memory usage was 186 MB and 189 MB after running ubuntu tweak, for both window managers.
If Openbox would be as lightweight as it claims to be I find it rather strange that I don't notice any difference in memory usage. Any ideas on this?

[SIZE="1"](about my "test": I changed the default window manager using ubuntu tweak, logged out and logged back in to start a new session, opened system monitor to measure memory usage)[/SIZE]

---

### Post by trinitydan on 2010-12-27
After I tried out UNR I decided it was time to start looking at some other distro options just in case the time should arise when Ubuntu had strayed too far from what my ideal OS should be.  I did a brief couple day distro-hop session and ended up trying out CrunchBang Linux.  I put it on my netbook and haven't had any problems with it at all aside from about the normal level of driver difficulty for a distro switch.  It is running right now on 133 MB of memory. :D  It's very minimal, but that enables you to add only the functions that you need.  It's debian based.  Sorry if this is too far off topic, I just saw the "openbox" and "lightweight" in the title and couldn't resist telling you.

---

### Post by kerry_s on 2010-12-27
it's not the window manager, it's other programs that run in the background. linux does a very good job of managing memory, better to just use what you like & leave the memory use to the system.
memory is no good if it's not used, trying to trim it is just wasting it. memory is faster than hd, more in memory, faster your system will feel. it's the same concept as preloading in windows, in linux apps are kept in memory until the memory is needed, if the memory is not required by other programs then it can stay there to help speed up relaunch of the program.

if your using the normal desktop version, you can use compiz to maximize windows, no need to install maximus.

---

### Post by mrkazoodle on 2010-12-27
@ trinitydan: thanks for the info, I might check crunchbang out someday, but not for now.

@kerry_s: I agree that memory shouldn't be wasted, I just found it very curious that just after starting a new session I didn't saw any difference between the two window managers in terms of memory usage. They had just started up, there was nothing to be left in the memory of programs which had been closed.
But to come back to my question: than what would the advantage of running openbox be? Less CPU usage? If it claims to be lightweight, than what is lightweight?

[SIZE="1"]I need to say that maximus was never removed from my system. But I'd find it surprising if maximus, which doesn't do more than maximizing and undecorating my windows, would be more demanding on resources than compiz. However I will try that out as well.[/SIZE]

---

### Post by kerry_s on 2010-12-27
> than what would the advantage of running openbox be? Less CPU usage? If it claims to be lightweight, than what is lightweight?

the thing about openbox is it's only a window manager, you still need to add other apps to get the things a desktop has.
being able to pick what parts you want gives you the option to use lighter programs or your preferred program.

by itself it is lightweight, because theres not much to it.

if you have 512mb or less then using a window manager makes since, but if you have 1gb or more then your just working to hard to get the desktop experience. when it comes down to it, it's a matter of preferences, some just like the choice of doing it there selves.

personally i been through all that already & learned it's best just to use whats there, some apps work faster than others, but they all work the same no matter what wm/de your using it's just the way there made.

---

### Post by peterfernandes238 on 2010-12-28
I wanted to get a more lightweight desktop environment.
------------
Peter Fernandes

---

### Post by Version Dependency on 2010-12-28
You won't notice a huge difference in metacity and openbox when run in Gnome because it's Gnome itself that is the big resource hog.  Openbox really shines when used without Gnome (or any other desktop environment).  Restart and log in to the Openbox session rather than the Gnome/openbox session and you will see a big difference.  Super lightweight.  But it will require you to manually configure the right-click menu...and you will probably want to install some sort of panel or dock.

---

### Post by mrkazoodle on 2010-12-29
I installed the lxde environment, which uses openbox and pcmanfm (= lubuntu?). Plus it already has a panel, however I don't like the lxpanel very much (in it's default layout). I'll try some tweaking (I already set it to using system colours, so much better), or I might try the xfce4 panel.

I do have another question: since Gnome is the resource hog, as you said, I'd probably better stop using [[COLOR="Blue"]_gnome apps_[/COLOR]]("http://projects.gnome.org/")?
Would using (some of the) xubuntu apps be a problem?
(I don't think so because they're neither gnome or kde, but I ask it just to make sure)

---

