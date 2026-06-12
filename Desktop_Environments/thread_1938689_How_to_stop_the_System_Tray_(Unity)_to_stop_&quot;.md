---
title: "How to stop the System Tray (Unity) to stop &quot;auto hiding&quot;?"
date: 2012-03-10
forum: Desktop Environments
---

### Post by iDudetu on 2012-03-10
Hi All,

I am not sure if I am posting in the "right" place - as this is my first post at the Ubuntu forums - please let me know if it would be better suited in another area.

I have noticed on my Ubuntu 11 install that the Unity System Tray - which I can only guess is the "equivalent" to the Windows Taskbar - keeps "hiding" whenever apps are dragged over it, or alternatively whenever app windows are made to cover the area that it occupies.

I would like to stop this "scrolling" / "hiding" behaviour! Ideally I want the System Tray to stay exactly where it is, on the left hand side of my screen, and I don't want it going anywhere under any circumstances.

Any suggestions on how to achieve this will be greatly appreciated.

Kind Regards,

iDudetu

---

### Post by rg4w on 2012-03-10
If you install Compiz Config Settings Manager from the Ubuntu Software Center, you'll find in it a section called "Unity Plugin" - there you'll find settings to adjust the behavior of the Launcher.

---

### Post by grahammechanical on 2012-03-10
By the way. That "Dodge windows" behavior has been removed in 12.04. And already people are complaining. They say they wanted it.  You don't. Other do. That is life.

Also in 12.04 you can switch off or on the Launcher autohide behavior in the Appearance utility in System Settings. You will not need to install Compiz Config Settings Manager (CCSM) to do that.

Regards.

---

### Post by rg4w on 2012-03-10
> **grahammechanical said:**
> By the way. That "Dodge windows" behavior has been removed in 12.04. And already people are complaining. They say they wanted it.  You don't. Other do. That is life.
I don't understand why they couldn't just change the default but leave Dodge available as an option.  While I prefer a persistent Launcher myself, Dodge was a truly innovative solution not found in any other OS, and it seems a great many people have come to love it.

> Also in 12.04 you can switch off or on the Launcher autohide behavior in the Appearance utility in System Settings. You will not need to install Compiz Config Settings Manager (CCSM) to do that.Unfortunately, while the CCSM Unity plugin currently provides four options for Launcher behavior, the new Settings panel in 12.04 provides only two (show or auto-hide).

Worse, nearly all of the other settings in CSSM's Unity Plugin aren't in the new Settings panel at all, requiring users to use CCSM to adjust those behaviors (or anomalies, depending on one's view of them <g>).  

Ironically, this decision to go with unusually sparse options comes at the very time some members of the team would like to ditch CCSM altogether, thus requiring CCSM be maintained.

I can understand not porting everything CCSM does to the Settings panel, or even all of the options in its Unity plugin.

But as it is, 12.04 accomplishes something that to the best of my knowledge has never been achieved by any other distro:  they have fewer options available to the user to adjust appearance than even Mac OS. ;)

---

### Post by iDudetu on 2012-03-10
Hi Everyone,

Thanks very much for your kind responses.

Regards

iDudetu

---

### Post by iDudetu on 2012-03-13
Hi Everyone,

I tried the Compiz..., but it didn't change the behaviour of the System Tray as I had expected. I tried every different setting, and sure enough the tray still "disappeared" off screen, only to return when I moused over the very left edge of the screen!

To reiterate I just want to "glue" the System Tray in place so that it behaves like the default Windows Taskbar - in so far as it does not "hide" under any conditions.

What an annoying feature! But what it super annoying is that you can't right click on the tray, as you can in Windows, and dictate behaviour in a logical way.

For all those who like the tray to hide - I challenge you to do some work on your computer, because I am the hair and you are the tortoise - there is no way to be productive on a workstation with the tray hiding all the time!

Is it possible to configure this - or is it "bye bye" Ubuntu for another 5 years?

Kind Regards,

iDudetu

---

### Post by iDudetu on 2012-03-13
Final clarification - please see this YouTube video (available in 720p)

[Video of Unity Plug-in Settings having Zero effect on the System Tray!]("http://www.youtube.com/watch?v=hBrCvk57ElI&feature=youtu.be")

---

### Post by stinkeye on 2012-03-13
Are you in the ubuntu-2d session?
In the terminal
```
echo $DESKTOP_SESSION
```

Log out and choose the "ubuntu" session and login.
[ATTACH]214206[/ATTACH]


Run 
```
echo $DESKTOP_SESSION
```

If it still shows **ubuntu-2d** 
your gfx card may not have the drivers installed or cannot run compiz and
you are being dropped back to the 2d session.

Post the output of...
```
/usr/lib/nux/unity_support_test -p
```
eg> [COLOR="Olive"]glen@Oneiric:~$[/COLOR] **/usr/lib/nux/unity_support_test -p **
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    **yes**
Not blacklisted:          **yes**
GLX fbconfig:             **yes**
GLX texture from pixmap:  **yes**
GL npot or rect textures: **yes**
GL vertex program:        **yes**
GL fragment program:      **yes**
GL vertex buffer object:  **yes**
GL framebuffer object:    **yes**
GL version is 1.4+:       **yes**

Unity 3D supported:       **yes**


If you are only able to log in to the ubuntu-2d session
run this command to set the launcher as never hide.
```
gsettings set com.canonical.Unity2d.Launcher hide-mode 0
```

To set back to default
```
gsettings reset com.canonical.Unity2d.Launcher hide-mode
```


**P.S** If you do get into the "ubuntu" session running compiz 
use this to set the launcher to never hide...
```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
```

---

### Post by iDudetu on 2012-03-16
Hi Stinkeye,

I ran this code ```
gsettings set com.canonical.Unity2d.Launcher hide-mode 0
```and all is good.

I forgot to mention in my original post that I am running Ubuntu in VMware Workstation - which probably explains everything!

Here is the output from this code ```
/usr/lib/nux/unity_support_test -p
```:

[HTML]
rocker@ubuntu:~$ echo $DESKTOP_SESSION
ubuntu-2d
rocker@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
[/HTML]

Thanks very much for your assistance - and I dig you're signature mate (pass the vegemite, LOL).

Cheers

iDudetu

---

### Post by iDudetu on 2012-04-09
Hi All,

I am now able to keep the "system tray" over other windows - however unlike in Windows the applications are now going behind the system tray!

I would like the app windows to never go behind the system tray, and respect the system tray as a boundary, similar to how the display area boundaries are respected.

Here is a link which clarifies what I am seeing:

[IMG]http://www.systemcontrol.com.au/dd/Applications-go-behind-system-tray.JPG[/IMG]

Kind Regards,

iDudetu

---

### Post by stinkeye on 2012-04-09
Doesn't hapeen on my 11.10 install in unity 2d.
Try creating a new user account and see if it happens when logged into
that account.

---

### Post by Krytarik on 2012-04-10
> **stinkeye said:**
> If you are only able to log in to the ubuntu-2d session
run this command to set the launcher as never hide.
```
gsettings set com.canonical.Unity2d.Launcher hide-mode 0
```> **iDudetu said:**
> I am now able to keep the "system tray" over other windows - however unlike in Windows the applications are now going behind the system tray! I would like the app windows to never go behind the system tray, and respect the system tray as a boundary, similar to how the display area boundaries are respected.
Please see my earlier post here:

[http://ubuntuforums.org/showthread.php?p=11800594#post11800594](http://ubuntuforums.org/showthread.php?p=11800594#post11800594)

Regards.

---

