---
title: "Steam games &quot;preparing to launch&quot; then nothing"
date: 2013-04-02
forum: Gaming &amp; Leisure
---

### Post by Ritlengo on 2013-04-02
Hi!
Just installed ubuntu on my MSI GX740 and I've got all the drivers,
and when i try to launch any games from steam.
It looks like it's launched for about a second then turned of again and there no error message

---

### Post by myromance123 on 2013-04-02
What drivers do you have exactly?

I checked that laptop's specs, and it's a Hybrid graphics system. AMD + Intel Integrated. A HD5870 with an Intel i5 graphics. Do you have the AMD proprietary drivers installed, or do you have the Open-Source Intel drivers being used instead?

To me, it looks like what you have is the Intel Open Source drivers in action here. It'd help us help you, if you could list down the games you're trying to run from Steam. Also what driver version and type (e.g OSS or Proprietary) you have installed yourself (if any), and what version of Ubuntu you are using (e.g. Ubuntu 12.04 or 12.10 or 13.04, and whether or not they are 32Bit or 64Bit).

---

### Post by Ritlengo on 2013-04-02
[HR][/HR]I've got AMD catalyst center and it has identified my graphics card. I  installed some third party drivers aswell but can't seem to find the  versions on them.
The Ubuntu version is 12.10 32 bit and the games I've tried to run is Team Fortress 2 and Psychonauts

---

### Post by myromance123 on 2013-04-02
Can you go into detail on how you installed the AMD drivers?

Was it through Additional Drivers in Ubuntu, or did you download the drivers from AMD's website and then manually install them?
I have a HP Envy 17 with 6850M and an i7, and it's been literally near impossible to get a working AMD driver. It will always result in Intel's driver being used, which is why I find it hard to believe that the AMD driver installed correctly on your system. It may have partially installed, which is why you can't get TF2 and Psychonauts (both 3D) running. To summarize, your graphics drivers might be in a broken state right now.

Here's a simple test we can do to see if 3D acceleration is working on your laptop in Ubuntu.

Open a new Terminal, and in it type the following and hit Enter:
```
glxgears
```

You'll know it's working if you can see 3 gears, blue green and red all spinning. Let me know if you can see them.

---

### Post by Ritlengo on 2013-04-02
I just followed some links when searching around for this problem and I found it somewhere 
I can see the cogs just fine.

---

### Post by myromance123 on 2013-04-02
Have you tried running Steam from a Terminal? This could help you identify the error that's happening whenever you try to start up a game. I'm trying to think of reasons it could be doing this, but besides it being a graphics driver issue I honestly don't know.

Could you point out anything you might personally think could be causing this problem, or even remotely be related to this problem?

---

### Post by Ritlengo on 2013-04-02
No I'm actually kinda new the Ubuntu so i don't know alot about it. 
But i really appreciate your help.

---

### Post by myromance123 on 2013-04-02
You can run Steam in the Terminal by opening a new Terminal and Entering:
```
steam
```

It'll output a lot of stuff, but only focus on what it outputs when you try to launch the game. I have to go to bed since I have a presentation tomorrow, but I'll get back to you tomorrow if no one else has.

Post any sort of error or output from the Terminal here, when you try to launch either TF2 or Psychonauts. Hopefully it'll shed some light on what could be going wrong.

---

### Post by Ritlengo on 2013-04-02
(steam:31933): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully
SDL video target is 'x11'
SDL video target is 'x11'
Installing breakpad exception handler for appid(gameoverlayui)/version(20130329114045_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Gtk-Message: Failed to load module "overlay-scrollbar"
[0402/184802:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Using breakpad crash handler
Setting breakpad minidump AppID = 440
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  
Did not detect any valid joysticks.
Gtk-Message: Failed to load module "overlay-scrollbar"
[0402/184803:ERROR:resource_bundle.cc(411)] Failed to load /home/myname/.local/share/Steam/SteamApps/myusername/Team Fortress 2/cef_gtk.pak

---

### Post by Ritlengo on 2013-04-02
Thats what I got from the terminal

---

### Post by myromance123 on 2013-04-03
> [0402/184803:ERROR:resource_bundle.cc(411)] Failed to load /home/myname/.local/share/Steam/SteamApps/myusername/Team Fortress 2/cef_gtk.pak

That seems to be the issue, at least for TF2. I know this is very basic, but have you Validated your TF2 files in Steam?

In Steam, under your games library, right click Team Fortress 2 and click Properties.

Now click the Local Files tab. Then click "Verify Integrity of Game Cache". It can take a while, maybe even  20 minutes but it'll check all your game data files to make sure there's no corruption.

After doing that, does it still return the same error?

---

### Post by drawkcab on 2013-04-04
Sometimes Steam just needs to be restarted in order for an update to install.  Sometimes it just needs to be restarted for my games to launch.  

Either way, having the best proprietary driver installed will help enormously so start there.

---

### Post by Ritlengo on 2013-04-13
Just installed ubuntu 12.04 LTS and now everything works just fine, thx for all the quick replys and all the help.

---

