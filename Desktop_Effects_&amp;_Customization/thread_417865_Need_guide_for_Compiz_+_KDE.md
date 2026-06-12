---
title: "Need guide for Compiz + KDE"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by FrozenFOXX on 2007-04-21
I checked out the thread about enabling Compiz effects with Gnome and after searching the thread for KDE mentions the only thing I found was a vague suggestion that it works in KDE but no description of how.


Since last time I tried to install Compiz on Feisty it completely and totally broke my system (it screwed up dpkg if that's believable) I'd like to know if anyone else had a guide about how they're getting it to work with KDE.  I wanted to use Compiz since I understand it's supposed to be stable.  I already have a nVidia GeForce 7800GT with the nvidia-glx drivers and the Kubuntu desktop so I think I'm okay with horsepower and requirements, I just need a step-by-step how-to if that's okay.

---

### Post by Bekker on 2007-04-22
*Stepping in line for a howto*

---

### Post by FrozenFOXX on 2007-04-22
I was under the impression Compiz was supposed to be easy to turn on in Feisty, guess I was wrong.

UPDATE:  nearly 100 views and not **one** person has a CLUE about using Compiz with KDE?  That's not too good.

---

### Post by Justin Trouble on 2007-04-23
I'll join the queue!

I'm experiencing the black window bug with Beryl under KDE despite 128 MB of video RAM ([http://forum.beryl-project.org/viewtopic.php?f=35&t=1664)](http://forum.beryl-project.org/viewtopic.php?f=35&t=1664)).

I hear that this happens less in Compiz.

Using the Copy Rendering fix in Beryl (from the link above) has a huge performance hit on my machine.

---

### Post by tomto66 on 2007-04-23
I'm in line for a Howto as well.

I have Gnome and KDE; under Gnome it's real easy and works well; under KDE I simply cannot find the Desktop Effects.

Tom

---

### Post by rama on 2007-04-23
One more in line. After installing kubuntu I m wandering if I need to install some packages and what I need to do after that.

---

### Post by Bekker on 2007-04-24
Yesterday I tried figuring it out myself, so I installed compiz-kde and compiz-plugins from the repositories. They depend on some other packages like compiz-core, after installation I could start it with "compiz --replace" in a terminal. That had some effect, it removed the top-bar from all windows making it impossible to move them...

The problem is that there isn't a thing like "gnome-compiz-manager" for kde... So I had a hard time figuring out how to enable plugins, and a way to easelly enable/disable compiz. That's why I installed gnome-compiz-manager in the end. This made things a bit simpler, using this manager it's possible to enable the famous spinning cube and it's supposed to be able to enable and disable compiz. Enabling works fine, disable doesn't seem to do anything. And the top-bars are still missing, which really sucks.

So far for my adventures. I will continue to experiment further, first a have to make an exam for school.

---

### Post by Justin Trouble on 2007-04-24
Bekker: I've seen the missing window title bar before. Make sure you've got the right bits in your xorg.conf.

This thread is for Beryl, but IIRC it's also for Compiz - [http://ubuntuforums.org/showthread.php?t=416630](http://ubuntuforums.org/showthread.php?t=416630)

I've been using Beryl for the past few days and my word it's buggy :D

I may have a go with Compiz later. I'm glad Compiz and Beryl are joining forces though.

---

### Post by Justin Trouble on 2007-04-24
Ok, I've got Compiz working in KDE.

First install the 'compiz-kde' package and it's dependancies.

Then the next part I found at [http://forum.compiz.org/viewtopic.php?t=239&highlight=compiz+kde+decorator:](http://forum.compiz.org/viewtopic.php?t=239&highlight=compiz+kde+decorator:)

Assuming you have the GLX_EXT_texture_from_pixmap extension, and you are running your normal window manager, go to a console and type the following command (choose the correct one depending on your card type)

NVIDIA
```
__GL_YIELD="NOTHING" compiz --replace --indirect-rendering gconf &
```

ATI and Intel
```
compiz --replace gconf &
```

If this crashes with a message about GLX_EXT_texture_from_pixmap being missing then run it with this command
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace gconf &
```

Assuming nothing went wrong with this, you will now see your windows but there will be no decorations. Run this command and the decorations (title bar etc.) should appear.

```
kde-window-decorator --replace &
```

I still need to look at automatically starting Compiz on Login. This depends if Compiz works better than Beryl.

---

### Post by Bekker on 2007-04-24
Thanks Justin! That did the trick.

In the mean time I made some more changes:
I removed gnome-compiz-manager and installed compiz-settings. That isn't in the repos, but it sounds better then using something called gnome-compiz-manager in kde. I could only find a edgy build on the net, but it works fine on feisty for me. After installation there's a new button in your task-menu under settings for the compiz settings manager.
Before starting this manager you should have started compiz with
```
compiz --replace &
```
in a terminal. It gives some errors that I haven't sorted out yet, but compiz runs.

After starting the manager succesfully I changed the options for window decoration. As you might have noticed if you try this yourself is that the window decoration theme changed into something gnomisch. That's because it uses "gtk-window-decorator" command, I changed it into "kde-window-decorator --replace" and after a ctrl-alt-backspace I got my favorite kde-theme back and all the goodness of wobblynes and spinning cubes.

It's not working perfect yet. I liked the window snapping in kde, that's gone. Resizing windows is slow and when I maximize a window it seems to fall a little outside my screen at the top.
Maybe this information will help you guys, but I don't feel this is the ultimate solution. Maybe we should wait for kde 4

For reference, my system: amd athlon 2000+xp with 756mb ram and a geforce 6600GT
With Feisty Fawn freshly installed and the nvidia drivers version 9755.

Edit 1: alright now we have two "howto's" :P
Edit 2: Another howto: [compiz+kde+nvidia on slackware]("http://www.linuxquestions.org/questions/showthread.php?t=541473") probarly works on ubuntu.

---

### Post by EMoShunz on 2007-04-24
I can't find the check box to enable 3D in Kubuntu, all the forums I read say you have to manually install 3rd party drivers, d/l beryl or compiz, edit the x.org file to enable 3d acceleration...not easy at all :(
No easy  driver install
No easy 3D activation
No easy Compiz install
I prefer KDE, but it appears the GNOME version of Ubuntu has  KDE beat in the destop effects!

---

### Post by Redcard on 2007-04-24
The Kubuntu team's release notes show that they were not working on the same feature set as Ubuntu. 

For you KDE types, here's the Kubuntu Feisty Fawn release notes.  
[http://kubuntu.org/announcements/7.04-release.php](http://kubuntu.org/announcements/7.04-release.php)

The Desktop effects thing , as well as Avahi et al was an Ubuntu spec.. not a Kubuntu one.

If you wish to get Beryl/Compiz working, I would suggest the respective project forums, and possibly kubuntuforums.net.

---

### Post by EMoShunz on 2007-04-24
At least that's a definitive answer.  Too bad it was not an option, I'd have really liked that.  That should be made an option in the next release.

---

### Post by Redcard on 2007-04-25
To that extent, Emo, sign up on launchpad.net and find out if there is a feature for such a thing. If there is not, make one. And then subscribe to it. (If there is, just subscribe to it.)

THey use subscription numbers to the features in order to determine level of support.. and they might also find some things for you to do.

---

### Post by EMoShunz on 2007-04-25
I will look into that.  It's not like I can create suggestions, just subscribe to existing ones?
As for what I can do...I wish...I used to know VB6 quite well, which basically amounts to nothing anymore.

---

### Post by EMoShunz on 2007-04-25
Closest thing I could find was this...
[https://blueprints.launchpad.net/ubuntu/+spec/kubuntu-xgl](https://blueprints.launchpad.net/ubuntu/+spec/kubuntu-xgl)
looks promising, but not quite what I was hoping for.

---

### Post by shifty_powers on 2007-06-10
Tbh, i found it fairly easy to get kubuntu and beryl working together, using the beryl manager and emerald theme. Have founf it stable and not had any real problems. The only rhing for me is that beryl causes huge frame rate issues with day of defest source, which is know about but not a real problem for me. Haven't got much time for games atm anyway....

Tbh, iirc, i just installed beryl through adept. I admit it took me a little while to get used to, but the beryl manager was very helpful...

---

### Post by Divan Santana on 2007-06-13
yeah kubuntu works ok with beryl and beryl manager and emerald! quite nice, seeing if can get it working with compiz though

---

### Post by kpolice on 2007-06-13
I am running Compiz GIT in my ArchLinux box + fglrx + XGL but I have a problem, when I login usually I have to logout and login again to get window decorations, it seems that there is a problem with KDM and XGL because before I was running in the same computer almost the same setup but with GDM as I also had GNOME installed and I didn't have any problems.

If I use the open source driver it works always but the driver is slower and it doesn't support powerplay.

---

