---
title: "Accessing the Gnome startup script/Creating a custom command"
date: 2011-07-21
forum: Desktop Environments
---

### Post by user:hackIt on 2011-07-21
I found a script I can use to enable my netbook touchpad with two finger scrolling/zooming in Ubuntu 10.04 Lucid Lynx. The site I found this code on suggested putting it in the startup programs in System -> Preferences -> Startup Applications. Only problem is, that you need a globally recognized command that the startup manager will call to start up your program. I can't put in a command line to execute a shell script.

So, "./2fsrl" or "./home/[USER NAME]/2fsrl" won't work. And, it's not for lacking the "sudo". I don't need to use that to execute this script.

Looking at the entries for the other startup programs, I see commands that call the program's executable. For example, for my Bluetooth Manager, the command is "bluetooth-applet."

So, I either need to find a way to create my own commands--I guess I would need to be able to create an executable for that--or I need to be able to edit the startup script that GNOME uses so I can add my code or call my shell script from there.

Unfortunately, I have not been able to find the startup script. I have done some browsing online, but no luck. Everybody seems to use the GUI application for this task.

Any help would be appreciated.

---

### Post by papibe on 2011-07-22
Make sure the script has execution permissions:
```
$ chmod a+x ./2fsrl
```
Then, in Startup Applications use the absolute path to the script:
```
/home/youruser/2fsrl
```
Note that an absolute path start with a '/' not a '.'

Hope it helps.
Regards.

---

### Post by user:hackIt on 2011-07-22
Yeah, I'm afraid I have already done that.

No difference.

And, I did not think that the "." is what you use to begin an absolute path. I was trying to execute the script at that path. I realize now that you don't even need the dot to execute it. The script is an executable when the properties have been changed with 'chmod'.

---

### Post by doas777 on 2011-07-22
do you have a bangline at the top of your script?
```
#!/bin/bash
....script contents......

```I believe you could also start your script from  /etc/gdm/Init/Default to start it with gdm instead of at login.put the code just above the Exit line at the bottom.```

if [ -x /path/to/script ]; then
   /path/to/script 
fi

Exit

```

---

### Post by user:hackIt on 2011-07-22
Okay, tried both of those suggestions, doas777. Still no result. 

Does it make a difference that I have Ubuntu configured to boot into the terminal first? And, then, I start Gnome with "startx" at my own discretion. (By the way, this was lifesaver when I put a troublesome command in the Startup Applications manager for this script. It wouldn't boot into Gnome until I removed it.)

---

### Post by doas777 on 2011-07-22
well, in that case I would definitely choose boot time mounting, so you don't need to rely on any particular DE to get access to the files. 

is there a particular step in the mounting process that you are having trouble with? what happens when you configure your fstab, and reboot? 

why don't you post your fstab, and we can look it over

---

### Post by papibe on 2011-07-23
Another thing you can try is to force your script to run as non-interactive script. Remove the bangline on your script and call it like this on your startup applications:
```
bash -c /home/youruser/2fsrl
```
Regards.

---

### Post by user:hackIt on 2011-07-23
papibe:  I tried your suggestion, but it's still not launching the script on startup.

doas777: I have the content of my fstab attached: textbox.txt.

It would be worth noting that whenever I jump out of X windows into one of the tty's, I have to rerun the touchpad script when I go back into Gnome. Also, if I run '2fsrl' from one of the tty's, I get this response: 

"Failed to connect to the X Server."

So, I don't believe I would be able run this script on bootup of terminal Linux. 

Not sure what kind mounting problems I am having that you are referring to, doas777. I wasn't able to start Gnome before, but I fixed that problem.

For clarity's sake, here is what I have inside the touchpad script (excluding the bangline):

synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=8
synclient EmulateTwoFingerMinZ=54

---

### Post by doas777 on 2011-07-24
> **user:hackIt said:**
> 
doas777: I have the content of my fstab attached: textbox.txt.


I owe you an apology; that post belonged in another thread I was in last night. I was somewhat suprised to find it wasn't in that thread today... now I know why.
I have no reason to believe that the fstab has any relationship to your issue, so sorry about that.

anyway, it is odd that you would have to reapply the script when toggling to Ctrl + Alt + F1 and then back to Ctrl + Alt + F7. but then again, it kinda makes sense. the system uses different drivers for tty's, so whenever the hardware profile changes, the script need to be applied over the defaults. that does imply that there should be an event that can be hooked to run your script, but I have no idea which one. 

Here is a list of gnome events you can trigger a script off:
[http://library.gnome.org/admin/gdm/stable/configuration.html.en#scripting](http://library.gnome.org/admin/gdm/stable/configuration.html.en#scripting)

try adding your script to XSession or Init and see if it fires when you switch between ttys and back to gnome. make sure your script is above the 'return 0' line.

---

### Post by user:hackIt on 2011-07-24
Is the X Session something that starts up whenever you go back into the Gnome screen (Ctrl + Alt + 7)? Maybe that's why it says "Cannot connect to X Server" whenever I try and run the script in one of the tty's. How is the X Server related to the X Session?

I tried putting the touchpad script's contents, or a call to that script, in the Init Default, the PreSession Default, and the PostLogin Default. I also have one in the Xsession script in /etc/gdm. I did not put anything in the PostSession Default because that looks like it is only called when Gnome exits.

Still no results.

---

### Post by doas777 on 2011-07-25
> **user:hackIt said:**
> Is the X Session something that starts up whenever you go back into the Gnome screen (Ctrl + Alt + 7)? Maybe that's why it says "Cannot connect to X Server" whenever I try and run the script in one of the tty's. How is the X Server related to the X Session?

I tried putting the touchpad script's contents, or a call to that script, in the Init Default, the PreSession Default, and the PostLogin Default. I also have one in the Xsession script in /etc/gdm. I did not put anything in the PostSession Default because that looks like it is only called when Gnome exits.

Still no results.

that sucks.

the reason you are getting that message in your tty1, is because there is no XServer running on that tty, so its like trying to run a windows program in dos.

I was hoping one of those everts woudl do it. I don't really know where to point you from here.

---

