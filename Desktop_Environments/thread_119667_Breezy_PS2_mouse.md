---
title: "Breezy PS/2 mouse"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ubuntu irv on 2006-01-20
How can I get my PS/2 mouse to work (MS coreless wheel mouse), and make the touchpad on my laptop inoperative?

I am using a compaq Presario 1685.  I have tried 3 different PS/2 mouses and none will work.  They do nothing.

---

### Post by Ocxic on 2006-01-20
i think it has somthing to do with the xorg.conf file, pointing to the device you want to use. I'm not sure how to go about configuring it in that way, but at least it may give you an idea.

---

### Post by ubuntu irv on 2006-01-20
Being a NEWBIE I think I need better information to make the changes and what changes??

---

### Post by southernman on 2006-01-20
[QUOTE=ubuntu irv]Being a NEWBIE I think I need better information to make the changes and what changes??[/QUOTE]Maybe so, but you gave VERY little info on your situation. Newbie is not defined as "the entitled one" - :p

The search function of this forum works as good, if not better than googles search engine.

---

### Post by slashem on 2006-01-20
Here are the relevant lines from my /etc/X11/xorg.conf :

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

YMMV

---

### Post by Urmas on 2006-01-20
Hi, Irv! I found this solution from the Finnish Ubuntu Forum. I don't use a laptop, so I haven't tried it myself. The feedback is positive, though.

1. This works only if you have a Synaptics touchpad. So: in Terminal:
```
 sudo gedit /etc/X11/xorg.conf
```

If you can find the following lines, you have the Synaptics driver in use. If not, don't bother reading on:
```
Section "InputDevice"
Identifier"Synaptics Touchpad"
Driver"synaptics"
Option"SendCoreEvents""true"
Option"Device""/dev/psaux"
...
```

Assuming that you had the Synaptics driver in use, we boldly proceed:

2. Add the following lines between the last Option"Device"... and EndSection:
```
               ...
Option"TouchpadOff""1"# Touchpadin oletusasetus (päällä vai pois X:n käynnistyessä)
Option"SHMConfig""on"# Sallii touchpadin asetusten muokkamisen X:n ollessa päällä)
EndSection
```
(Yeah... Finnish! :p )

3. Save and close the file; don't close the editor just yet. Open a "New" file. Copy/Paste the following in there:
```
#! /bin/bash
#
#  touchpad
#  This script either enables or disables Synaptics touchpad
#  thanks to littleLion =)
#
#  Mikko Saarinen - 15.9.2005
#

#  view 'man synclient' for more info

synclient -l | grep TouchpadOff | grep 1 > /dev/null

#  if last command succeeded, then Touchpad is deactivated

if [ $? -eq 0 ]             # test exit status of grep 1
then
  synclient TouchpadOff=0   # activate touchpad
else
  synclient TouchpadOff=1   # deactivate touchpad
fi

exit 0                      # exit script with success status
```

Save the file as **/usr/bin/touchpad** and close the editor.

4. Next, you'll have to make the new /usr/bin/touchpad file executable. In Terminal:
```
sudo chmod 755 /usr/bin/touchpad
```

Now, every time you open the Terminal and write "touchpad", it toggles the touchpad on/off.

5. If you don't like using the terminal for this all the time, you can create a "hotkey" for it:
- Applications -> System Tools -> GConf Editor (or whatever it's called... car-with-open hood icon).
- From the left window:
apps -> metacity -> keybinding_commands
- From the right window, choose: command_1 (or if it's "taken", choose the first "free" number). Right-click it.
- Choose "Edit Key" (or whatever... I'm using the Finnish version) and for "Value", write **/usr/bin/touchpad**. Click "OK".
- From the left window, choose "global_keybindings".
- From the right window, choose "run_command_1" (or  _2 or whatever you are using). Right-click it.
- Choose "Edit Key(?)", and, as "Value", write the key combination you want to use for this, for example **<Ctrl><Alt>M**. Click "OK".

That's it! Hope this works for you.

---

### Post by ubuntu irv on 2006-01-20
I followed your instructions as given.
I rebooted the machine and got a message that it "Failed to start the X server".  I login and am sitting at:

irv@ubuntuirv:~$

Do not want to touch anything until you get back to me..
Thanks

Irv

---

### Post by ubuntu irv on 2006-01-20
[QUOTE=southernman]Maybe so, but you gave VERY little info on your situation. Newbie is not defined as "the entitled one" - :p

The search function of this forum works as good, if not better than googles search engine.[/QUOTE]
"How can I get my PS/2 mouse to work (MS coreless wheel mouse), and make the touchpad on my laptop inoperative?
I am using a compaq Presario 1685. I have tried 3 different PS/2 mouses and none will work. They do nothing."

You need to read my posts before you answer like that....I think I was very clear on what the problem was.
Irv

---

### Post by carlosqueso on 2006-01-20
[QUOTE=ubuntu irv]I followed your instructions as given.
I rebooted the machine and got a message that it "Failed to start the X server".  I login and am sitting at:

irv@ubuntuirv:~$

Do not want to touch anything until you get back to me..
Thanks

Irv[/QUOTE]


You should probably type ```
sudo nano /etc/X11/xorg.conf
``` and take out the lines that you added.  Then save and exit, and type startx.  It should work then, but your problem with diabling the touchpad still exists.

---

### Post by ubuntu irv on 2006-01-20
Came back saying that 
X10: fatal IO error 104 (Cnnectio resetby peer) on X server "0.0" after 0 requests.
xauth: error in locking authority file /home/irv/ .Xauthority

I typed in sudo dpkg-recovery -phigh xserver-xorg
then startx
I am now back at the desktop.

Thanks

Irv

---

### Post by ubuntu irv on 2006-01-20
Anyone else got any idea's on this problem:

How can I get my PS/2 mouse to work (MS coreless wheel mouse), and make the touchpad on my laptop inoperative?

I am using a compaq Presario 1685. I have tried 3 different PS/2mouses and none will work. They do nothing.

Irv

---

### Post by Edward The Bonobo on 2006-01-20
At the same time...can anyone tell me how to get my serial mouse working in Breezy?

I had the same problem in Hoary and followed the instructions from the wiki [https://wiku.ubuntu.com/SerialMouseHowto](https://wiku.ubuntu.com/SerialMouseHowto)

But the same won't work in Breezy.  I'm not given a choice for mouse.  Also...when I try gedit on xorg.conf I'm getting 'Cannot open display'

---

