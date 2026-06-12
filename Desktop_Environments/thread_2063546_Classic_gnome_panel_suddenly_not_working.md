---
title: "Classic gnome panel suddenly not working"
date: 2012-09-27
forum: Desktop Environments
---

### Post by netopalis45 on 2012-09-27
After having some trouble with some disk full errors the classic gnome panel that I have been using stopped working.  I tried running it from terminal and got some errors about expecting a string and getting a list, I managed to fix those by changing some values in the gconf-editor. Now all I get when I try to run it from terminal is "Segmentation fault (core dumped)". I have uninstalled, purged, and reinstalled several times but no effect. Using Ubuntu 12.04 64-bit.

---

### Post by netopalis45 on 2012-09-30
After purging and reinstalling several times I finally figured out that it was leaving some remnants so I removed those as well. This time it tried to start and then it gave me another error that it stopped working and suggested I send an error report, which I did. I then tried starting it from terminal and got this message 

```

** (gnome-panel:3228): WARNING **: Error opening directory '/usr/share/gnome-panel/4.0/applets': No such file or directory
Segmentation fault (core dumped)

```

After reinstalling Ubuntu 12.04 still having the same problem. I purged again and autoremoved and am still seeing remnants when I use whereis and locate. Really could use some help here

---

### Post by netopalis45 on 2012-10-05
Admin: Can you move this thread to General Help, I think I may at least get a reply there.

---

### Post by Ravi5kumar on 2012-10-05
Maybe it will work again if you reset the gnome to its default.

***This command will delete your configuration files.*** So be warned!;)

First if you want to backup your config file run this:

```
mkdir ./.old-gnome-config/ && mv ./.gnome* ./.old-gnome-config/ && mv .gconf* ./.old-gnome-config/ && mv ./.metacity ./.old-gnome-config/ && mv ./.cache ./.old-gnome-config/ && mv ./.dbus ./.old-gnome-config/ && mv ./.dmrc ./.old-gnome-config/ && mv ./.mission-control ./.old-gnome-config/ && mv ./.thumbnails ./.old-gnome-config/   && ~/.config/dconf/* ./.old-gnome-config/
```Now delete config files:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
```Log out and log in back.

---

### Post by netopalis45 on 2012-10-05
Just gave that a try and when it tried to copy the .metacity folder it said "file not found". Could that be what is causing the problem in the first place?

---

### Post by Ravi5kumar on 2012-10-05
Metacity is a window manager and is used by gnome-classic session. 

> Just gave that a try and when it tried to copy the .metacity folder it said "file not found"

Its probably mean that something is missing inside the folder. I cannot clearly tell if it is the problem. I suggest you to delete the config files using the second command I posted and see if problem still exists......

---

### Post by netopalis45 on 2012-10-06
So I checked on metacity and it looked to be installed correctly but I went ahead and purged and reinstalled it but it didn't help any. Strange thing is I have a laptop with 12.04 installed and am running gnome classic perfectly on it so I really don't know what's going on.

---

### Post by kansasnoob on 2012-10-06
First be certain that you are logging into the classic (no effects) session and NOT the standard classic session:

[ATTACH]225200[/ATTACH]

The standard classic session uses compiz rather than metacity and it's proven to be problematic, more so on some hardware than others.

---

### Post by kansasnoob on 2012-10-06
Oh, just thought to add, since you have no panel(s) you might find it difficult to log out and display the login screen. The key combo Alt+SysReq+K should log you out if needed, and SysReq is PrtScn on some keyboards.

---

### Post by kansasnoob on 2012-10-06
If you find that some of your configuration files are messed up this may be helpful:

[http://ubuntuforums.org/showpost.php?p=11968600&postcount=40](http://ubuntuforums.org/showpost.php?p=11968600&postcount=40)

I made quite a few notes about using classic (no effects) here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by netopalis45 on 2012-10-06
That doesn't seem to be the problem. I changed the .compiz-1 files like your article said and nothing changed. When I log into Gnome Classic I can see all my desktop icons but the panels don't start. I can try starting them from a terminal but I still get the error "Segmentation Fault (core dumped)". I think it is a problem with the panel itself and not metacity or compiz but I can't figure out what. I am attaching a screenshot of what it looks like when I try to launch the panel from a terminal in Gnome Classic.

---

### Post by kansasnoob on 2012-10-07
What is the output of:

```
echo $DESKTOP_SESSION
```

---

### Post by netopalis45 on 2012-10-07
```

echo $DESKTOP_SESSION
gnome-classic

```

---

### Post by QDR06VV9 on 2012-10-07
> **netopalis45 said:**
> That doesn't seem to be the problem. I changed the .compiz-1 files like your article said and nothing changed. When I log into Gnome Classic I can see all my desktop icons but the panels don't start. I can try starting them from a terminal but I still get the error "Segmentation Fault (core dumped)". I think it is a problem with the panel itself and not metacity or compiz but I can't figure out what. I am attaching a screenshot of what it looks like when I try to launch the panel from a terminal in Gnome Classic.


I ran into something simular and was able to correct with this.
"killall gnome-panel"

---

### Post by kansasnoob on 2012-10-07
> **netopalis45 said:**
> ```

echo $DESKTOP_SESSION
gnome-classic

```

That's the standard gnome classic session which uses compiz. Please log out, then select Gnome classic (no effects), and log back into the (no effects) session which uses metacity.

I think the problem with compiz is not so much compiz itself, but rather the compiz settings "hard-coded" in Unity specific settings.

Anyway, at least trying a (no effects) session to see what happens is easy and totally non-harmful :)

BTW if you run "echo $DESKTOP_SESSION" while logged into a session running metacity the output will be "gnome-fallback".

Rather off-topic but the Ubuntu GNOME Remix project has come a long ways in 12.10:

[http://ubuntuforums.org/showthread.php?t=2064293](http://ubuntuforums.org/showthread.php?t=2064293)

It doesn't even have compiz installed and uses mostly Gnome specific default settings so it should be possible to just install compiz and build your own settings using ccsm.

Of course it's NOT an official respin yet but hopefully it's a step in the right direction.

---

### Post by netopalis45 on 2012-10-07
I ran "echo $DESKTOP_SESSION" in (no effects) and got "gnome-fallback" like you said but still no panels. I had seen rumours about a Gnome remix for 12.10 and am very excited. In my opinion Ubuntu should never have gone away from Gnome. Any idea when the Gnome remix will be out of beta?
I still don't think the problem is metacity or compiz related but with the panels themselves.

---

### Post by netopalis45 on 2012-10-09
Here's another interesting tidbit, when I log into Gnome Classic with our without effects there is no right-click menu at all, and no Alt-F2 run dialogue. The only reason I can do anything is because yakuake is in my startup and automatically loads

---

### Post by netopalis45 on 2012-10-10
I just did a complete reinstall to 11.10 and installed the slightly limited classic Gnome panel and then upgraded back to 12.04. At first this seemed like it fixed it but I am getting the same error again. I assumed that when you use apt-get purge it would remove all traces of a package but I was apparently wrong, ended up installing synaptic and completely removing everything that has anything to do with gnome-panel. Maybe this will work

---

