---
title: "Tips/hints for UT2004"
date: 2007-03-02
forum: Gaming &amp; Leisure
---

### Post by Eazy© on 2007-03-02
[COLOR="DarkGreen"]**[SIZE="3"]Tips for UT2004[/SIZE]**[/COLOR]

I'm not trying to make a HowTo, just some tips and hints of what's possible to do. I still consider myself as a noob on Linux, and I will probably not be able to help you much if you want to try the things I post here. I run Kubuntu and have not tested any of these things on Ubuntu. I am also not good at writing, but I did the best I could :)

I play a lot UT2004 on-line and I have tried to make my UT2004 experience more comfortable. So over the last 2 years I have (off and on) tinkering with a lot of different things to make things better.



Biggest problem was to make UT2004 run smooth on line, and to accomplish that I had to compile my own kernel (did it some time ago so my version is 2.6.18). The reason why I had to compile my own kernel was so I could get 500hz (the guide on linux-gamers didn't work for me) for my mouse to make UT2004 run smooth. It took me about 3 months to find out that the mouse was to blame for all troubles I had. You may not have the same problem as I had, so maybe you don't need to compile a new kernel.

[COLOR="Red"][SIZE="4"]The kernel compile tip is outdated concerning mouse-polling. You should try[/COLOR] [[COLOR="Blue"][SIZE="4"]Cappy's Mouse-polling howto[/SIZE][/COLOR]]("http://ubuntuforums.org/showpost.php?p=2347666&postcount=1") [COLOR="Red"]  first.[/COLOR][COLOR="Red"] I'll leave the kernel compile section in here in case someone wants to use it, or if Cappy's howto doesn't work (it should). I also leave it here because I haven't tested Cappy's howto myself.[/COLOR][/SIZE]

[COLOR="DarkGreen"]**_Kernel compile_**[/COLOR]

I will not get into how I compile my kernel but I used [this]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel") guide (the kernel-version have changed since I used this guide). To get 500hz for my mouse I used [this kernel-patch]("http://no.oldos.org/files/2.6.18-rad1/broken-out/usb-mouse-polling.patch"). I had some errors when I applied the patch, but it worked anyway. To set the mouse for 500hz I had to change a number under "USB_HID" to 2ms (2ms = 500hz) The name of the module is: CONFIG_USB_HID_MOUSE_POLLING_INTERVAL=2. I also had to apply the linux-patch-evems which I downloaded through synaptic to make my ntfs-disk to mount.

[COLOR="DarkGreen"]**_Xchat and UT2004_**[/COLOR] (I had much help from a Linux guru named NakedApe on this. Thanx man!)

As I am a on-line gamer I use IRC a lot, and xchat is my favourite IRC-client.
You can not start UT2004 from xchat with UT2004-links (ut2004://) normally (normal IP works). To make those links clickable you have to compile xchat from source. 

Download the source from [http://xchat.org](http://xchat.org) and decompress it. Open the file: /home/YOUR_USERNAME/xchat2/src/common/url.c with a text editor. Find the line { D("gopher://") }, .Copy that line and paste it under the line you just copied. Change gopher:// to ut2004://. When you are done it looks like this:
 
----Cut-----
		{ D("rtsp://") },
		{ D("gopher://") },
		{ D("ut2004://") },
	},
	suffix[] = {
		{ D(".org") },
		{ D(".net") },

----cut----

Save the file and compile. When xchat is installed, start xchat and go to settings --> advanced --> URL-Handler. Make a new  post and name it Open with UT2004 (or whatever you prefer) then add the command !ut2004 %s Make a new post and Name it Spec with UT2004 and the command !ut2004 %s?SpectatorOnly=1 Now you can start UT2004 as a player or as a spectator from Xchat if you right click on either a "normal IP" or a ut2004://IP

[COLOR="DarkGreen"]**_Beryl and UT2004_**[/COLOR] (NakedApe on this one as well)

I get poor performance when playing UT2004 at the same time I have Beryl on, so I have a script that will turn it off when I start UT2004, and when I'm done playing, close UT2004 Beryl turns back on automatic. You might want to change the URL-handler to point to the script in Xchat if you use it.

Start your favourite text editor and paste this in:

```
#!/bin/bash

killall -s USR2 beryl-manager
ut2004 $@ ;
killall -s USR2 beryl-manager
beryl & emerald --replace & 
exit 0
```

Name it noberyl (or what you prefer) and save it in /home/bin. Then chmod a+x noberyl Change the command !ut2004 %s in xchat URL-handler to !noberyl %s

[COLOR="DarkGreen"]**_Hotkeys and UT2004_**[/COLOR]

I cannot guarantee this will work if you got a keyboard that is not the same as mine.

UT2004 seems to hog the keyboard for it self, so change songs in Amarok does not work from the media buttons. To get around this you need to install hotkeys from the repository: 

sudo apt-get install hotkeys

Open up a console and write:

hotkeys -l
If you are lucky you will find your keyboard in the list. I have "logitech Internet Navigator Keyboard" so I pick itouch. If your keyboard is not listed you can try one that is closest to yours. Test your way forward to one that works. You can edit it later using xev.

in console:
hotkeys -t itouch

Now if you found your keyboard and use xmms as your mp3-player you don't need to do anything more, but if you use Amarok you need to edit the hotkeys.conf

sudo your_text_editor /etc/hotkeys.conf 

then change all the xmms line to this:

PrevTrack=amarok --previous
Play=amarok --play-pause
Stop=amarok --stop
Pause=amarok --pause
NextTrack=amarok --next
# Rewind=

To be able to change Amarok's internal volume you need to add some key codes to your "Keyboard definition file". Mine was itouch if you remember :) Yours may be some other but I use mine as an example:

Choose two multimedia-buttons you are not using. Start xev from a console. Press the buttons you choosed. The keycode, you will see in the console. Now write down the keycode an a piece of paper (or whatever)

In console:
sudo your_texteditor /usr/share/hotkeys/itouch.def
find a line that resembles like this:

<!-- Feel free to customize this -->

and add this under it:

    <userdef keycode="234" command="dcop amarok player volumeUp">Amarok Volume Up</userdef>
    <userdef keycode="233" command="dcop amarok player volumeDown">Amarok Volume Down</userdef>

I have been trying to get pasting to work with UT2004, hotkeys and klipper, but I have not yet succeeded. 

dcop klipper klipper getClipboardContents

does only work in a console and only in the console a execute the command. This is a problem I like to solve.

[COLOR="DarkGreen"]**_gUnrealTools_ (guts)**[/COLOR]

gUnrealTools is a tool for UT2004 which include a "cache manager" (which installs what's in the cache into real files), a "UMod Unpacker" (unpacks UMods), "Unreal Compressor" (compress and decompress uz2-files) and Umark Benchmark-starter (you need Umark for this: [http://www.unrealmark.net/](http://www.unrealmark.net/) site seem to be down atm.)

I do have a deb-package for it but no where to upload it to. If you like to compile from source you find it [here]("http://gunrealtools.sourceforge.net/")

[COLOR="DarkOliveGreen"]_**Key binds**_[/COLOR]

I only Play TDM and these binds are the only ones I use, so I don't know the binds for other weapons etc.

It is of course possible to bind weapons in the game and it's probably the easiest way, but if you want to bind more than 1 weapon to a key, you need to do this in your user.ini.

2 weapons on one key:

Key_You_Want_to_bind=PipedSwitchWeapon 4 | PipedSwitchWeapon 9

This will give you Shock Rifle and Lightning Rifle on the same button.

Key_You_Want_to_bind=PipedSwitchWeapon 6 | PipedSwitchWeapon 5

This will give you Mini Gun and Link Gun on the same button. Think you understand how it works now :)

ID-number for Weapons:

0 = Super Weapons
1 = Shield Gun
2 = Assault Riffle
3 = Bio Rifle
4 = Shock Rifle
5 = Link Gun
6 = Mini Gun
7 = Flak Cannon
8 = Rocket Launcher
9 = Lightning Rifle
10 = Translocator 

The Shield Gun is good to have a bind to. Here is a trick that will save you some time:

MiddleMouse=switchweapon 1 | altfire | onrelease switchtobestweapon

As long as you hold down Middle Mouse you will have the shield and as soon as you let go of the button you will get the weapon you had before.

Throw weapons to your team mate and at the same time tell you throw a weapon:

Key_You_Want_to_bind=Teamsay [%W] dropped [%L] | ThrowWeapon (you van change "dropped" to something else if you like. e.g. "here is a gun for you" :P

100 armour, 50 armour and Double Damage spawns in intervals, and it's good to say to your team mate you took one of these things. e.g. (make you personally touch :))

Key_You_Want_to_bind=teamsay >> 50 Armour Taken, 27 Seconds To Respawn <<
Key_You_Want_to_bind=teamsay >> 100 Armour Taken, 54 Seconds To Respawn<<
Key_You_Want_to_bind=teamsay >> DD Taken, 81 Seconds To Respawn <<

Here are the Spawn times for armour etc.:

27.5 seconds: Weapons, Ammo, Adrenaline, Health, 50 armour
55 seconds: 100 armour, 199-Health
82.5 seconds: Double Damage (lasts for 27 seconds)


This is so far the tips I got. If someone has a tip, or feel I'm out in the blue, I could add it to this post if you like :)

---

### Post by cookfromfrozen on 2007-03-02
Very helpful, good work.  When I first installed UT2004, I had trouble locating the latest Linux patch for it (3369).  If anyone needs it, it is available [HERE](http://icculus.org/news/news.php?id=2536).

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-03-02
Thanks for sharing and taking the time to compile your HowTO on this subject: This is great information to have available here on the forums. 

Regards,

---

### Post by Eazy© on 2007-03-03
The feeling that I had waisted to much time on UT2004 is less when I post this ;) 

If I come up with anything else, I will add it. I could make a little guide on how to make key bindings for weapons if someone needs it etc.

---

### Post by cookfromfrozen on 2007-03-03
A key binding guide would be good. :) Binding "playvehiclehorn 1" is always good :D

---

### Post by Scunizi on 2007-03-09
sometimes I'd rather play ut2004 in a window instead of full screen.  I use to be able to but since I maximized it I haven't found a way to get it back to the window state.  Any ideas?

---

### Post by Eazy© on 2007-03-10
Alt + enter puts UT2004 in window mode. Ctrl + G releases the mouse. To set what size you want for the window mode:
Open your ut2004.ini with a texteditor, find and edit this:

```
[SDLDrv.SDLClient]
WindowedViewportX=800
WindowedViewportY=600
```

This sets my ut2004 in 800x600 window.

---

### Post by Scunizi on 2007-03-11
Thanks!  That worked like a charm!:guitar:

---

### Post by anonymous_user on 2007-05-26
I cannot find /home/bin. Does the bin folder have to be manually created?

---

### Post by Eazy© on 2007-05-26
try and creat /home/bin. If it does not work, you can put the script in /usr/bin.

---

### Post by phr0ze on 2007-06-16
What an excellent guide. I was trying to play UT with beryl on, and it was a major pain. UT would lock up the system when I tried to close it. 

Thanks.

---

