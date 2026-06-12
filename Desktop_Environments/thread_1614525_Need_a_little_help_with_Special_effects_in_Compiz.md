---
title: "Need a little help with Special effects in Compiz"
date: 2010-11-05
forum: Desktop Environments
---

### Post by irv on 2010-11-05
I was able to rotate the desktop cube in Compiz by holding the Ctrl/Alt/arrow keys, but now all I can do is this: see screen shot. How can I get the cube rotation back? 
I don't know what changed?
[ATTACH]174691[/ATTACH]

---

### Post by 3Miro on 2010-11-05
You need to install either Simple Compiz Settings and/or CCSM (search for CCSM in the software center). CCSM is more advanced and has more options, SCS is easier to use. Then you can set whatever cube/wall effects you want with corresponding shortcuts. For the cube, in CCSM you need to enable 3D cube, Rotate Cube and from inside the Rotate Cube sub-menu, you can set the binding for "initiate".

---

### Post by janf on 2010-11-05
Hi -

It appears that your keyboard shortcuts have gotten changed.  Your screenshot is actually the Unfold Cube command (Ctrl-Alt-Down arrow).

I'm not sure what you have installed, so I'll start at the beginning.

Start Synaptic, and type "compiz" in the Search window.  When Search is complete, click on compiz-settings-manager, and click on Mark for Installation. Click Apply at the top of the Synaptic window to complete the installation.  Close Synaptic.

On the menus, go to the System menu, Preferences, and click on CompizConfig Settings Manager.  When it opens up, scroll down to the Desktop section, where the Desktop Cube stuff is. 

Check Desktop Cube and Rotate Desktop Cube.  Others in the section are optional.

Double-click Rotate Desktop Cube to open it. Click on the Bindings tab, then click on Rotate Cube to expand its menu.

Here you will find the keyboard and mouse bindings. Make sure that the keyboard Rotate Left is set to <Control><Alt>Left, and keyboard Rotate Right is set to <Control><Alt>Right. Click the Back button on the left od the window to go back to the main settings window.  Settings are immediate, so you should be able to test the keyboard commands without exiting CompizConfig Settings Manager.

While you are in CompizConfig Settings Manager, I'll suggest a setting that you may find convenient if you have a mouse with a scroll wheel.

Still in the Desktop section, check Viewport Switcher to enable it.  Click it to open the settings section, then click on the Desktop-based Viewport Switching tab.

These are all mouse settings.  Go to the Move Next setting and click on the Disabled button to change the setting.  When the small window opens, check Enabled to allow settings to be made.  When the Edit Move Next window opens, click on the "Button1" dropdown and select Button5.  Click OK to keep the setting.  Back at the Desktop-based Viewport Switching screen, click on the Move Prev setting. Again, check Enable in the small window to get the Edit Move Prev window.  Click on the "Button1" dropdown and select Button4.  Click OK to keep the setting.

This will allow you to switch desktops by rotating the mouse wheel.  It works when you place the cursor over the desktop.  When you place the cursor over an open window, such as a Web browser, the scroll wheel behaves normally and scrolls the window.

Hope this helps.

---

### Post by irv on 2010-11-06
I already have CCSM installed, and I have not changed any of the binding (short cut keys). I am using Ambiance theme with custom icons, but that shouldn't make a difference. Here are a couple of screen shots of my settings.
[ATTACH]174749[/ATTACH]   [ATTACH]174750[/ATTACH]

---

### Post by irv on 2010-11-06
I will mark this solved because I have it working now.
The Rotate cube Initiate shortcut got changed. It was set to <Control><Alt><Button2 and Not Button1> when I changed it back it began to work again. I don't know how it got changed because I did not change it.
Thank you all for the help here.

---

