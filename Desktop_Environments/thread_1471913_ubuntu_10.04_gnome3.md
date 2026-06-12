---
title: "ubuntu 10.04 gnome3??"
date: 2010-05-03
forum: Desktop Environments
---

### Post by xenosaga456 on 2010-05-03
so ya i know that ubuntu 10.04 comes with gnome 2 but what about gnome 3??? how do i use that

---

### Post by pytheas22 on 2010-05-04
Gnome 3 is still in development, but you can test out Gnome Shell (the major component of Gnome 3) by first installing it with:
```

sudo apt-get install gnome-shell
```

and then typing:
```

gnome-shell --replace
```

to start it.  Just remember that it's still not close to being finished, and you will likely have major problems.

---

### Post by galdren on 2010-05-04
so do you know how to rollback to the stable 2.30 when we're done trying it?

---

### Post by 3Miro on 2010-05-04
> **galdren said:**
> so do you know how to rollback to the stable 2.30 when we're done trying it?

If you use compiz effects:
> compiz --replace

If you don't use effects:
> metacity --replace

Gnome 3, or Gnome-Shell, is simply another windows manager like compiz and metacity. If you don't use it (gnome-shell --replace) it doesn't do anything on your system.

---

### Post by galdren on 2010-05-04
haha that was easy..like it :) can't wait till the final release

---

### Post by redkiwi on 2010-05-04
gnome-shell is so cool \\:D/
i love the simple handling and good looking design.

**many thanks to all the programmers =D>**


Is use this version:

**Gnome Shell  Testing PPA**
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

**sources.list**
deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) lucid main

**permanent use**
sudo update-alternatives --config x-window-manager 
sudo cp /usr/share/applications/gnome-shell.desktop /etc/xdg/autostart

---

### Post by Rubicon421 on 2010-05-04
So if you use Compiz and have desktop effects enabled then does that mean that you won't see the visual changes in 3.0? If you want to keep Compiz and desktop effects enabled would there be any benefit to upgrading to 3.0?

---

### Post by pytheas22 on 2010-05-04
> So if you use Compiz and have desktop effects enabled then does that mean that you won't see the visual changes in 3.0? If you want to keep Compiz and desktop effects enabled would there be any benefit to upgrading to 3.0?

Gnome-Shell doesn't use Compiz, because Gnome-Shell provides its own window manager (in Gnome 2.x, the window manager is a separate component; in Gnome 3 this will no longer be the case).  However, Gnome-Shell should generally support the same kinds of effects that Compiz provides in Gnome 2.

So the answer to your question, as I understand it, is: don't worry, you can upgrade to Gnome 3 and still have desktop effects.  The backend that's providing them will no longer be Compiz, but from the end-user's standpoint the behavior will essentially remain the same.

---

### Post by Rubicon421 on 2010-05-04
@Pytheas22

Thanks for the quick reply. I understand your answer but is there any benefit to switching then? Will everything look the exactly the same or will the layout of Nautilus menus be improved and things like that? If it's all just backend improvements then what would I actually notice if I upgraded?

thanks again!

---

### Post by pytheas22 on 2010-05-04
> Thanks for the quick reply. I understand your answer but is there any benefit to switching then? Will everything look the exactly the same or will the layout of Nautilus menus be improved and things like that? If it's all just backend improvements then what would I actually notice if I upgraded?

Gnome 3 will look drastically different, because the "Shell" that you see when you type "gnome-shell --replace" is the new desktop.  There will no longer be a Gnome panel, Applications/Places/System menu, etc.  So it's definitely not just backend improvements; it's a total overhaul of the desktop.  Whether or not you consider the changes a benefit is up to you.

I'm still waiting for Gnome 3 to come closer to completion before passing judgement, but I am kind of concerned about what I see so far.  For example, you *need* a graphics card that supports 3D acceleration to use Gnome Shell, and one of my computers doesn't have that.

You can read more at [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

---

### Post by techunit on 2010-05-04
Please post photos when possible I would like to see what Gnome 3 has to offer. I am excited about the new improvements but apprehensive about the new look.

---

### Post by pytheas22 on 2010-05-04
> Please post photos when possible I would like to see what Gnome 3 has to offer. I am excited about the new improvements but apprehensive about the new look.

I've written a few blog posts about it, which include a couple of screencasts (keep in mind that they weren't based on the most up-to-date code).  You can find them at [http://www.workswithu.com/tag/gnome-shell/](http://www.workswithu.com/tag/gnome-shell/)  You should also be able to find plenty of other, better screenshots and screencasts around the Internet.

---

### Post by BF79 on 2010-05-05
i just watched a few short vid's of gnome 3 and i think that it looks awesome 
i cant wait to put my 2 GPU's to the bench with that 
very sexy  :guitar:

---

### Post by 3rdalbum on 2010-05-05
Why all this "What does Gnome Shell look like", "Can you post some screenshots" etc?

Gnome Shell is available in the repositories for you to try out, risk-free. So get to it! :-)

---

### Post by redkiwi on 2010-05-05
I am currently not home, but here are a  few screenshots:
[http://www.workswithu.com/2010/03/18/testing-the-gnome-3-release-candidate/](http://www.workswithu.com/2010/03/18/testing-the-gnome-3-release-candidate/)

youtube video:
[http://www.youtube.com/watch?v=NN4lW_eaeO8](http://www.youtube.com/watch?v=NN4lW_eaeO8)

---

### Post by Rubicon421 on 2010-05-05
OK, before I test out Gnome shell on my main machine I have just one more question. I was thinking about testing it in a VM (Virtualbox on Windows 7 host/Ubuntu 10.04 32 bit guest). Since Gnome shell is 3D acceleration dependent will it even work in a VM and if so will it look the same or revert to some low graphics mode? Virtualbox has an option to enable 3D acceleration in the VMs settings but desktop effects/compiz don't work in VMs so does anyone know if this would be a waste of time to try and test it in a VM?

---

### Post by pytheas22 on 2010-05-05
> OK, before I test out Gnome shell on my main machine I have just one more question. I was thinking about testing it in a VM (Virtualbox on Windows 7 host/Ubuntu 10.04 32 bit guest). Since Gnome shell is 3D acceleration dependent will it even work in a VM and if so will it look the same or revert to some low graphics mode? Virtualbox has an option to enable 3D acceleration in the VMs settings but desktop effects/compiz don't work in VMs so does anyone know if this would be a waste of time to try and test it in a VM?

It should work if you enable 3D acceleration.  I haven't used VirtualBox on a Windows host, but Compiz works for me with an Ubuntu host and an Ubuntu guest.  I don't see any reason why it shouldn't also work on a Windows host.

Also note that there is no "low graphics" mode for Gnome Shell.  Without 3D acceleration it won't work at all.

---

### Post by KdotJ on 2010-05-05
Looks very interesting I must say, I think I'll have a play around with it. So you say that compiz won't be the backend, but have similar effects. Does that stand true for the cube and 3D windows? 
Also, do you think that gnome 2.x will be supported for a long time after?

---

### Post by Rubicon421 on 2010-05-05
I just tried installing Gnome shell in a VM and got the following:

u1004@u1004-desktop:~$ sudo apt-get install gnome-shell
[sudo] password for u1004: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
u1004@u1004-desktop:~$ gnome-shell --replace
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 278, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 135, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 73, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'
u1004@u1004-desktop:~$ Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Cannot register the panel shell: there is already one running.

[EDIT] OK, I forgot the sudo command. I re-ran the replace command and it seemed to have just reverted me back the original Gnome that I had. It looked different because it had undone the changes to the panels and theme that I had added and went back to the default Gnome setup.

---

### Post by 3Miro on 2010-05-05
> **KdotJ said:**
> Looks very interesting I must say, I think I'll have a play around with it. So you say that compiz won't be the backend, but have similar effects. Does that stand true for the cube and 3D windows? 
Also, do you think that gnome 2.x will be supported for a long time after?

Gnome-shell supports much fewer effects than compiz. In fact, it only supports some zoom effects. This will change in the future, but they are nowhere near a "cool effect stage". Right now they seem to be working on functionality first (which makes perfect sense).

```
gnome-shell --replace
```
Do not use "sudo"! Also, for graphical applications, do not use "sudo" at all, use "gksudo" instead. Also, do not use "gksudo" for gnome-shell, no special privileges are required. This is temporary thing to do, i.e. stop compiz and then start gnome-shell on its place.

This is a glx error, what is your video card and if it is NVIDIA or ATI, do you have the latest drivers. Can you run "glxgears". You can install it with
```
sudo apt-get install mesa-utils
```
Can you run compiz with zoom and/or cube effects?

---

### Post by KdotJ on 2010-05-05
thanks for the info, yes i can run compiz with the cube and zoom effects.
If i install Gnome-shell from the ubuntu software centre, what will it do? replace gnome? or will it give me the option at the login screen?

---

### Post by 3Miro on 2010-05-05
> **KdotJ said:**
> thanks for the info, yes i can run compiz with the cube and zoom effects.
If i install Gnome-shell from the ubuntu software centre, what will it do? replace gnome? or will it give me the option at the login screen?

It does none of those. Gnome-shell is not a separate environment, it is more like a separate window manager.

```
metacity --replace
```
This gives you the default Gnome manager, with panels and desktop and all of that.

```
compiz --replace
```
This gives you more or less the same picture as above, but with the added 3D effects.

```
gnome-shell --replace
```
This gives something that will look different, but will work very similar to the above.

Gnome-shell is just another application, it is not an environment. If you have it installed, you can start it and stop it with the above commands. If you don't start it, it just sits on the HDD and does nothing (it doesn't replace Gnome). You don't select it from the log in menu, you can choose to run it when Gnome loads (after you log in), but this is done with startup applications.

---

### Post by KdotJ on 2010-05-05
thanks you 3Miro, it all makes perfect sense now. I'm gonna give it a spin...

---

### Post by seeker5528 on 2010-05-05
> **KdotJ said:**
> Also, do you think that gnome 2.x will be supported for a long time after?

The literal response to this in itself would be.....

Libraries needed to run Gnome 2 applications will be around, similar to the way Gnome 1.x libraries have been around in many distribution until recently.

But I expect what you really wanted to know is if you can still use Metacity as your window manager. 

Since the window manager does not equal Gnome but is only a small part of it, and Gnome devs are not taking away your ability to use other window managers, you will be free to choose from a variety of window managers and panels for Gnome 3 including Metacity and gnome-panel. 

Whether Metacity continues to be developed under the umbrella of the Gnome desktop or outside of it is another question, but for now there is not a lot of reason to think it won't continue to be worked on in some fashion.

Looking at [this list](http://blogs.gnome.org/aklapper/category/computer/gnome/), there are bugs filed against Metacity related to Gnome 3 readiness, and work continues to fix these things, so even if these things are not all fixed by the time Gnome 3 is released, it should be expected that Metacity will not have a continued reliance on Gnome 2.x stuff over the long haul.

As far as it relates to Ubuntu, I don't think the Ubuntu devs even know what they will do yet, with the initial Gnome 3 releases they may not even include Gnome-Shell as part of the OOBE, much less have it enabled by default. On the other hand, the first release after an LTS may be viewed as the perfect time to stuff Gnome-Shell in there as default, since they will have the bulk of the next 2 years to sort issues out for the next LTS.

Later, Seeker

---

### Post by 3Miro on 2010-05-05
When KDE 4.0 came out, old KDE apps had to be rewritten to match a new API. And again for KDE 4.1. In that sense, Gnome is taking a more evolutionary approach. Old apps would work, including Gnome panel and Metacity. I, for one, think that gnome-shell requiring 3D capable video cars is a mistake. Kwin for KDE 4, can do both, with 3D effects and without them.

Gnome-shell is more then a window manager, but not too much more. It is supposed to be less of a change than KDE 4.0. Naturally Metacity and Compiz will be supported for quite some time. Many KDE fans wanted to have a fork on the KDE project. It did not happen and it was a good thing. I am hoping there will not be a fork in the overall smaller (in terms of fan if not devs) Gnome project.

Another issue is how quickly distros will switch to the new system. About 6 months ago, I tried to find a non-Ubuntu distro with good KDE 4.3 support and there weren't many (Sabayon was the only really good one, Mandriva is free and in cheap only for 32bit and Suse is Novel). On the other hand, many distros still used KDE 3.5. Gnome 2.x will be around in a massive way for at least another 2-3 years. Ubuntu has a short release cycle, so they will make the switch sooner. Gnome-shell is already in the repos, if not necessarily the latest version. If not for 10.10, 11.04 will come with Gnome-shell as the default. Whether or not this will be a good thing is a totally separate issue.

I don't want to pre-judge, but I don't like the way Gnome-shell is going (and I have tested it). I did go for KDE 4.1 and 4.2 beta when they came out, but I will probably stick with XFCE and KDE until at least Gnome-shell 3.3 stable (may test it earlier, but it will not be my default system). Then again, this is me, many people love the new interface.

---

### Post by seeker5528 on 2010-05-06
> **3Miro said:**
> Gnome-shell is more then a window manager

Technically not. There is a relationship that is kinda parallel to what was done in KDE on one hand, but significantly different as well. 

Mutter is the window manager, Gnome-Shell is a plug-in to Mutter. So it's tied specifically to Mutter, if it could be separated and ran independently it would still probably require direct rendering, OpenGL, and compositing. 

If you compare that to KDE.

Kwin is the window manager, Plasma is used to create the shell. Plasma was this idea to create something flexible to allow doing cool stuff on the desktop, which turned out to be useful/flexible enough for applications to use for some of their stuff as well. It's not tied to kwin in any way and doesn't require direct rendering, OpenGL, etc...

You can draw some conclusions based on that, but to really make a judgment on the Gnome side would take a broader analysis of why the Gnome devs chose to do G-S as a plug-in to Mutter and what future limitations result from that, both from the desktop and application perspective, depending on whether G-S can someday be separated from Mutter so you could use G-S with your window manager of choice or not.

I have not seen anything to indicate the G-S developers have plans to turn G-S into something more directly equivalent to Plasma, but that doesn't necessarily mean it couldn't be done.  

Later, Seeker

---

### Post by xenosaga456 on 2010-06-15
wow thanks guys its pretty cool lol i like it

---

