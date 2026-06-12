---
title: "How to automatically arrange desktop icons?"
date: 2019-01-14
forum: Desktop Environments
---

### Post by G0at1 on 2019-01-14
Anyone know how to automatically arrange desktop icons so they snap in their positions?

Also, when I connect a USB drive or copy/paste files to the desktop, they go over existing icons. How do I fix that? I've installed Gnome Tweaks. Is there a setting in there?

---

### Post by G0at1 on 2019-01-17
Anyone know how to do this? I want the icons to snap in position horizontally.

---

### Post by yetimon_64 on 2019-01-17
What ubuntu release and desktop environment are you using?

I am on an xfce DE on trusty 14.04 and can right click the desktop to get a context sensitive menu to show and select the option "Arrange desktop icons". If I recall correctly it is very similar in Unity on 16.04. I haven't tried the latest 18.04 release for stock Ubuntu with the new gnome desktop set up yet so am not sure if it is the same there though I expect it will be similar.

Whatever DE/release you are on try right clicking anywhere on the desktop and see if there is an option called "Arrange desktop icons" and if that helps your situation.

**Edit:** my suggestion is more of a manual means of arranging the icons "as needed". I just noted "automatically" in the title so my suggestion may not be answering exactly what you are asking for, sorry if that is the case. I am not aware of any such automatic sorting apart from using the context sensitive menu.

Regards, yeti.

---

### Post by G0at1 on 2019-01-18
I'm on 18.04 LTS and using Gnome Unity I guess.. I'm new to Ubuntu. There is a "keep aligned" feature if I right click the desktop, as well as a "organize desktop by name" which line up the icons vertically, but I have to click "keep aligned" each time I move an icon manually. It doesn't snap in place automatically (horizontally, at least). And when I plug in a USB drive, the icon goes on top of other existing icons. In that case, I have to move it manually or use the "keep aligned" feature again.

---

### Post by yetimon_64 on 2019-01-19
I have not tried the new 18.04 LTS Ubuntu release yet so am not sure what the set up with your system is.
> I'm on 18.04 LTS and using Gnome Unity I guess...
I don't think the standard desktop is Unity any more, as far as I understand the situation Canonical has moved away from Unity as the standard desktop and gone back to using gnome. I haven't used a gnome desktop since gnome2 many years ago :-).

I suggest you wait for other helpers, who actually use the new Ubuntu 18.04 desktop, to assist with this question.

Regards, yeti.

---

### Post by Dennis N on 2019-01-19
Observations based on my experience with Ubuntu 18.04:

You should arrange icons manually within the rectangular desktop grid (column,row). Last positions occupied are registered by OS so next time, icons return to same position. A never before used device or file has no recorded position, so icon goes into first unregistered (column,row) spot. 

In first attached image, USB named MyData2: when device inserted, icon went where it is because it was there last time I removed it and not into first blank space (which is registered to another USB named MyData) 

Image 2: I then plug in USB named MyData, and it went into its last-used position. Amazing! This is evidence positions are remembered.

I don't save files to the desktop itself - only device icons appear there. Instead for files there is a link to a folder 'Desktop-files' where I can store stuff temporarily until I decide on its disposition.

Tips:
Initially, to see the grid locations, use the "Organize desktop by name" action.  Reorder manually using these grid locations. Set "keep aligned" option. Then never use "Organize" again - it resets everything. I think my devices and links are in column 3 (to stay out of the way of the dock on the left).
If you move an icon, its last position becomes available again.

---

### Post by G0at1 on 2019-01-19
Hey Dennis and Yeti, thank you for your help. You're right, Gnome remembers the last position of the icons. I guess I'll go with Dennis' tips :)

---

### Post by ajgreeny on 2019-01-19
Does the 18.04 Ubuntu gnome desktop save the positions of desktop icons in a simple text file like Xubuntu, which I use does?

I no longer have any desktop icons, using an autohidden left hand side panel instead, but when I did use them in the past, having set their positions, I made those text files immutable with command ```
sudo chattr +i .config/xfce4/desktop/icons*
```
Should any of them move for unknown reasons a quick press of F5 on the desktop would put them all back in place.

---

### Post by G0at1 on 2019-01-20
I guess not. I got this error: chattr: No such file or directory while trying to stat .config/xfce4/desktop/icons*

---

### Post by Dennis N on 2019-01-20
There is a configuration file (just not where you are looking) - it not meant to be changed by the user.

---

### Post by ajgreeny on 2019-01-20
> **Dennis N said:**
> There is a configuration file (just not where you are looking) - it not meant to be changed by the user.
Thanks for that Denis N; I presume from that comment that the config file is somewhere in the filesystem, not the user's home, as it is in Xubuntu.

I can not get on well with the gnome 3 desktop so have never bothered to look into these sort of details, but in the days when Xubuntu with desktop icons used to move those icons around drove me really mad! Making the file immutable was a quick and harmless action that just worked very well, so it's a shame the same is not true of Ubuntu with gnome.

@G0at1
I did not intend you to run that exact command as that is for Xfce4 (Xubuntu) not the gnome desktop you're using.

---

### Post by G0at1 on 2019-01-20
> **ajgreeny said:**
> @G0at1
I did not intend you to run that exact command as that is for Xfce4 (Xubuntu) not the gnome desktop you're using.

That's ok, lol I don't know what I'm doing with this operating system anyway. :D

---

### Post by Dennis N on 2019-01-21
> I presume from that comment that the config file is somewhere in the filesystem, not the user's home, as it is in Xubuntu.
Icon positions registered in: ~/.config/nautilus/destkop-metadata
I don't think it's meant to be modified by the user. The system will write to this file to update or add desktop icon positions.

---

### Post by ajgreeny on 2019-01-22
Interesting!
Have you tried making that file immutable?
It is possible, I accept, that doing so might make the complete DE crash, but as I don't use gnome I have no way of checking that.  The file may also govern other aspects of the DE that need to change when running gnome, which would make an immutable file a problem, but I speak only from a position of lack of experience.

---

### Post by G0at1 on 2019-01-22
@ aj: I don&#8217;t know how. Is DE=desktop? If so, I don&#8217;t want it to crash..
I&#8217;m just gonna live with what I have. No big deal...

---

### Post by yetimon_64 on 2019-01-24
> **G0at1 said:**
> @ aj: I don&#8217;t know how. Is DE=desktop?...
ajgreeny's code box in post #8 shows the chattr command to set a file immutable, the path would need to be changed in the code box to suit the gnome file. I don't think it would be a good idea in gnome, just a feeling though, I don't know for sure what would happen by doing so; xfce4 is pretty forgiving when tweaking it from my experience.

DE means Desktop Environment. 
Cheers, yeti. :)

---

### Post by G0at1 on 2019-01-24
I&#8217;m not touching anything then :)

---

