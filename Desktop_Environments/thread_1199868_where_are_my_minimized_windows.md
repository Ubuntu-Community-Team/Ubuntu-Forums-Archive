---
title: "where are my minimized windows?"
date: 2009-06-29
forum: Desktop Environments
---

### Post by pooja on 2009-06-29
Yesterday when I used to minimize Firefox windows they would go down to the dock (avant window dock). Today when I minimize any window they're just disappearing from my sight, I can't see them but I know they are running in the background. I was watching a video but then I minimized it and I just couldn't get it back, it disappeared from my sight, it wasn't even in the dock, yet I could hear the sounds of the video. What's happening? Did I mess up something with Compiz? I did experiment a lot by enabling and disabling many options/effects from the Compiz manager under System > Preferences. Can you please help me? I'm new to Ubuntu, just installed it 2 days ago.

---

### Post by Idefix82 on 2009-06-29
Have you got an icon on the AWM dock for launching firefox? If you do then you might have triggered a setting by which running firefox windows (and other programs for which there is a launcher in the dock) are not displayed separately in the dock but instead the launcher gets a marker to indicate that they are running. To get them into the foreground, you can then click on the launcher.

Of course, you can always shuffle between the running programs by holding down Alt and pressing Tab, like under Windows.

---

### Post by Spike1158 on 2009-06-29
Well I can't help you with with fixing it in the dock, definitely not familiar with those, but if you still have a Panel on you're desktop, you can add a Window list to that for now until someone can help you with you're problem. 
Right click the Panel, click add to panel, then find "Window List", should be toward the bottom..hope that helps for now at least.

---

### Post by pooja on 2009-06-29
[QUOTE=Idefix83]Have you got an icon on the AWM dock for launching firefox?[/QUOTE]
No I don't have any firefox icon on AW dock.
Besides an error message popped up saying the screen was not composited and aw manager was mentioned. I didn't know what to do so I decided to close Avant Windows manager and from System > Preferences > Appearence disabled any special effects by returning to *Normal* mode.
I restarted the whole system and as soon as the desktop appeared all the missing windows appeared too. I don't know where do they disappear once a minimize them, I can't see them anymore. 

It's not only a Mozilla firefox windows' problem, it's about any window.

Thank you for telling me that <ALT> + <TAB> can help me get back at them but I really need to see them on the lower panel or on the awn dock. I have now closed down Avant Windows Manager and have kept 'None' as Visual Effect under System > Preferences > Appearance.

From a terminal I ran a check on Compiz. 
(myName stands for my name, as the Administrator of my PC)

```
myName@Ubuntu-LAPTOP:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by pooja on 2009-06-29
> **Spike1158 said:**
> Well I can't help you with with fixing it in the dock, definitely not familiar with those, but if you still have a Panel on you're desktop, you can add a Window list to that for now until someone can help you with you're problem. 
Right click the Panel, click add to panel, then find "Window List", should be toward the bottom..hope that helps for now at least.

Thanks, that was very useful! At least for the time being....

---

### Post by Greyfox_75 on 2009-06-29
"Besides an error message popped up saying the screen was not composited and aw manager was mentioned."

aw manager must require that you have compositing enabled. Did you get updates sometime before you restarted?  Possibly a video driver update broke your compositing, therefore causing your problem.  What kind of gfx card do you have?

---

### Post by pooja on 2009-06-30
> **Greyfox_75 said:**
> What kind of gfx card do you have?

You mean graphics card? Nvidia GeForce. But I thought I enabled it right at the very beginning, when I first ran Ubuntu from my hard disk.

---

### Post by pooja on 2009-07-06
I think the problem is all about adding an applet called "Launcher/Taskmanager" to the AW dock. If that applet is missing from the dock, whenever you minimize a window AND you don't have a panel at the bottom of your desktop, they just disappear nowhere. Unless you create a panel with "Window List" applet (*right click on the panel, choose [FONT="Courier New"]Add to Panel[/FONT], find the applet*) or you press ALT+TAB you won't get those windows back.

---

### Post by GO%)$@*1 on 2009-07-29
Hello!

I've been having this problem too. None of my applications are minimizing to the dock. Not even an icon showing that the application is even running. Weird. Never had this before. I've also been getting a "screen not composited" while it's shutting down. It did a system beep every time, and it was driving me nuts. I have a Dell Inspiron 6400/E1505 128mb ATI X1300 Video WF147 for graphics.

---

### Post by GO%)$@*1 on 2009-07-29
OK I tried to run compiz and I got

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/user/.compiz/session/1022fc3bc72945c48e124891710599058000000031830003"
```and also got a "screen not composited".

---

### Post by GO%)$@*1 on 2009-07-29
Your solution worked for me too! I didn't read the posts until after I posted just the title. Well, It works now! Thanks!

---

