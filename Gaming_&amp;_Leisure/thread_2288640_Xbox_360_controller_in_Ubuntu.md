---
title: "Xbox 360 controller in Ubuntu?"
date: 2015-07-28
forum: Gaming &amp; Leisure
---

### Post by dorlow on 2015-07-28
I recently bought a new laptop.  It came with Windows 8.1.  I loaded Steam and started playing games.  (I'm in IT and my whole career I never played games which most people find odd.  So I thought I'd try it out.)  Turns out I like playing video games.  I like this game Counter Strike Global Offensive and bought it.  But I don't like using windows so I formatted the laptop and put Ubuntu on it.  I loaded steam and was able to install the game into Ubuntu.  It works really nice except I can't get the xbox 360 wireless controller to work in Ubuntu.  I followed some instructions here.

[[COLOR=#1155cc][FONT=Arial]_[http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working](http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working)_[/FONT][/COLOR]]("http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working")

I got it kind of working.  I loaded the apps suggested via apt-get.

I then start the xbox software in a terminal via "sudo xboxdrv."  I hit buttons on the xbox controller and i see the commands in the terminal window.  I can open Steam and control steam using the controller.  But as soon as I go into Counter Strike, the controller does nothing.  Any ideas how to get it working?

---

### Post by hansooloo2 on 2015-08-07
I have not done this in a few years but I found some thing that may be able to help you. It seems all most the same with using 3rd party software to configure the controller. Is their a chance that you didn't configure it correctly or change your steam or game preferences. In the Github project his **README.MD** file gives you instructions on how to set up everything all so.

[https://github.com/x360ce/x360ce](https://github.com/x360ce/x360ce)
[URL="http://askubuntu.com/a/399662/435324"]http://askubuntu.com/a/399662/435324


[/URL]> 

This is an update to existing answers for a way to get an XBox360  controller working in Wine >= 1.7, including Steam games in Wine on  Ubuntu >= 13.10. No root permissions needed for installation and  operation.
  The below method makes use of **[x360ce.exe]("https://code.google.com/p/x360ce/downloads/list")**,  which basically provides Dinput codes for Wine to communicate with a  game (Note that your XBox controller still sends Xinput controls).


[LIST=1]
[*]Plug in your XBox360 (or compatible) controller to have it automatically recognized with the xpad kernel module.[QUOTE]*No need to install and run xboxdrv because at present the controller appears to be recognized. Do **not** blacklist the Xpad kernel module as was recommended in older tutorials.* 
[*]Download the ZIP archives for the [Windows (Wine) application x360ce]("https://github.com/x360ce/x360ce") and its accompanying .dll binaries for Xinput, and Dinput. 
[*]Extract the ZIP archives to copy their content with at least the following files to the game's executable directory (e.g. ```
~/.wine/drive_c/Programs/Games/game.exe
``` or ```
~/.wine/drive_c/Programs/Steam/SteamApps/common/Name_Of_Game/game.exe
```
    > ***some games may also need:***
[LIST]
[*]**x360ce.exe** 
[*]**dinput8.dll** 
[*]**xinput1_3.dll** 
[*]**xinput1_9.dll** 
[/LIST]
  
[*]Run **x360ce.exe** with Wine to create a sample **x360ce.ini** file in the game's directory if not yet present. 
[*]Quit **x360ce.exe** (you may have to kill Wine to do so as the application may hang) 
[*]Open the **x360ce.ini** file with an editor to add the following line to prevent future crashes or hangs:  ```
Version=1
``` 
[*]Start **x360ce.exe** again to recognize your XBox controller(s). 
[*]We may optionally choose from a premade setup file as soon as the controller was recognized. 
[*]Adjust buttons and joystick axes of your controller to appropriate values.[IMG]http://i.stack.imgur.com/VM1qA.png[/IMG] 
[*]Save saves these settings to the **xbox360ce.ini** file 
[*]Then quit (or kill) **x360ce.exe** 
[*]if needed open the **x360ce.ini** file in an editor again to fine tune some of the settings. 
[*]Your Windows game should now recognize the controller when started from Wine.> [INDENT]
[LIST]
[*][B]Do not unplug the controller, as it will then only be recognized after a restart of the game.
[/B] 
[*]**Backup the .ini file for future use to avoid re-calibration.** 
[/LIST]
[/INDENT]

  
[/LIST]

[/QUOTE]

[URL="http://askubuntu.com/a/399662/435324"]
[/URL]

---

### Post by efflandt on 2015-08-09
I am just curious if the default xpad driver did NOT work for you? I have a Logitech F710 wireless gamepad and as long as its switch is the right position to emulate an xbox controller, it worked out of the box in Linux Steam Big Picture mode and for Steam games. With the switch in the other position (rumblepad?) the controls are all mixed up. There was only one game under development that had a keyboard config gui, but not a controller gui, and I had to modify an gamepad.xml file for desired Dpad functions. But other than that my gamepad just worked out of the box without installing anything. I did install jstest-gtk just to see how Linux saw all the levers and switches.

If from Big Picture mode using a controller you start a game that is currently configured to use a keyboard/mouse, it should ask if you want to use the controller. But if you start the game from Steam Library you may need to set options in the game itself to use a controller.

But I have never had a game console and am a Quake player from way back, so ground combat with a controller is awkward for me and I use keyboard/mouse for that. But I have flown RC aircraft (and a real airplane once), so I use the controller for things that fly.

---

### Post by jim_deadlock on 2015-08-10
Try this: View > Big Picture Mode > Settings > Controller

Set/save your gamepad and it should then pass the proper settings to all the games in your library. You can restart Steam in normal display after this and the settings will stay. This worked for me for several games I was having gamepad trouble with (I'm using the standard xpad driver).

---

