---
title: "I can not play any of these games..."
date: 2010-05-04
forum: Gaming &amp; Leisure
---

### Post by Edward B. on 2010-05-04
I recently made a donation and downloaded the five games available as part of the [Humble Bundle]("http://www.wolfire.com/humble").

I am running the most recent version of Ubuntu.

Only **World of Goo** installed, and that game is running so slow that it is not playable. My PC exceeds all of the system requirements.

As for the rest:

**Aquaria**

Could not display "/home/edward/Desktop/Humble...ia-lnx-humble-bundle.mojo.run".

There is no application installed for executable files

**Lugaru**

Could not display "/home/edward/Desktop/Humble...ugaru-full-linux-x86-1.0c.bin".

The file is of an unknown type

**Gish**

Nothing happens. I click on the icon labeled "Gish" that looks like a set of blue gears. Absolutely nothing happens.

**Penumbra**

Could not open the file /home/edward/Desktop/Hu&#8230;/penumbra_overture_1.1.sh.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.


Any help would be greatly appreciated.

---

### Post by fetuszero on 2010-05-04
For **Penumbra**, right click the file and select "Properties", under the "Permissions" tab tick the box next to "Allow executing file as program".

Once that's done, double click the file and choose "Display in terminal", it will unpack the installer and run automatically, as well as giving you the coupon code to the rebate for the Penumbra Collection on Frictional Games store.

For **Aquaria**, follow the same steps as Penumbra. When you'll double click it, the installer will pop up.

For **Lugaru**, I placed the .BIN file into my home folder and followed a command I found that worked from the terminal:
> chmod 775 lugaru-full-linux-x86-1.0c.bin

sudo ./lugaru-full-linux-x86-1.0c.bin
After that, the installer should pop up.

I too have purchased the pack and am looking to install them. I'll come back if I find anything for the last one. By the way, thanks for supporting the cause :]

---

### Post by hikaricore on 2010-05-04
There is a known issue with Gish, the developer should be aware of it and has a fix pending.

---

### Post by Edward B. on 2010-05-04
Well, that explains Gish.

Fetus, thanks for the info. It worked on Aquaria. The game installed, but is still running incredibly slow. It took probably 15-20 minutes for the screen to scroll to the heroine. 

I have never had any problems like this before.

Is it possible that the latest edition of Ubuntu is causing this problem?

EDIT: Just tried Battle for Wesnoth and it ran perfectly. Now, I know the other two games are more graphic intensive, but when I had Windows on this PC it ran Gun and Medieval II: Total War with few problems.

---

### Post by Merritt.kr on 2010-05-04
> **Edward B. said:**
> Well, that explains Gish.

Fetus, thanks for the info. It worked on Aquaria. The game installed, but is still running incredibly slow. It took probably 15-20 minutes for the screen to scroll to the heroine. 

I have never had any problems like this before.

Is it possible that the latest edition of Ubuntu is causing this problem?

EDIT: Just tried Battle for Wesnoth and it ran perfectly. Now, I know the other two games are more graphic intensive, but when I had Windows on this PC it ran Gun and Medieval II: Total War with few problems.

First thing that pops to mind is: have you installed your graphics drivers? That could cause the issues. Works perfect for me.

Thanks @ hikaricore for the tip on Gish, I was worried. :)

---

### Post by matchett808 on 2010-05-04
sh ./penumbra_overture_1.1.sh for the last one, I only have 1 left that i have not tried....



edit: all installed, the .run and .sh and .bin need to be a+x'd

---

### Post by fetuszero on 2010-05-04
> **Edward B. said:**
> Well, that explains Gish.

Fetus, thanks for the info. It worked on Aquaria. The game installed, but is still running incredibly slow. It took probably 15-20 minutes for the screen to scroll to the heroine. 

I have never had any problems like this before.

Is it possible that the latest edition of Ubuntu is causing this problem?

EDIT: Just tried Battle for Wesnoth and it ran perfectly. Now, I know the other two games are more graphic intensive, but when I had Windows on this PC it ran Gun and Medieval II: Total War with few problems.

I have no problems running Aquaria in 1680x1050 on Lucid, runs perfectly for me. So I'd say like Merritt.kr and check to make sure you have the latest drivers.

If all fails, I believe *(could be wrong)* that the official final release of Aquaria for Linux never took place meaning we probably have their latest test build, so you can always try running the Windows version in Wine, it used to worked fine for me back then.

I'm glad to know for Gish, I was wondering what to do since it's the only one I couldn't get to work.

---

### Post by Merritt.kr on 2010-05-04
Seems Gish is working now. The original file was version 153, now version 153-1 is available. It also has a gish64, which for me does nothing even though I run 64-bit, but the normal gish file works now (no install apparently, that runs the game!)

So go download your Gish!

---

### Post by Edward B. on 2010-05-04
Stupid question. How can I find what drivers I need to install and where can I find them at?

---

### Post by fetuszero on 2010-05-04
> **Edward B. said:**
> Stupid question. How can I find what drivers I need to install and where can I find them at?

From the taskbar: System > Administration > Hardware Drivers
Then choose the recommended one, it should do the trick (worked for me) as it automatically checks and offers the appropriate ones. Otherwise you can go to your graphic card provider website and download the Linux drivers for the appropriate model that you have and see if it works better.

And Gish does work now! So you can go redownload it from Wolfire's website.

---

### Post by prions on 2010-05-05
I just downloaded gish and nothing happens still, it is set to run as an executable file also.

Got it to work, install libopenal1 from synaptic.

---

### Post by ad_267 on 2010-05-05
Yeah Gish doesn't include the libraries it needs and expects them to be installed, so you might have to run it from a terminal and check for any errors.

---

### Post by weeman43302 on 2010-05-05
Does Gish even install? Or do you just have to click on the icon?

---

### Post by Perfect Storm on 2010-05-05
> **weeman43302 said:**
> Does Gish even install? Or do you just have to click on the icon?

[http://ubuntuforums.org/showpost.php?p=9239521&postcount=39](http://ubuntuforums.org/showpost.php?p=9239521&postcount=39)

---

### Post by Elwro on 2010-05-05
Unfortunately, the Aquaria Linux version I bought via the bundle does not run on my Ubuntu 9.10 i386 32bit with the official nVidia drivers. My resolution is 1440x900; when I run the game, the screen goes black with an "out of range" message. The only thing I can do is shut down Gnome. Any pointers?

edit: and Gish does not have sound for me:

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: alSource.c:2362: alcDestroyContext(): deleting 13 Source(s)
AL lib: alBuffer.c:1079: exit(): deleting 32 Buffer(s)


edit: I tried the suggestions here: [http://ubuntuforums.org/showpost.php?p=9239521&postcount=39](http://ubuntuforums.org/showpost.php?p=9239521&postcount=39) but they didn't help me.


Penumbra Overture also gives me the "Out of range" error.

---

### Post by kamon8124 on 2010-05-05
here, check this out for a fix to gish
[https://help.ubuntu.com/community/Games/Native/Gish]("https://help.ubuntu.com/community/Games/Native/Gish")
that seems to be working for people, at least as far as sound goes.
Good luck!

---

### Post by Edward B. on 2010-05-05
I'm going to try fiddling with my system later tonight. I really wish that the people promoting the bundle would have mentioned that Linux users will have to jump through hoops to get the games to work, however. I was anticipating them to be as easy to install and run as any game you would download using the package installer. If I knew it was going to be so much trouble, I would not have purchased the package of games.

EDIT: Installed drivers. World of Goo appears to be running... I was only able to check out the title screen, but it is running quite fast. Aquaria, however, has gotten worse. Now the title screen does not even come up - instead there is a floating box that reads "Invalid Input" or "Input Error" or something similar. I had to physically turn the computer off and on again in order to clear it.

---

### Post by Elwro on 2010-05-05
> **kamon8124 said:**
> here, check this out for a fix to gish
[https://help.ubuntu.com/community/Games/Native/Gish]("https://help.ubuntu.com/community/Games/Native/Gish")
that seems to be working for people, at least as far as sound goes.
Good luck!Thanks! Turned out "sudo apt-get purge bluez-alsa" did the trick in my case (alsa seems to have been set to use bluetooth devices... with bluetooth turned off. Weird, since I had sound from audio CDs and mp3s... well, anyway, it worked).

edit: @Edward B., the next time something like this happens, try ctrl-alt-backspace to restart gnome which might be easier on the hardware.

edit: and anyone with problems regarding Penumbra should check [this](http://www.frictionalgames.com/forum/thread-3049-post-27202.html#pid27202) thread, which solved my issues.

---

### Post by Edward B. on 2010-05-05
> **Elwro said:**
> Thanks! Turned out "sudo apt-get purge bluez-alsa" did the trick in my case (alsa seems to have been set to use bluetooth devices... with bluetooth turned off. Weird, since I had sound from audio CDs and mp3s... well, anyway, it worked).

edit: @Edward B., the next time something like this happens, try ctrl-alt-backspace to restart gnome which might be easier on the hardware.

edit: and anyone with problems regarding Penumbra should check [this](http://www.frictionalgames.com/forum/thread-3049-post-27202.html#pid27202) thread, which solved my issues.

Thanks for the info. I did try doing that with Aquaria but it did not work. Not sure what issue I am running into now.

---

### Post by Edward B. on 2010-05-05
Gish is working perfectly for me. And World of Goo (it locked up once, but I have a feeling this is an issue with my PC).

These two games are a lot of fun, especially World of Goo, so I don't feel quite so bad now that I've gotten them to work.

I can not even figure how to install Lugaru, however.

---

### Post by hikaricore on 2010-05-05
There are posts thoughout this thread that tell you how to install it.
Re-read them.

---

### Post by Edward B. on 2010-05-05
> **hikaricore said:**
> There are posts thoughout this thread that tell you how to install it.
Re-read them.

Woops, so there is.

Lugaru now operating fine.

My only problem is that the sounds cuts out sometimes, requiring a restart. Any ideas on what type of problem this may be?

I have not tried to install Penumbra yet.

That leaves Aquaria as the only game I can not get to work. I will try more tonight.

Thanks to everyone for all of their help.

---

### Post by hikaricore on 2010-05-05
You'll need to flag both Penumbra and Aquaria as executable just like Lugaru for them to be installable.
Aquaria is amazing once you get into it.  :)

---

### Post by Edward B. on 2010-05-05
> **hikaricore said:**
> You'll need to flag both Penumbra and Aquaria as executable just like Lugaru for them to be installable.
Aquaria is amazing once you get into it.  :)

Yeah, it looks pretty good. It is installed, just will not run for some reason.

On Lugaru, how in the heck are you supposed to get to the top of that lookout on the first campaign level to rescue the kid rabbit? I can jump onto the second block. There is a large outcropping above me, and one slightly below that across a ravine. I can not jump across to that one, or jump high enough to get on the one above me!

---

### Post by stoogiebuncho on 2010-05-05
Crouching makes you jump higher.

---

### Post by ad_267 on 2010-05-05
And when fighting in Lugaru just hold down the left mouse button, it works way better than clicking.

---

### Post by jorrieboy on 2010-05-07
I have a problem with aquaria;
When I run "./aquaria-lnx-humble-bundle.mojo.run", it loads the installer window, but after a while it reports that there is an fatal error, and that he can't make a file.

Does anyone knows what the problem is?!?!

EDIT:
I've downloaded it again, and it i've installed it

---

### Post by dh04000 on 2010-05-09
NOTICE: Initial Lua setup failed. Cannot continue.
[hit enter]


Its says that for Aquaria and the Lagura? How do I fix this?

---

### Post by brunotc on 2010-05-13
Here's a fix that worked for me:

Edit /etc/openal/alsort.conf and add a line that says:

**[FONT=Courier New][SIZE=3]drivers=oss[/SIZE][/FONT]**

Try to run Gish again.

This will make OpenAL default to its OSS backend, which apparently works on Ubuntu. By default, it will try its Pulse or Alsa backend (I'm not sure which), which is causing the "connection failed" problem.

But, as with any advice, YMMV.

---

### Post by dmuir on 2010-05-15
> **dh04000 said:**
> NOTICE: Initial Lua setup failed. Cannot continue.
[hit enter]


Its says that for Aquaria and the Lagura? How do I fix this?

Probably a corrupt download. I had the same problem. Check the MD5 hash. It should be 8b24ddeeb553e028bbd501102f891cc2

Cheers,
David

---

### Post by sp0tz on 2010-05-18
A few people ITT are having an issue where the games start up, but their monitors just say "invalid input range" or something similar. This is because several of the games are set up to run at some 4:3 resolution and their monitors can only support widescreen. The fix for world of goo is as follows:


from the world of goo install directory, get into the "properties" directory. There's a config.txt file in there. Open that in vi or gedit and look for these lines:

  <param name="screen_width" value="whatever" />
  <param name="screen_height" value="whatever" />

Replace the word whatever with your resolution's width and height to make the game run.



I'm trying to find a config file like that for aquaria, but it doesn't seem to be that easy. I don't have a non-widescreen monitor, or else I'd just set that up and change the resolution in game.

---

### Post by Perfect Storm on 2010-05-18
> **sp0tz said:**
> 
I'm trying to find a config file like that for aquaria, but it doesn't seem to be that easy. I don't have a non-widescreen monitor, or else I'd just set that up and change the resolution in game.

nano ~/.Aquaria/preferences/usersettings.xml


None of the games gave me trouble with widescreen games res 1680x1050.
On the other hand widescreen 1440x900 monitors = troubles when it comes to games.

---

### Post by sawjam on 2010-05-23
Problem Aquaria - Mouse can't exit game or select things.
Had to physically shut machine down to gain control.


Solved this by editing the .../.Aquaria/preferences/usersettings.xml 

Changed this line to :  <JoystickEnabled on="0" />

Was previously .."1" I think it detected my Microsoft Wireless Keyboard as a Joystick.

---

### Post by MacFall on 2010-12-24
Hey guys, I just installed Braid from the new Humble Bundle pack (enabled running the .bin file as an executable, then dragged it into the terminal window). The icon shows up in my "Games" folder in the applications dropdown menu, but when I click it, nothing happens. Any clues?

---

### Post by thatguruguy on 2010-12-24
> **MacFall said:**
> Hey guys, I just installed Braid from the new Humble Bundle pack (enabled running the .bin file as an executable, then dragged it into the terminal window). The icon shows up in my "Games" folder in the applications dropdown menu, but when I click it, nothing happens. Any clues?

Open a terminal and type the following: 

```

cd braid
./braid
```See what errors pop up, if any.

---

### Post by MacFall on 2010-12-24
I got this:

> Game Startup Error: Unable to set up graphics.
Reason: Failed to initialize OpenGL display.

To help fix this problem make sure you are running the newest version of your video drivers.
Lastly, you could try running this game with the -windowed command-line option.

---

### Post by thatguruguy on 2010-12-24
What video card are you using? Do you have the correct drivers set up?

Also, you might want to read the discussion in [this thread]("http://ubuntuforums.org/showthread.php?t=1644127").

---

### Post by MacFall on 2010-12-24
> **thatguruguy said:**
> What video card are you using? Do you have the correct drivers set up?

I actually have no idea, and don't know how to check. I thought about posting this in the noob forum, but figured I'd just use an existing thread instead.

---

### Post by MacFall on 2010-12-25
Ok, I got this using "sudo lspci |more"

> 00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev 
a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audi
o Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (r
ev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev
 a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address 
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
01:00.0 VGA compatible controller: Matrox Graphics, Inc. Parhelia (rev 03)


---

