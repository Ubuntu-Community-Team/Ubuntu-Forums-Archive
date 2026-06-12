---
title: "Where can I find hotkeys &amp; compiz question"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by XNYE on 2007-10-22
I'm a complete new person to linux... I probably spent 60-80 minutes googling/reading trying to find out where/what the hot keys are.

I've been searching for the expo and scale hot keys but haven't been able to find them.

Also I've been reading about some compiz-manager that I need to install but I cannot find it in the synaptic package manager.  

Also,  just now typing in firefox... it has scrolled down automatically... it seems to be glitchy.  Is there something to fix this?  It also will the "left-click toolbar."

Thanks

---

### Post by RomeReactor on 2007-10-22
Hi. The expo plugin is activated by pressing SUPER+E ("super" is the windows logo key); note that you can choose which workspace to activate by pressing either the LEFT or RIGHT arrows, and then pressing enter, or by hovering your mouse pointer over the desired workspace and **right-click** (not left-click).

The scale plugin is activated with SHIFT+ALT+UP (the up arrow on the keyboard).

You can install **compizconfig-settings-manager** to enable and/or disable other effects; look for it in Synaptic (System->Administration->Synaptic), or to install from the terminal (Applications->Accessories->Terminal):
```
sudo apt-get install compizconfig-settings-manager
```
Once it's installed, you can find it in "System->Preferences->Advanced Desktop Effects Settings"; or, open "System->Preferences->Appearance->Visual Effects tab", select "Custom" and press "Preferences".

As for your Firefox problem, probably someone else can comment on that. And welcome to the forums!

---

### Post by Lord_Dicranius on 2007-10-22
> Also, just now typing in firefox... it has scrolled down automatically...
First thing that comes to mind is that you're using a laptop and your hand touched the touchpad causing it to scroll down :confused:

---

### Post by XNYE on 2007-10-22
> **Lord_Dicranius said:**
> First thing that comes to mind is that you're using a laptop and your hand touched the touchpad causing it to scroll down :confused:

I am using a laptop but I am not touching the pad.  I wish that was it.  

I'll randomly scroll and go off of my current focus in the window.



[QUOTE=RomeReactor] Hi. The expo plugin is activated by pressing SUPER+E ("super" is the windows logo key); note that you can choose which workspace to activate by pressing either the LEFT or RIGHT arrows, and then pressing enter, or by hovering your mouse pointer over the desired workspace and right-click (not left-click).

The scale plugin is activated with SHIFT+ALT+UP (the up arrow on the keyboard).

You can install compizconfig-settings-manager to enable and/or disable other effects; look for it in Synaptic (System->Administration->Synaptic), or to install from the terminal (Applications->Accessories->Terminal):
Code:

sudo apt-get install compizconfig-settings-manager

Once it's installed, you can find it in "System->Preferences->Advanced Desktop Effects Settings"; or, open "System->Preferences->Appearance->Visual Effects tab", select "Custom" and press "Preferences".

As for your Firefox problem, probably someone else can comment on that. And welcome to the forums[/QUOTE]

I tried the sudo apt-get install yesterday and it wouldn't work but for some reason it did today.  Maybe because I rebooted?  But I've got everything straightened out with the compizconfig settings manager.  Thanks.

How am I to find the specific key commands to do any specific effect? I can't find where it tells the shortcut keys in the compizconfig settings manager.  ig.  How do I do the cube thingy, the exp, scale.. Are there a list of shortcut keys somewhere?

Also, off topic because I don't want to spam the forums with my questions and hopefully someone can help.  What does it mean and how do I become root.  Some previous things I've tried to install that wanted me to be in root where the nvidia drivers but somehow I got that working without being in root... at least I think it's working.  Today I tried installing aim-1.5.234-1.i386.tgz and it told me I needed to be root.  Or something of the sort.  Things I've tried: rebooting, pressing esc, pressing 'c' to go to the command prompt.  From there I typed in the password.  (The password I set by right clicking my user name when I'm logged in;edited user and groups; double clicked the root under the name column; made a password)  I couldn't do anything with the small amount of linux commands that I some-what know.  I've tried to log in as root and with the password I created but it says "The system admin is not allowed to log in from this screen."  

I guess my main question point from all that is, "do I have to install everything as root?"

Thanks

---

### Post by Lord_Dicranius on 2007-10-22
For the root stuff, that's what the "sudo" is.  SU stands for "super user" so basically "sudo" is saying "super user, do this".  And as for the question if you have to be root to install everything: for the most part yes.  Most installs need to put files in locations that your regular user account cannot access and needs root access.

---

### Post by RomeReactor on 2007-10-22
To add to what Lord_Dicranius said, on most other Linux distros, a root user has full access to the system, and can install and remove programs, and create or delete files anywhere. In Ubuntu, this user is disabled by default, and instead we use **sudo** for tasks that require administrator rights (root). There is a way to log in as root, but it is highly recommended you don't do that, especially when trying Linux for the firs time, as you can very easily erase a system library that could render your system useless. This may sound ominous, but is something that can happen--and has.

As for figuring out the key bindings to the plugins, in CompizConfig press on the desired plugin, and go to the "Actions" tab.

---

### Post by XNYE on 2007-10-22
> **RomeReactor said:**
> To add to what Lord_Dicranius said, on most other Linux distros, a root user has full access to the system, and can install and remove programs, and create or delete files anywhere. In Ubuntu, this user is disabled by default, and instead we use **sudo** for tasks that require administrator rights (root). There is a way to log in as root, but it is highly recommended you don't do that, especially when trying Linux for the firs time, as you can very easily erase a system library that could render your system useless. This may sound ominous, but is something that can happen--and has.

As for figuring out the key bindings to the plugins, in CompizConfig press on the desired plugin, and go to the "Actions" tab.

Thank you to the two above posters... every bit of information helps, especially when it's specific to my problems. :)

Say that I wanted to install AIM 1.5 that I found off the net. ( My dad informed me that I can just use pigon, which I will ) I downloaded it onto my desktop... so now I have a .tgz file... I think I followed the extract instructions and I now have a usr directory on the desktop.  I have no idea what to do with that... it does have a .exe in the bin and I recognize the usr directory.  I tried to move the .exe file to the  /user/bin/ dir via the gui folders but was denied because I don't have permissions. So my question is how come I cannot just drag and drop as I can in Windows?  Must I sudo mv 'cd to the dir' usr/bin/aim /usr/bin ? Or is that not the proper way to do things??

Thanks

EDI: I got the aim.exe file( I think it's an .exe file) in the /usr/bin/ dir but when I use the gui windows to execute it, it doesn't do anything.  How do I execute it via the gui window, and how do I execute it via the terminal??

---

### Post by RomeReactor on 2007-10-22
It's usually better to search in Add/Remove or Synaptic first for programs; if your desired package is not there, then maybe it can be found at [GetDeb]("http://www.getdeb.net/"). Having a .deb package (which you can double-click to install, as long as it's compatible with your version of Ubuntu) is convenient. If you can't find a .deb package, then you'll have to get a .tar package (like the one you have), or a .bin installer or .sh script.

For .tar.gz files, what you do with it depends on whether it contains source code (to be compiled) or a precompiled binary you can run. The included readme file will tell you what to do.

If it's source, you usually have to run three commands:
```
./configure
```
to create a makefile; you could also run ./configure with other parameters, which the readme file will likely inform you about, but most of the time you just run it without parameters. Then:

```
make
```
to prepare the files for installation, compile the binary files needed or recompile others; and lastly:

```
sudo make install
```
for the installation itself.

I don't really know much about compiling programs, so maybe there are errors in my description, but that's essentially what it does.

If the .tar.gz file contained precompiled binaries, then you run it from the terminal by first changing to the directory extracted:
```
cd /PATH/TO/DIRECTORY
```
and:
```
./NAME_OF_EXECUTABLE
```

**.exe** files are for windows. You *could* attempt to run them using a compatibility layer called Wine, but there's no guarantee they'll work. There are many Linux alternatives to windows programs.

Pidgin should work with the AIM protocol; give it a try. Where did you download the AIM .tar.gz from?

---

### Post by XNYE on 2007-10-22
Thanks, I'm going to sub to this thread for future reference.

I downloaded the app from:
[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

I'm not going to use it though.  Pidgin looks much better and is already installed.

Some hotkeys for others that might be looking.
> Ctrl+Alt+(left or right arrow)
Shift+alt+Uparrow
Crtl+Alt+DownArrow
of course Alt+Tab
Ctrl+Alt+Shift+(Left or Right arrow) to move current window to other workspace
Ctrl+Alt+LeftMouse button
Click Middle Mouse Button to move cube
Super+E
ctrl+alt+d fade all windows to desktop
alt+scroll make ur winow transparent
winkey+tab the itunes thing


And they can be found in the CCSM(CompizConfig Settings Manager)>select an effect>go to actions>collapse.

---

