---
title: "Compiz not working"
date: 2011-10-26
forum: Desktop Environments
---

### Post by yoramdavid on 2011-10-26
I am running Ubuntu 11.10 classic.

I want to use Compiz as my window manager but it will not work.
When I start the system, I get no minimize, maximize and close icons on windows.
I have to have the command ```
metacity --replace
``` on the startup programs in order to have them.
If I disable it and start compiz via the fusion-icon, the desktop freezes.
I did the test and it was ok but one thing: ubuntu-composite manager had to be disabled.
I disabled it but compiz did not work either.

How can I make compiz work and remove the ```
metacity --replace
```command from startup?

Thanks.

---

### Post by yoramdavid on 2011-10-29
Any help would be appreciated, I am still stuck with the problem.
Thanks.

---

### Post by yoramdavid on 2011-10-31
I don't know what's wrong with my Ubuntu...
Is it normal that I need to have the command:
```
metacity --replace
```
In the startup items to have minimize, maximize and close buttons on windows?

Please help.

Thank you.

---

### Post by 3Miro on 2011-10-31
No, it is not normal.

Which version of Ubuntu is this?

---

### Post by yoramdavid on 2011-10-31
> **3Miro said:**
> No, it is not normal.

Which version of Ubuntu is this?

It is Ubuntu 11.10 in classic mode.
Thank you.

---

### Post by 3Miro on 2011-11-01
Sorry it took me so long to respond, I had to test this on my laptop.

Whan I login with Gnome-classic (supposedly with effects), I only get Metacity working. I had to manually start compiz --replace from the terminal and then I got the desktop effects, however, the decorations took a minute to load. For the decorations, you need to to go to CCSM (compizconfig settings manager) and go to Windows Decorations. Then make sure you have the command:

```
/usr/bin/compiz-decorator
```

After that you should be able to run "compiz --replace" in the terminal and have compiz.

In order to make this run on startup, you can add the "compiz --replace" command to the starting applications. A better way would probably be to install fusion-icon (from the software center) and then use "fusion-icon" to select compiz as the default WM (you will need to add fusion icon to the startup applications).

I hope this works for you.

---

### Post by yoramdavid on 2011-11-01
> **3Miro said:**
> Sorry it took me so long to respond, I had to test this on my laptop.

Whan I login with Gnome-classic (supposedly with effects), I only get Metacity working. I had to manually start compiz --replace from the terminal and then I got the desktop effects, however, the decorations took a minute to load. For the decorations, you need to to go to CCSM (compizconfig settings manager) and go to Windows Decorations. Then make sure you have the command:

```
/usr/bin/compiz-decorator
```

After that you should be able to run "compiz --replace" in the terminal and have compiz.

In order to make this run on startup, you can add the "compiz --replace" command to the starting applications. A better way would probably be to install fusion-icon (from the software center) and then use "fusion-icon" to select compiz as the default WM (you will need to add fusion icon to the startup applications).

I hope this works for you.

Thank you for your response.

I had compiz manager already installed and the fusion icon as well.
From the fusion icon, compiz is already the default window manager but it does not work (I think it says it is the default but it is not even running). Windows decorations are enabled in compiz, but not working, since I think compiz is not running in the system.

The command:
```
/usr/bin/compiz-decorator
```
Gives me the following output:
```
Starting unity-window-decorator

```
Then nothing happens.

When I run the command:
```
compiz --replace
```
The windows got a little distorted, and the desktop freezes, and I have to restart the x serer with Ctrl+Alt+Backsapce.

I hope this gives you enough information to help me.
Thank you.

---

### Post by typhoon_tip on 2011-11-01
Did you do an upgrade to 11.10 from 11.04 or was it a fresh install ? Seems to me like a normal mess that happens when you play around with compiz in 11.10 (easy to break everything), or something that happen when you upgrade from 11.04.

If you did an upgrade, I suggest you to reset all the default settings of compiz and unity before starting over again. You will find a lot of threads in this forum that has the command sequence to do a proper reset of compiz.

---

### Post by yoramdavid on 2011-11-02
> **typhoon_tip said:**
> Did you do an upgrade to 11.10 from 11.04 or was it a fresh install ? Seems to me like a normal mess that happens when you play around with compiz in 11.10 (easy to break everything), or something that happen when you upgrade from 11.04.

If you did an upgrade, I suggest you to reset all the default settings of compiz and unity before starting over again. You will find a lot of threads in this forum that has the command sequence to do a proper reset of compiz.

I did an upgrade from 11.04.
Compiz was already giving problems in 11.04, when unity got installed on the upgrade from 10.10.
I do not use Unity (2D) but it is still installed in the system.
Unity 3D never worked on this computer.
I will search for threads about resetting compiz to defaults settings.
What about resetting unity default settings to default? I would prefer to remove it.

Thank you for your time.

---

### Post by 3Miro on 2011-11-02
Unity is only a plugin for compiz, so removing will probably not gain you anything.

If you are having problems with compiz in general, I should ask you about your video card. Older Nvidia cards don't work with Unity (although they should work with compiz) and recently ATI dropped support for some of their older cards, hence even if compiz worked fine in the past, it may not run now.

You can try to go into the compiz settings and disable as many of the extra plugins as you can find. For example, you can disable the windows animations. It is possible that one effect in particular is breaking compiz and disabling it may fix all problems.

---

### Post by yoramdavid on 2011-11-02
> **3Miro said:**
> Unity is only a plugin for compiz, so removing will probably not gain you anything.

If you are having problems with compiz in general, I should ask you about your video card. Older Nvidia cards don't work with Unity (although they should work with compiz) and recently ATI dropped support for some of their older cards, hence even if compiz worked fine in the past, it may not run now.

You can try to go into the compiz settings and disable as many of the extra plugins as you can find. For example, you can disable the windows animations. It is possible that one effect in particular is breaking compiz and disabling it may fix all problems.

I have NVIDIA display driver.

I did the reset to the default settings using this command:
```
gconftool-2 --recursive-unset /apps/compiz
```
I then restarted the system and ran the
```
/usr/bin/compiz-decorator
```
which gave me again the following output:
```
Starting unity-window-decorator
```
Then the same happende when running the
```
compiz --replace
```
Which froze the desktop again. I can only move the mouse around. Nothing else.

In the console a lot of Initializing options such as opengl, decor, mousepoll, place, resize, animatin, workarounds, etc were done successefully and one problem and one warning:

Error:
Compiz (core) - Error: Plugin 'text' not loaded.

Warning:
Compiz (expo) - Warn: failed to bind image to texture

I then restarted the xserver and ran compiz-manager and started to disable all plugins (uncheck the tick marks on the boxes).
Compiz manager closed when I tried to uncheck the following plugins:
Composite
OpenGL
Compiz Library Toolbox

Then after restarting the application with all the other plugins deactivated, I was able to deactivate those as well.

Then I ran the command ```
compiz --replace
```
And got no errors, and desktop is fine but one thing: I have no minimize, maximize and close buttons and no bar at the top to move windows around.

It is when I try to enable the "OpenGl" plugin that the desktop freezes.

---

### Post by 3Miro on 2011-11-02
The command:
```
compiz --replace
```
restarts both compiz AND the windows decorator.

What you need to do is to go to CCSM and find the "Windows Decorations" plugin, in that plugin you need to add the command:

```
/usr/bin/compiz-decorator
```
or
```
/usr/bin/compiz-decorator --replace
```
Then the decorator should run if you restart compiz. You should make sure the decorations plugin is enabled.

---

### Post by yoramdavid on 2011-11-02
> **3Miro said:**
> The command:
```
compiz --replace
```
restarts both compiz AND the windows decorator.

What you need to do is to go to CCSM and find the "Windows Decorations" plugin, in that plugin you need to add the command:

```
/usr/bin/compiz-decorator
```
or
```
/usr/bin/compiz-decorator --replace
```
Then the decorator should run if you restart compiz. You should make sure the decorations plugin is enabled.

I am not sure I understand, where and how exactly do I do that?
When running the Compiz settings manager application, I do not see where to add a command...

All I see in the CCSM application is a tab called "preferences" where thre is a list of plugins. On the left all the plugins and on the right the plugins in use.
All is greyed out, no editing possible.

Thank you.

---

### Post by 3Miro on 2011-11-02
> **yoramdavid said:**
> I am not sure I understand, where and how exactly do I do that?
When running the Compiz settings manager application, I do not see where to add a command...

All I see in the CCSM application is a tab called "preferences" where thre is a list of plugins. On the left all the plugins and on the right the plugins in use.
All is greyed out, no editing possible.

Thank you.

Here is a screenshot of my CCSM. This is neither Gnome nor Ubuntu, but CCSM should be working regardless whether or not compiz is. The second image shows the line where you have to enter the command (instead of "emerald --replace" use the compiz-decorator command).

I will double check that tomorrow when I get back to Ubuntu at work. However, you should be able to edit CCSM with or without compiz working, try reinstalling CCSM to make sure it is working properly. You can also run it from the terminal to see if it gives any error messages.

---

### Post by yoramdavid on 2011-11-03
> **3Miro said:**
> Here is a screenshot of my CCSM. This is neither Gnome nor Ubuntu, but CCSM should be working regardless whether or not compiz is. The second image shows the line where you have to enter the command (instead of "emerald --replace" use the compiz-decorator command).

I will double check that tomorrow when I get back to Ubuntu at work. However, you should be able to edit CCSM with or without compiz working, try reinstalling CCSM to make sure it is working properly. You can also run it from the terminal to see if it gives any error messages.

I could not find the window decoration plugin, found it now after I reinstalled compiz and plugins.
The command ```
/usr/bin/compiz-decorator
```was already there. I also tried  the command ```
/usr/bin/compiz-decorator --replace
``` with no success.

Starting CCSM from the console gives the following (a lot of "failed"):
```

yoram@yoram-II:~$ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : false
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
/usr/lib/python2.7/dist-packages/ccm/Window.py:92: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.LeftPane.pack_start(page.LeftWidget,   True, True)
/usr/lib/python2.7/dist-packages/ccm/Window.py:95: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.show_all()
/usr/lib/python2.7/dist-packages/ccm/Widgets.py:1567: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self._table.attach (button, col, col+1, row, row+1, 0, xpadding=TableX, ypadding=TableY)
Loading icons...
/usr/lib/python2.7/dist-packages/ccm/Widgets.py:1572: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.show_all ()
Initializing gnomecompat options...done
Initializing decor options...done
Initializing opengl options...done
Initializing composite options...done
```

Still no top bar menu on windows if I do not run "metacity --replace".
Desktop still freezes if I run "compiz --replace".

Thank you.

---

### Post by stinkeye on 2011-11-03
The command to reset compiz to default is
```
gconftool-2 --recursive-unset /apps/compiz-1
```

Give it 10 to 15 secs to load then run 
```
compiz --replace &
```

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> The command to reset compiz to default is
```
gconftool-2 --recursive-unset /apps/compiz-1
```

Give it 10 to 15 secs to load then run 
```
compiz --replace &
```

Still no improvements, same as before.
Thank you.

---

### Post by stinkeye on 2011-11-03
Are you loading the fusion-icon at boot or using it to change settings.
May not work that well with compiz on 11.10.

---

### Post by stinkeye on 2011-11-03
This info would be useful

video and driver
```
lspci -k | grep -A3 VGA
```

and you could also run this compiz test
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by 3Miro on 2011-11-03
What is happening for me is that when I type "compiz --replace" I do lose all decorations and the desktop freezes for about 20 seconds, however, then the whole thing resets itself and I do get compiz working just fine (decorations, effects and so on).

Can you use stinkeye's command "lspci -k | grep -A3 VGA" to let us know the exact model of your video card. Then you should also check the Nvidia Settings application from either System or Other (or Accessories, I am using Intel video right now so I am not sure where the app will appear).

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> Are you loading the fusion-icon at boot or using it to change settings.
May not work that well with compiz on 11.10.

I just using the fusion-icon to test compiz now.
It is not starting at boot. I am afraid to do so, then if it freezes my desktop, I will not know how to remove it from the startup.

Thank you

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> This info would be useful

video and driver
```
lspci -k | grep -A3 VGA
```

and you could also run this compiz test
```
/usr/lib/nux/unity_support_test -p
```

Here are the results:
```
lspci -k | grep -A3 VGA
01:00.0 [COLOR="Red"]**VGA**[/COLOR] compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
	Subsystem: Hewlett-Packard Company Device 30bb
	Kernel driver in use: nvidia
	Kernel modules: nvidia_173, nvidia_current, nouveau, nvidiafb
```

And:
```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

Not software rendered:    **[COLOR="YellowGreen"]yes[/COLOR]**
Not blacklisted:          [COLOR="Red"]**no**[/COLOR]
GLX fbconfig:             [COLOR="YellowGreen"]**yes**[/COLOR]
GLX texture from pixmap:  [COLOR="YellowGreen"]**yes**[/COLOR]
GL npot or rect textures: [COLOR="YellowGreen"]**yes**[/COLOR]
GL vertex program:        [COLOR="YellowGreen"]**yes**[/COLOR]
GL fragment program:      [COLOR="YellowGreen"]**yes**[/COLOR]
GL vertex buffer object:  [COLOR="YellowGreen"]**yes**[/COLOR]
GL framebuffer object:    [COLOR="YellowGreen"]**yes**[/COLOR]
GL version is 1.4+:       [COLOR="YellowGreen"]**yes**[/COLOR]

Unity 3D supported:       **[COLOR="Red"]no[/COLOR]**
```

Thank you

---

### Post by yoramdavid on 2011-11-03
> **3Miro said:**
> What is happening for me is that when I type "compiz --replace" I do lose all decorations and the desktop freezes for about 20 seconds, however, then the whole thing resets itself and I do get compiz working just fine (decorations, effects and so on).

Can you use stinkeye's command "lspci -k | grep -A3 VGA" to let us know the exact model of your video card. Then you should also check the Nvidia Settings application from either System or Other (or Accessories, I am using Intel video right now so I am not sure where the app will appear).

I waited for about two minutes after running the "compiz --replace" command, desktop did not unfreeze. I can move the mouse and when I click on something I get a sound. That is all.
The results for the command "lspci -k | grep -A3 VGA" are above.
As for the Nvidia settings, I have an application called "Nvidia Xserver settings", some of the settings are (which exactly would be useful)):

X Server Information tab:
  System Information
    Operating System:      Linux-X84_64
    NVIDIA Driver vErsion: 280.13

  X Sever Information
    Server Version Number: 11.0
    Server Vendor String:  The X.Org Foundation
    Server Vendor Version: 1.10.4 (11004000)
    NV-CONTROL Version:    1.27
    Screens:               1

nvidia-settings Configuration tab:
  Enable ToolTips (enabled)
  Display Status Bar (enabled)
  Slider Text Entries (enabled)
  Include X Display Names in the Config Gile (diabled)
Show "Really Quit?" Dialog (enabled)

X Screen 0 tab:
X Screen Information:
...
GPUS:                 GeForce Go 7400 (GPU 0)
  
Thank you.

---

### Post by stinkeye on 2011-11-03
> Not blacklisted:          no
Apparently your vid card is blacklisted from running compiz.
eg my output
```
glen@Oneiric:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 285.05.09

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

You may want to do a search for your card and compiz.

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> Apparently your vid card is blacklisted from running compiz.
eg my output
```
glen@Oneiric:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 285.05.09

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

You may want to do a search for your card and compiz.

Ah. That was not always the case because I used compiz before.
Thank you.

---

### Post by bluexrider on 2011-11-03
I had an issue like this too. Found that the graphics card isn't what it should be.

Used this to check it out. 

[http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/](http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/)

---

### Post by stinkeye on 2011-11-03
I found a youtube video showing you how to force start unity.
It's for 11.04 but worth a try.

Hit the show more button for instructions.
[**_[COLOR="DarkRed"]How to 'force-enable' Unity[/COLOR]_**]("http://www.youtube.com/watch?v=5F4VsEc-Arc")

---

### Post by yoramdavid on 2011-11-03
> **bluexrider said:**
> I had an issue like this too. Found that the graphics card isn't what it should be.

Used this to check it out. 

[http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/](http://www.makeuseof.com/tag/check-if-compiz-will-run-well-on-your-linux-box-with-compiz-check/)

Here is the result of the check:
```
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 11.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [GeForce Go 7400] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ **[COLOR="Olive"]OK [/COLOR]**]
 Checking for non power of two support...          [ **[COLOR="Olive"]OK [/COLOR]**]
 Checking for composite extension...               [ **[COLOR="Olive"]OK [/COLOR]**]
 Checking for FBConfig...                          [ **[COLOR="Olive"]OK [/COLOR]**]
 Checking for hardware/setup problems...           [ **[COLOR="Olive"]OK [/COLOR]**]
```
 
Thank you.

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> I found a youtube video showing you how to force start unity.
It's for 11.04 but worth a try.

Hit the show more button for instructions.
[**_[COLOR="DarkRed"]How to 'force-enable' Unity[/COLOR]_**]("http://www.youtube.com/watch?v=5F4VsEc-Arc")

No luck with that either.
If I do not have Unity installed, perhaps that is why?

Thank you.

---

### Post by stinkeye on 2011-11-03
Unity is a plugin for compiz which is part of the default 11.10 install.
Can you log into the ubuntu session with unity 3d or does it fall back to 2d?

The only other fix I know to see if you can get compiz to work is to 
remove all the config files
Run one at a time...
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> Unity is a plugin for compiz which is part of the default 11.10 install.
Can you log into the ubuntu session with unity 3d or does it fall back to 2d.

Unity 3D is not installed either since it never worked, I think my system is perhaps too slow (Intel Dual core T5500 1.66Mhz, 2006 MiB, NVIDIA GeForce Series Video Driver 7400, Video ram 256 MB, GPU frequency 100 MHz).

So when I had 2D installed it used to fall back into it.
I now do not have Unity 2D installed, I am using Gnome-classic (as I said at the beginning of the post).

Thank you for the thumbnail, I went into the CCSM and I do not have that plugin :confused:

Thank you

---

### Post by stinkeye on 2011-11-03
I don't understand.
Did you uninstall unity?
No reason to , you just disable the plugin in compiz.

ie I can change to a gnome classic session from within this unity 3d session.[LIST]Disable the unity plugin in ccsm (unity Panel and launcher gone)[/LIST]
[LIST]
[*]Start up gnome-panel
[/LIST] 

and that's it I'm running classic gnome with compiz.

---

### Post by yoramdavid on 2011-11-03
> **stinkeye said:**
> I don't understand.
Did you uninstall unity?
No reason to , you just disable the plugin in compiz.

Yes, I uninstalled it.
I do not like Unity and went back to gnome-classic.
I uninstalled it because of need of space.

Does that affect the effectiveness of compiz on the gnome-classic desktop?

Thank you.

---

### Post by stinkeye on 2011-11-03
> **yoramdavid said:**
> Yes, I uninstalled it.
I do not like Unity and went back to gnome-classic.
I uninstalled it because of need of space.

Does that affect the effectiveness of compiz on the gnome-classic desktop?

Thank you.

I don't know but it's quite possible since you said you had used compiz before.

---

### Post by 3Miro on 2011-11-03
Unless you are running Unity, it doesn't get loaded into RAM. Since it is only a plugin for compiz, Unity takes hardly any space on the HDD.

Try installing it back (i.e. install ubuntu-desktop) and then try to get in the Gnome-fallback session. It is possible that the compiz decorator somehow relies on Unity.

PS your CPU and RAM are enough for both Unity and Gnome+Compiz. The video is incompatible with Unity, but compiz should work.

---

### Post by yoramdavid on 2011-11-03
> **3Miro said:**
> Unless you are running Unity, it doesn't get loaded into RAM. Since it is only a plugin for compiz, Unity takes hardly any space on the HDD.

Try installing it back (i.e. install ubuntu-desktop) and then try to get in the Gnome-fallback session. It is possible that the compiz decorator somehow relies on Unity.

PS your CPU and RAM are enough for both Unity and Gnome+Compiz. The video is incompatible with Unity, but compiz should work.

I installed gnome-desktop and with that Unity got also installed and the Unity plugin was now in compiz.
So I enabled the plugin.
I disabled the "metacity --replace" from starting up, rebooted the pc and reloaded the compiz window manager from the fusion-icon.
Again the desktop freezes. The top bar is there on the menus, but I cannot do anything.

Thank you

---

### Post by 3Miro on 2011-11-03
> **yoramdavid said:**
> I installed gnome-desktop and with that Unity got also installed and the Unity plugin was now in compiz.
So I enabled the plugin.
I disabled the "metacity --replace" from starting up, rebooted the pc and reloaded the compiz window manager from the fusion-icon.
Again the desktop freezes. The top bar is there on the menus, but I cannot do anything.

Thank you

The idea is not to have the Unity plugin running (I don't think your video card supports it), the idea is to have it just installed. Also, you need to install ubuntu-desktop, which is probably a different package from Gnome-desktop.

Disable Unity from CCSM, make sure you have the decorator in the decorations plugin and then try to start compiz again.

---

### Post by yoramdavid on 2011-11-04
> **3Miro said:**
> The idea is not to have the Unity plugin running (I don't think your video card supports it), the idea is to have it just installed. Also, you need to install ubuntu-desktop, which is probably a different package from Gnome-desktop.

Disable Unity from CCSM, make sure you have the decorator in the decorations plugin and then try to start compiz again.

Still no luck...
With compiz running I get the top bar menu, but cannot do anything at all. Desktop freezes, just the cursor goes around...

Thank you

---

### Post by 3Miro on 2011-11-04
> **yoramdavid said:**
> Still no luck...
With compiz running I get the top bar menu, but cannot do anything at all. Desktop freezes, just the cursor goes around...

Thank you

I am sorry yoramdavid, at this point I am out of ideas. I will not be able to help you any further.

If 11.10 is giving you hard times and if you prefer the old Gnome 2 interface, then you may consider going back to 10.04 or even Debian 6. I recently installed Debian 6 on a Pentium Dual Core laptop with Intel Video and it runs beautifully. It is harder to install then Ubuntu, but once you have it set, it will be supported for another 3 years at least. If you don't want to mess with Debian, you also have 2 years support left on Ubuntu 10.04.

I know that changing the distro is the easy way out of a situation and fixing the issues on your current install is the right way to go, however, there is nothing else that I can offer. Maybe somebody else will know more and have more luck helping you.

Sorry and good luck!

---

### Post by stinkeye on 2011-11-04
One last thing.
Remove the force unity line you added before.
```
gksudo gedit /etc/environment
```

You may have to settle with using metacity as your window manager.

---

### Post by yoramdavid on 2011-11-04
> **3Miro said:**
> I am sorry yoramdavid, at this point I am out of ideas. I will not be able to help you any further.

If 11.10 is giving you hard times and if you prefer the old Gnome 2 interface, then you may consider going back to 10.04 or even Debian 6. I recently installed Debian 6 on a Pentium Dual Core laptop with Intel Video and it runs beautifully. It is harder to install then Ubuntu, but once you have it set, it will be supported for another 3 years at least. If you don't want to mess with Debian, you also have 2 years support left on Ubuntu 10.04.

I know that changing the distro is the easy way out of a situation and fixing the issues on your current install is the right way to go, however, there is nothing else that I can offer. Maybe somebody else will know more and have more luck helping you.

Sorry and good luck!

That is ok, thank you very much for your time and help.

In 10.04 I had other problems that this distribution solved, so I am going to stay as it is for now, at least it works...

I am about to leave the country so I will leave it dormant for a while ;)

---

### Post by yoramdavid on 2011-11-04
> **stinkeye said:**
> One last thing.
Remove the force unity line you added before.
```
gksudo gedit /etc/environment
```

You may have to settle with using metacity as your window manager.

I went to remove that line and it was not there anymore, I must have removed it when it did not work. So I put it back (one more attempt), disable "metacity --replace" from the startup, loaded fusion icon, changed to metacity window manager, then back to compiz window manager and the screen appeared all distorted now. Then I tried something I had tried before having the ubuntu-deskotp installed, which is selecting the "Compiz Option / Indirect Rendering" Option under the fusion icon. And it works ! :p

What is that Indirect rendering option about?
Only one things that do not work: my screenlets do not appear on the desktop when I login, it does with metacity.

Another thing I notice as I write this text, sometimes I see gaps in the text that are not there which disappear when I scroll up or down, is that because of this indirect rendering?

Also I have to find a way to have compiz to load at startup, it does not. I have to go and reload the window manager from the fusin icon.

I also tried to run "compiz --replace" and the desktop froze as before.
After rebooting, I got no top menu on windows. Only after I launch compiz again.

Thank you.

---

### Post by yoramdavid on 2011-11-04
Now I cannot get to my desktop any more, I have fusion-icon starting with the system, and I unchecked the option "Indirect Rendering" and now even rebooting in gnome classic (no effects) I have an empty desktop.

Ok, I got it back using the recovery console login, then typing gnome-panel to get the menu and from there it was easy.

---

### Post by stinkeye on 2011-11-04
Try 
```
fusion-icon -n 
```
as the startup command so it doesn't reload the window manager.

---

### Post by yoramdavid on 2011-11-04
> **yoramdavid said:**
> Now I cannot get to my desktop any more, I have fusion-icon starting with the system, and I unchecked the option "Indirect Rendering" and now even rebooting in gnome classic (no effects) I have an empty desktop.

Ok, I got it back using the recovery console login, then typing gnome-panel to get the menu and from there it was easy.

It is fine now with "Indirect Rendering" checked.
Thank you

---

### Post by yoramdavid on 2011-11-07
It is not working fully well, but since I manage to run compiz, I will mark this as solved.

---

