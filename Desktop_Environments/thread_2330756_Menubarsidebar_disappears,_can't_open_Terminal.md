---
title: "Menubar/sidebar disappears, can't open Terminal"
date: 2016-07-14
forum: Desktop Environments
---

### Post by pol-d on 2016-07-14
Hi All,

I am trying to find answers to my problems in the forums, but have failed to do so. So, here are my problems with my Ubuntu/Linux machine:

Out of sudden, the VirtualBox icon disappeared from the side menubar, followed by the Terminal. Then, the whole menubar disappeared from the desktop screen. I tried to open the terminal using the Ctrl+Alt+T, but no response. Luckily, I have linked a folder on my desktop, so I can access my folder and files from there and potentially open the Firefox Web Browser. I am not sure how to fix this, but I think something has crashed. 

I have posted 2 images of the desktop screen showing to side menubar.

Anyway, I think the way to fix this is by using the Terminal. But the main problem is the Terminal cannot be opened at all. 

Oh please help me.

Thanks

---

### Post by MAFoElffen on 2016-07-14
So this is a host problem, not really associated with VirtualBox... except that it's icon disappears from the desktop, along with other things and functions?

You can always get to a console prompts via <Cntrl><Alt><F2> (using function keys 1-7, to get to different virtual consoles)... or to a terminal vai, click anywhere on your background, so the desktop is in focus, then <Cntrl><Alt><T>.

So lets get more details. What is this on, hardware and OS Flavor/Version?

Note that I may move your thread, if I feel it is more appropriate and would get better exposure for this in another section.

---

### Post by ajgreeny on 2016-07-14
Are the missing icons originally just those two from the launchbar on the left side of the unity desktop, followed by the complete launchbar disappearing?

I'm confused.

---

### Post by pol-d on 2016-07-14
Hi..

First of all, I am still a beginner to this Ubuntu/Linux...and mostly doing my data (genetic) analysis using the Terminal.

MAFoElffen, I agree that it is not associated with the VirtualBox. I just don't understand how the VB d suddenly isappear from the menu, followed by the Terminal, and then the whole launchbar on the left side and menubar on the top (FYI, ajgreeny). I can do right-click, open all files in the folder, and do usual work (such as internet browsing, LibreOffice etc). But I cannot save or close the windows since the top menu is gone, so the only way to do this is to apply Alt+F4.
 
I tried Ctrl+Alt+F2 or Ctrl+Alt+F1 and these gave me a blank screen. But, I am not sure what to do next. Again, I tried Ctrl+Alt+t so many times and it did't work.

My computer is on:
 ubuntu 14.04LTS
memory: 31.4GiB
 Processor: Intel Cire i7-4790 CPU @ 3.60GHz x 8
Graphic Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OS type: 64-bit
Disk: 950.6 GB
[URL="http://ubuntuforums.org/member.php?u=1044547"]
[/URL]Sometimes, this appear:

Sorry, Ubuntu 14.04 has experienced an internal error
ExecutablePath
  /usr/bin/unity-control-center
Package
  unity-control-center 14.04.3+14.04.20150915-0ubuntu1
ProblemType
  Crash
Title
  unity-control-center crashed with signal 5 in g_object_new_valis()
ApportVersion
  2.14.1-0ubuntu3.21
...etc etc

I am totally clueless here...

---

### Post by MAFoElffen on 2016-07-15
I first suspected either memory corruption or a problem with Compiz... but seems to be more with Unity itself.

We are right that it isn't a problem with VirtualBox, just that it's icon is round-about included in the disappearance of objects from your desktop. I'm going to move this to another section to get better exposure form you problem. But will still follow it for support.

---

### Post by MAFoElffen on 2016-07-16
No one here touched this and I said I would followup, so...

Click on the Desktop. <Cntrl><Alt><T>. A terminal window should appear.
```

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```
Tell me if that works things out in your install. I'll re-check this thread later to see how it went.

---

### Post by pol-d on 2016-07-20
Sorry, almost forgot my problem here.

The Terminal did not appear when clicked on the Desktop and applied Ctrl+Alt+T (as I have mentioned earlier). 
Is there other alternative to open the Terminal?

Thanks.

---

### Post by Frogs Hair on 2016-07-24
You could try the following from tty . Press Ctrl + Alt + F1 , login with user name and enter password. Enter the following commands one at a
time. 

```
sudo apt-get install dconf-tools
``````
 dconf reset -f /org/compiz/
``` ```
sudo reboot
```

---

### Post by smelheim85 on 2016-07-24
pol-d

When you press Alt+Ctrl+Fx(1-7) drops you into a terminal.  If your more familiar with Windows it's sorta like getting into the DOS prompt when the Graphical wasn't available.  You can ran the command suggested from MAFoElffen.  Frogs Hair also has good suggestions because it sounds like something was either turned off or corrupted and the controls for the graphical needs to be reset.  I should also mention when you get into this black window it should prompt you like normal and will only give you a command line to type into.  I haven't taken the time to run a spin of Ubuntu 16.04 so I don't know if compiz is even installed really.  But start by reinstalling Unity because that seems to be the problem.

---

### Post by middlechild2 on 2016-07-31
This thread is the closest to my issue as well. The launcher bar on the left is missing, the menu bar across the top as well.  I can open a terminal session by right click in any open desktop area and select from the menu.

I have two Ubuntu computers running 16.04. Both were upgrades from 15.10, both have all patches. 
The computer with the issue is a dual boot, Win10 and another difference is the graphics card present in this box.

The computer with the issue:
Dual boot - Win 10, Ubuntu 16.04
CPU: i5-4690
memory: 16GB
Graphics: NVIDIA GeForce GTX 960
Drive: 750GB 

Steps taken so far:
Ensure all latest patches up to date
Check all four edges, to verify the shortcuts have not moved
Reset desktop image to default
Installed dconf-tools, and reset - no change
Installed Ubuntu-Desktop - no change

Thanks in advance

---

### Post by P-I H on 2016-07-31
I also got this problem. It happened when I rebooted the computer and I don't know why.
I fixed it in the following way.
Started a terminal by right clicking the mouse and selected "Open terminal"

Then started CCSM with the command ccsm.
In CCSM I checked that the the following was ticked


In General: Commands, Composite, Copy to texture, OpenGL
In Accessibility: Enhanced Zoom Desktop
In Desktop: Desktop Wall, Expo, Viewport Switcher, clicked Ubuntu Unity Plugin and checked that it was enabled
In Effects: Animations, Fading Windows
In Image Loading: PNG
In Utility: Compiz Library Toolbox, Mouse position polling, Redex Matchning, Session Management, Workarounds
In Windows Management: Grid, Move Window, Place Window,Resize Window, Scale, Snapping Windows
In Uncategorized: Unity MT Grab Handles
I had to resolve some inconsistencies

Then I made these commands in the terminal
export DISPLAY=:0
sudo dconf reset -f /org/compiz/
setsid unity

After this the Laucher and the Upper panel came back.

---

### Post by middlechild2 on 2016-07-31
I will do these steps shortly, once I am back in front of the machine.
What is the process CCSM and how does it get corrupted?

Thanks in advance

---

### Post by P-I H on 2016-07-31
CCSM is a program used to set parameters for the unity dektop. In case it isn't installed you have to install it.
Use this command in the terminal
sudo apt-get install compizconfig-settings-manager

I don't know why, but it has happened one time earlier on this computer.

---

### Post by middlechild2 on 2016-08-03
I verified the compiz settings, after installing ccsm. 
The settings on the affected computer matched, no changes were required.
Several other observations:
1. When logging into the desktop account, the top bar was present showing power off, speakers, etc
2. Guest account had all menu / side bar as expected
3. System settings on the guest account all appeared normal
4. Back to user account, the menu bar and side bar were gone, inaccessible.
5. Back to user account the ALT key did nothing, no obvious response. Other keyboard shortcuts did not respond either, although ALT-F4 does close the window but ALT-TAB does not work.

Is there a keyboard shortcut to open display settings for a particular user account?

Thanks in advance

---

### Post by middlechild2 on 2016-08-06
Are there keyboard shortcuts, for disability access, in the desktop that I might have tweaked?  Such as a scroll button in a certain place magnifies the desktop, a right click in the corner changes font size, something?  
Something has changed, because this worked for the past year when i installed Windows 10 as a dual boot machine. 
Could the desktop have grown beyond the edges of the physical monitor, to where the mouse pointer cannot get to the trigger?
Could the width of the menu bars be changed, to where they are so narrow now they are inoperable?

How do I restore a desktop environment back to a default setting?

---

### Post by middlechild2 on 2016-08-06
The new value for the key binding for the action Prev window (All windows) in plugin Application Switcher conflicts with the action Key to switch to the previous window in the Switcher for all viewports of the Ubuntu Unity Plugin plugin.
Do you wish to disable Key to switch to the previous window in the Switcher for all viewports in the Ubuntu Unity Plugin plugin?

Researching to find why <ALT>-Tab doesn't work:  In CCSM, the switcher function was not checked. A list of settings appeared, and this warning appeared. I have not intentionally reassigned any key bindings, so not sure what the implication is here. How coudl this setting have changed? What is the "Prev window" key doing, and or any idea how it was changed from default?  Was there a patch released that changed some Unity settings?

---

### Post by middlechild2 on 2016-08-23
The issue remains.....
What bothers me is the lack of ability to grab the side edge of an application. Like the Firefox app running as I type this. It is full screen, and I have no way to shrink it down. Almost like the desktop is larger than the monitor and the cursor cannot escape the edge of the monitor to get to the edge.

---

### Post by middlechild2 on 2016-08-23
Tonight I ran apt-get update, and there were over 100 packages to install.  Obviously at some point something became corrupted.  Now I run update quite often, and I am sure I had done so since the problem first appeared. Anyway, the problem now appears fixed. The menu / task bar is back.

Thanks...  
-- Middle

---

