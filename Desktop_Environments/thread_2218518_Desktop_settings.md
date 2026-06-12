---
title: "Desktop settings"
date: 2014-04-21
forum: Desktop Environments
---

### Post by offir on 2014-04-21
After a lot of work

Ubuntu desktop looks exactly like I want
But there are some small problems
It's not exactly problems
It's more I do not know where the settings


I installed Cairo Dock
And I want him to work without open gl
how do i do that ?


I installed compiz
But somehow the effects do not work
I set 4 desktops
And it does not save
I guess the same reason all the effects are not working
screenshot Is attached


[COLOR="#FF0000"]When I browse to sites I get a message that I need to install Flash (Some work and some do not work)
Although I did it[/COLOR]
[COLOR="#0000FF"]Solved[/COLOR]
[http://www.youtube.com/watch?v=gerD__lYnqc]("http://www.youtube.com/watch?v=gerD__lYnqc")


I have an Nvidia video card
And currently is working with the Linux Driver
What is the difference between drivers
Is there an advantage of Nibida driver for the Linux driver or inverted
screenshot Is attached


Last problem
Home folder
I have opened new folders
And I want to have a shortcut in the left column of the screen
screenshot Is attached
[COLOR="#0000FF"]Solved[/COLOR]

---

### Post by offir on 2014-04-24
Have remained only two problems
I do not get along with them


Question is not related
How the subject of the message has changed
Was written something else there

---

### Post by grumblebum2 on 2014-04-24
For compiz desktops you only need to set the vertical and horizontal virtual size in ccsm.
Once set, if you return to the desktop size tab in ccsm, all settings return to the default 1 workspace and need to be set again.
I have found the linux gfx driver is fine unless gaming.
The gpu temperature regulation may be better with nvidia drivers.
Test for yourself...can always revert.

For cairo-dock I believe to run without opengl the start command is
```
cairo-dock -c
```

Check the manual page via terminal...
```
man cairo-dock
```

---

### Post by offir on 2014-04-26
Thanks for the help

Answers

> For compiz desktops you only need to set the vertical and horizontal virtual size in ccsm.
Once set, if you return to the desktop size tab in ccsm, all settings return to the default 1 workspace and need to be set again.

When I write down the values &#8203;&#8203;of 1 in both upper fields
I can not move the cube
I can switch desktop only through the icon Cairo Dock
The problem is After I click another Desktop in the Icon
I get a desktop with nothing but the image
Without any icons or cairo Dock

There is no way to go back to The first desktop with icons except shutdown and turning on the computer
{At least not something I know}

I added screenshots of all the settings might see something I did not set good

When I filled in the third box the value 4

So it was not a cube

But when I clicked on the icon for the Different desktop on the  Dock
I went to another one with Cairo Dock
Like  it supposed to be with the cube




> For cairo-dock I believe to run without opengl the start command is
Code:

cairo-dock -c

Check the manual page via terminal...
Code:

man cairo-dock




Regarding Cairo Dock

I know what command to run without open gl
I do not know where it will record

Ubuntu 10.04
I had a list of programs that start when the system rises
And there it was possible to change the command
Here I can not find it






> I have found the linux gfx driver is fine unless gaming.
The gpu temperature regulation may be better with nvidia drivers.
Test for yourself...can always revert.

If this is so, I will leave the current
Because it works well
No need to fix what is not broken

---

### Post by offir on 2014-04-26
Rest of screenshots

---

### Post by grumblebum2 on 2014-04-26
> **offir said:**
> Rest of screenshots
As I find your posts are a bit confusing I have some questions for you.
What release of ubuntu did you install?
```
lsb_release -a
```

What session are you logging in to and what window manager is running.
Install this small(90kb) application to help me.
```
sudo apt-get install wmctrl
```

Then...
The session your logging into...
```
echo $DESKTOP_SESSION
```

and the window manager running...
```
wmctrl -m | awk '/Name:/{print $2}'
```

---

### Post by offir on 2014-04-26
> As I find your posts are a bit confusing I have some questions for you.
What release of ubuntu did you install?
Code:

lsb_release -a



```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

```



> echo $DESKTOP_SESSION

```
cairo-dock
```




> wmctrl -m | awk '/Name:/{print $2}'

```
Compiz

```











A few days ago I installed Ubuntu 14.04
After four years of use in Ubuntu 10.04

In Ubuntu 10.04  i used in Cairo  Dock
in Ubuntu 10.04 i  also had the cube (compiz)

When I installed Ubuntu 14.04
I did not like the Unity interface

So I change it  with Cairo Dock

---

### Post by grumblebum2 on 2014-04-26
> **offir said:**
> ```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

```

```
cairo-dock
```

```
Compiz

```

A few days ago I installed Ubuntu 14.04
After four years of use in Ubuntu 10.04

In Ubuntu 10.04  i used in Cairo  Dock
in Ubuntu 10.04 i  also had the cube (compiz)

When I installed Ubuntu 14.04
I did not like the Unity interface

So I change it  with Cairo Dock

ok so your logging into the cairo-dock session with compiz as the window manager.
Compiz is a compositing manager and cairo-dock should run fine with opengl.

I'm not sure where the cairo-dock startup file is located for the cairo-dock session.
You could edit the .desktop file to always run the cairo-dock -c command.
```
gksudo gedit /usr/share/applications/cairo-dock.desktop
```
and change the Exec command to **cairo-dock -c**

or
start up your own instance of **cairo-dock -c** in the Ubuntu/unity session.
Unity is just a plugin for compiz so, using ccsm you can disable unity then enable the window decorations plugin and the cube and add **cairo-dock -c** to startup applications.

---

### Post by offir on 2014-04-26
I tried
Both ways and it does not work
Cairo Dock still works with open gl

Cube does not work Also in Unity

---

### Post by grumblebum2 on 2014-04-26
Open a terminal and run,,,
```
killall cairo-dock
```

then...
```
cairo-dock -c
```

How do you tell which is running?
They look the same to me but terminal shows....
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **cairo-dock -c**

 ============================================================================
	Cairo-Dock version : 3.3.2
	Compiled date      : Apr  7 2014 22:10:21
	Built with GTK     : 3.10
	[COLOR="#FF0000"]Running with OpenGL: 0[/COLOR]
 ============================================================================

```
The cube works...
Disable **dektop wall**
Enable **desktop cube** and **rotate cube**
and 
ccsm > general options > desktop size
and set the **horizontal virtual size** to 4.
It will revert to 1 if you open to that tab again and will need to be reset.

---

### Post by offir on 2014-04-26
> Open a terminal and run,,,
Code:

killall cairo-dock

then...
Code:

cairo-dock -c

How do you tell which is running?

When I go into the properties of Cairo
There is black background and hard to read whatever was written there



```
 ============================================================================
	Cairo-Dock version : 3.3.2
	Compiled date      : Apr  7 2014 22:10:21
	Built with GTK     : 3.10
	Running with OpenGL: 0
 ============================================================================

warning :  (/build/buildd/cairo-dock-3.3.99.beta1.2.really.3.3.2/src/gldit/cairo-dock-utils.c:cairo_dock_launch_command_sync_with_stderr:231)  
  No value set for `/desktop/gnome/interface/font_name'

cairo_dock_create_surface_from_image: assertion 'cImagePath != NULL' failed
Cairo-Dock - Launcher API Daemon is already running (1758)
_cd_find_volume_name_from_drive_name: assertion 'pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion 'pDrive != NULL' failed
warning :  (/build/buildd/cairo-dock-3.3.99.beta1.2.really.3.3.2/src/gldit/cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:463)  
  This file (/home/offir/.config/cairo-dock/extras/weather/7degrees/.svg) doesn't exist or is not readable.

```




> The cube works...
Disable dektop wall
Enable desktop cube and rotate cube
and
ccsm > general options > desktop size
and set the horizontal virtual size to 4.
It will revert to 1 if you open to that tab again and will need to be reset. 


I tried it
I have it working on another computer with Ubuntu 10.04

But here somehow it does not work
If I change the value to 4 it goes crazy



If you happen to have teamviewer
I'd show you what happens

---

### Post by grumblebum2 on 2014-04-26
Try starting fresh,

Reset compiz to defaults....
```
dconf reset -f /org/compiz/
```

Log out ...log back in.
You will see unity is now showing.
Open ccsm and disable the unity plugin
The window decoration should still be enabled when you disable unity...check window decoration is enabled.
Then do as in previous post to enable the cube.

---

### Post by offir on 2014-04-26
i try this two 
it did not work


i had to restart the computer

---

### Post by grumblebum2 on 2014-04-26
I have no idea then ...I tested the exact procedure on my Trusty install first.
What does this command give you...
```
/usr/lib/nux/unity_support_test -p

```
eg mine
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **/usr/lib/nux/unity_support_test -p **
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.38

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by offir on 2014-04-26
```
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV96
OpenGL version string:  3.0 Mesa 10.1.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

---

### Post by grumblebum2 on 2014-04-26
In an earlier post you said you installed compiz.
Why would you need to do this when it's already installed in Ubuntu?
Did you remove anything?

No more answers except
try installing the proprietary nvidia driver.

---

### Post by offir on 2014-04-26
i install the ccsm
i did not remove anything 


driver is installed

---

### Post by grumblebum2 on 2014-04-26
> **offir said:**
> i install the ccsm
i did not remove anything 


driver is installed
Your previous post showed the open-source nouveau
driver was in use???
> OpenGL vendor string:   **nouveau**

---

### Post by offir on 2014-04-27
i dont konw what is nouveau
Right after I installed Ubuntu 14.04
I went into the software manager
And installed the 

ccsm
cairo doak
vlc
avidemux
amule
qbittorrent
thunar file manager
fslint
gimp
qcomicbook

and from the internet i install 

teamviewer 9
ubuntu tweak

```
sudo apt-get install ubuntu-restricted-extras 
```
```
sudo apt-get install flashplugin-installer
```
```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```
```
sudo apt-get install oracle-java8-installer
```

Beyond that i did not install anything

---

### Post by grumblebum2 on 2014-04-27
Nouveau is the open-sourced nvidia driver.
The proprietary closed-source nvidia driver usually performs better with 3d.
To check what driver your card may need first, run...
```
lspci -nnk | grep -iA2 vga
```
then search [**_[COLOR="#B22222"]nvidia drivers[/COLOR]_**]("http://www.nvidia.com/Download/index.aspx?lang=en-us") for your card.
The one shown may be a little bit later than whats shown in software-properties-gtk.


To install run....
```
software-properties-gtk --open-tab=4
```
and  wait while drivers are found, then choose a driver.
I usually choose the one labelled "proprietary,tested" which should be the most stable.
Click the apply button and reboot once installation has finished.

After reboot check driver in use with...
```
lspci -nnk | grep -iA2 vga
```

---

### Post by offir on 2014-04-27
OK
I think I understand What're you talking about


I referred to it at the beginning of the message
And now I see in the picture the name of the driver is nouveau
Here's the screenshot again


You wrote
> I have found the linux gfx driver is fine unless gaming.
The gpu temperature regulation may be better with nvidia drivers.
Test for yourself...can always revert. 

And I wrote

> If this is so, I will leave the current
Because it works well
No need to fix what is not broken 

---

### Post by PJs Ronin on 2014-04-27
That screenshot is telling you the proprietary driver, 331.38, is NOT in use even thou it is selected in the top part of the image.   This is supported by your post #15:> OpenGL vendor string:   nouveau

You have something wrong with your system and I'm not smart enough to show you how to fix it.

---

### Post by offir on 2014-04-28
Another attempt

I think the problem is in open gl
That's a guess



Is there anyone else that might come across the same symptoms

---

### Post by grumblebum2 on 2014-04-29
[COLOR="#FF0000"]EDIT[/COLOR] Oops already ran this. Ignore.

Run the unity support test....
```
/usr/lib/nux/unity_support_test -p
```

eg mine
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.38

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by grumblebum2 on 2014-04-29
What puzzles me is why you have no 3d effects with compiz when your unity support test checks ok.
Compiz should be ok with the the nvidia or nouveau driver.

The fact that the nvidia driver is selected in the drivers tab but the nouveau driver is loading on boot shouldn't matter.
Just means the nvidia driver is failing to load for some reason and reverts to the nouveau driver.

---

### Post by offir on 2014-04-29
I have some effects
Almost everything except the cube

---

### Post by grumblebum2 on 2014-04-29
If you want, try and load my saved ccsm.profile .
I started with the default profile and just enabled the cube as I described earlier.

Before you do this, open a terminal just in case you need to reload unity.
Save the attached  archive.
Extract the archive to reveal the ccsm.profile file.

Open ccsm and hit "preferences" > import 
and navigate to the extracted ccsm.profile file.
After importing, let it run for at least 30secs before you click on anything.

If unity  fails to reload properly (eg no decorations), run 
```
setsid unity
``` 
in the terminal.
Now test to see if you have the cube.

If unity is still buggered up, run...
```
dconf reset -f /org/compiz/ && setsid unity
```
Disable the unity plugin if you just want cairo-dock.

---

### Post by offir on 2014-04-29
Dude

You are a genius

It worked
Not only that
With it I found the problem

The problem is 3d windows Effect
Once marking [COLOR="#FF0000"][SIZE=3]V[/SIZE][/COLOR] No Cube
Remove [COLOR="#FF0000"][SIZE=3]V[/SIZE][/COLOR] the cube returns


Wonder why it makes a problem


in the Icon of the General options
The value registered screen resolution is 640 x 480

My resolution is 1152 x 864

is it ok ?

---

### Post by grumblebum2 on 2014-04-29
The 3d windows plugin has been known not to work for a while now but should have been disabled when I 
first gave you the compiz reset command back in post #12.

Canonical only concentrates on the plugins it uses in unity.
The extra plugins you install aren't officially supported and from time to time 
some just fail to work properly as compiz develops. 

> in the Icon of the General options
 The value registered screen resolution is 640 x 480

 My resolution is 1152 x 864

 is it ok ?
Mines the same. Just leave as is.

Long process but we got there. :)

Once you have compiz how you like, use 
ccsm > preferences 
to export your compizconfig profile so you can easily import your saved profile 
if you mess compiz up.

---

### Post by offir on 2014-04-29
i will do it 
and save the file on e mail 

Thank you for helping

---

