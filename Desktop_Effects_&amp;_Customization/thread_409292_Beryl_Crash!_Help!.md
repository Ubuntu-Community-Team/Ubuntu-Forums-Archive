---
title: "Beryl Crash! Help!"
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by Ankher on 2007-04-14
Okay, I've installed A) the driver for my nVidia card, and B) Beryl. When I clicked on the red gem thing by the time that allows you to change options and stuff I discovered that some of the boxes are unchecked. So I check both of them. My system hangs. So I turn the power off and back on (really stupid, I know, but hey, what else am I supposed to do? (don't answer that please)) and when I reload Ubuntu, I get to the login screen, I login and then the GNOME loader thing pops up, everything loads and it goes away. So far so good. then the bars at the top and bottom of the screen, that become the system tray and whatever else it's called (sorry, don't know what else to call it) and then they go away. So I'm left with just a tan screen. I wait for a bit, but then I switch to one of the other terminal things and figure out how to shut down the computer.

What I'm wondering is: is there a way to get either A) beryl-manager off of the Gnome loading list from within the terminal, or B) beryl-manager to load right? :confused:  Thanks in advance!

P.S. once that's fixed, I have a smaller issue: my monitor goes up to 1280x1024 and it did this automatically when I was running onboard graphics. Now that I have the driver, it only goes to 1024x768, is there a way to change this?

---

### Post by dreadlord_chris on 2007-04-14
from the terminal:
```

sudo killall beryl

```

This will turn beryl off - but leave beryl-manager running. This will allow you to reset the Window Manager to Metacity in the beryl-manager - right-click the ruby > select Window Manager > Metacity. It might also be a good idea for you to select Launch Fallback Window Manager if beryl crashes.

---

### Post by ruibuntu on 2007-04-14
You have t edit your xorg.conf file ay /etc/X11.

Go to the Screen section and add 1280x1024

---

### Post by Ankher on 2007-04-14
ruibuntu: thanks! It worked great!

Okay, I uninstalled and installed Beryl again. So far so good. But now I have a bigger problem. At first I can't get any of the effects to display. So I go to the terminal and type ```
sudo beryl
``` which removes all the borders on my windows and produces this output: ```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!
``` Help!

---

### Post by serialdae on 2007-04-14
do you have Option "AddARGBGLXVisuals" "True" in your Section Screen of your xorg.conf

---

### Post by Ankher on 2007-04-14
uhh... no. There isn't an option for it?

---

### Post by omgitsruss on 2007-04-14
The 'nvidia' driver doesn't support GLX_EXT_texture_from_pixmap yet, so don't worry too much about that.

I'm no expert here so somebody chime in if I'm talking out of my ***... But are you running Xorg in a 24-bit resolution?
Do...

```
gksu gedit /etc/X11/xorg.conf
```

Browse down to 'Section "Screen"'
There should be an entry just underneath saying 'DefaultDepth' - Is that set to 24? If it isn't, change it to 24, save the file, and restart X (Ctrl-Alt-Backspace).

---

### Post by Ankher on 2007-04-14
It's on 24. I changed xorg.conf earlier by adding ```
"1280x1024" 
``` to anything that had screen resolution (like 1024x768 or 800x600) options. Would this wreck anything? (I didn't touch the rest of the file)

Actually, when I run ```
sudo beryl
``` it gives the output, and then beryl starts running. When I exit the terminal, though, all my window borders disappear. if I run ```
beryl
``` it gets as far as "No GLX_EXT_texture_from_pixmap" and then the system hangs and I have to turn the power off to turn the computer off. Does this help?

---

### Post by omgitsruss on 2007-04-14
I doubt it. 
I'm afraid that I'm a bit stumped. Have you got 'Modes "1280x1024"' listed under 'Depth 24' in your xorg.conf?

I had a similar problem which resulted in my system completely hanging - This was resolved by turning off the 'blur' effect in beryl-settings, then starting beryl. This is the only other thing I can suggest.

---

### Post by serialdae on 2007-04-14
> **serialdae said:**
> do you have Option "AddARGBGLXVisuals" "True" in your Section Screen of your xorg.conf

If that is n ot in there then add it and restart x

---

### Post by Ankher on 2007-04-16
> **omgitsruss said:**
> I doubt it. 
I'm afraid that I'm a bit stumped. Have you got 'Modes "1280x1024"' listed under 'Depth 24' in your xorg.conf?

I had a similar problem which resulted in my system completely hanging - This was resolved by turning off the 'blur' effect in beryl-settings, then starting beryl. This is the only other thing I can suggest.

Yes I do. Should I? ('cause it's got the other screen resolutions there too, so I thought, it must go there too.

Okay, I'm gonna try adding that option

*trys*

Okay, I added it and after a TON of screwing around (killing and restarting beryl and beryl-manager and reloading window decorators) Beryl appears to be running fine! Now to close out of the terminal

*crosses fingers*

YAY! I think it's working now!

---

