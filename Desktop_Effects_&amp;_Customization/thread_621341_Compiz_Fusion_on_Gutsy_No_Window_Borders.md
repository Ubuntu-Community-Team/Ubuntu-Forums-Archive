---
title: "Compiz Fusion on Gutsy: No Window Borders"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by dbbolton on 2007-11-23
Compiz Fusion was working fine until I upgraded to Gutsy. When I try to enable Desktop Effects from System > Preferences > Appearance > Visual Effects, my window borders disappear. Here is the output of running 'compiz' from the terminal:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0241 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
```

---

### Post by mpierce on 2007-11-23
At first I thought you needed this but appears that you have no glx running and you didn't mention what type of video card you are using which may be your problem. Here's what I was posting but look at both reasons:

Look for the Window Decoration button. 
Right next to Command, type kde-window-decorator, gtk-window-decorator or emerald (depending on what you want to use - this will prevent the window borders to disappear in certain situations). 

Hope this helps...

---

### Post by dbbolton on 2007-11-23
I have a newer geForce card, and I'm using the nVidia driver.

In the "Widow Decoration" options, 'gtk-window-manager' was entered as the command at the time I tried to run compiz.

---

### Post by dbbolton on 2007-11-23
Also, I thought this might be helpful in diagnosing the problem. I searched "compiz" in Synaptic. Here is what I have installed:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/compizpackages1.png[/IMG]
[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/compizpackages2.png[/IMG]

Maybe I need to purge/install some packages.

---

### Post by dbbolton on 2007-11-24
Forget it. I just decided to do a clean install of Feisty.

Those who are thinking about upgrading to Gutsy, be warned.

---

### Post by FuturePilot on 2007-11-24
> **dbbolton said:**
> Forget it. I just decided to do a clean install of Feisty.

Those who are thinking about upgrading to Gutsy, be warned.

I think the problem was that you had Trevino's Compiz Fusion installed in Feisty.
It's kind of late now, but you should have tried purging everything related to Compiz and reinstalled it.
[http://ubuntuforums.org/showthread.php?t=580063]("http://ubuntuforums.org/showthread.php?t=580063")

---

### Post by dbbolton on 2007-11-24
> **FuturePilot said:**
> I think the problem was that you had Trevino's Compiz Fusion installed in Feisty.
It's kind of late now, but you should have tried purging everything related to Compiz and reinstalled it.
[http://ubuntuforums.org/showthread.php?t=580063]("http://ubuntuforums.org/showthread.php?t=580063")
Actually, I had used Amaranth's repos to install compiz-fusion. I have never used Trevino's repos. 

Also, I purged all of the packages shown in the above screenshot, disabled all third party repos, and reinstalled 'compiz' and its dependencies-- to no avail.

---

### Post by Sijmes on 2007-11-24
I had this problem also whilst using an nvidia card and feisty and solved it bij adding this to my xorg.conf file...

 "Option "AddARGBGLXVisuals" "On" 
  
However since a clean install of gutsy the same problem has returned after an update which included a newer nvidia driver,and the above fix does not work ..   any ideas...?

---

### Post by Sijmes on 2007-11-24
OK here is the fix...

  go to the compiz fusion contro panel and find the"section "effects" ,then tick the "Window decoration " icon and your uncles a monkey,erm a gibbon ...

                     yes we somtimes look further than necesary ...   :-)

---

### Post by dbbolton on 2007-11-24
> **Sijmes said:**
> OK here is the fix...

  go to the compiz fusion contro panel and find the"section "effects" ,then tick the "Window decoration " icon and your uncles a monkey,erm a gibbon ...

                     yes we somtimes look further than necesary ...   :-)
I had tried that too.

---

### Post by 164747 on 2007-11-25
I have the same problem, the situation is solved for me if I change to

Defaultdepth 24

and

 Depth 24

(for me previous values where 16 in booth cases) under the Screen Section and Display Subsection in /etc/X11/xorg.conf

HOWEVER, even though the frames show up and everythin. IT GOES MUCH SLOWER.
So I have to choose between speed and frames.

Anyone who knows anything about this?

---

### Post by googleaseerch on 2007-11-26
Starting compiz from the command line gives me basically the same warning - this only started happening after a recent update from a few days ago.  Also
gtk-window-decorator --replace
does not get me anywhere.

---

### Post by -grubby on 2007-11-26
when you had this problem did you try to run
```
compiz --replace
``` ??

that fixes it for me

---

### Post by JBAlaska on 2007-11-27
Since you have a window border problem, and you have (had) emerald installed, you need to start emerald to get said window borders;
```
emerald --replace
```

---

### Post by MNICY on 2007-11-27
did you download emerald and put 'emerald' into the window decoration "command" box?
Worked for me. (although, the default GNOME decorator was working for me... i just like emerald ;))

---

### Post by dbbolton on 2007-11-27
I had tried installing emerald, AND putting 'emerald' in the command box under Window Decoration, but it didn't work.

Who knows, this may work for some people, but I had several other problems with Gutsy so I decided to downgrade.

---

### Post by DutyDuty on 2007-11-28
Getting XGL could also fix the problem. It dodges several compiz related problems, I've seen.

---

### Post by bcollignon on 2007-11-29
I have tried all of the above minus changing the default depth to 24 instead of 16.  Unfortunately, a video game which my son runs requires 16 as the default depth and will not run with 24.  So, if I change the default depth to 24, I may get my title bars and borders only to give up functionality of my son's game.  Is there an easy way to make this switchable?  Any help is greatly appreciated.

---

### Post by ruthgard on 2008-04-30
I found a way to solve this, it seems to have to do with the transparancy not working for gtk-window-decorator. I runned this command:

gtk-window-decorator --no-opacity-shade --replace &

And it worked fine after that.

---

### Post by teet on 2008-04-30
I followed the advice here:  [http://geekybits.blogspot.com/2007/10/no-window-borders.html](http://geekybits.blogspot.com/2007/10/no-window-borders.html)

Basically just enter the 2 commands into a command prompt and then reboot.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo nvidia-xconfig --add-argb-glx-visuals -d 24

```

It worked.

-teet

---

