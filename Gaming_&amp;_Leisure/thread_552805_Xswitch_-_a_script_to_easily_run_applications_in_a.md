---
title: "Xswitch - a script to easily run applications in another xserver"
date: 2007-09-17
forum: Gaming &amp; Leisure
---

### Post by deadlydeathcone on 2007-09-17
This script tries to make it as easy as possible to run applications in another xserver - just add "xswitch" before a program's name - up to eleven at a time - and it will be automatically started in a new xserver. Plus, when the program exits you won't be stranded in the grey void of an empty xserver - you'll be prompted as to how to get back to your original desktop.

It also has the ability to shut down the old xserver after starting the new, making it useful for setting up minimal gaming desktops. For example, the command ```
xswitch -s gnome-terminal metacity nautilus
``` starts up a terminal, window manager and file-manager and then, because of the -s flag, shuts down the original xserver.

You can also run more then two xservers - the "-d" flag to specifies which display they are started on. "1" is the first display after you current desktop (tty 7), "2" the second and so on.

To install, [grab the script]("http://ubuntuforums.org/attachment.php?attachmentid=74092&d=1213501654"), download it to your home directory, and enter the following command in a terminal:

```
sudo tar -xvvzf xswitch_0.9.tar.gz -C /usr/bin/
```
You'll also need to have zenity installed, so if you haven't, ```
sudo apt-get install zenity
```

A word of thanks - credit for this goes to cogadh, as this script is largely an automated version of his discoveries in [this thread ]("http://ubuntuforums.org/showthread.php?t=493025").

############
# Other stuff #
############

If you use a program with either spaces in the name or command line arguments, surround it in quotes, like this - ```
xswitch "winefix -d 1 /home/jack/.wine/drive_c/Program Files/df_suba/dwarfort.exe" metacity 
``` If a program is using the one after it as a command line argument, add two quotes ( "" ) between them.

When the script is first started, unless you've run multiple xservers before, the first thing you'll see is this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43852&stc=1&d=1190225619[/IMG]

Answer yes and the script will change a line in /etc/X11/Xwrapper.config that allows xservers to be started without root permissions, and then immediately changes it back after a xserver is launched. If you never want to be bothered by it again, though, just edit the file yourself and change the line "allowed_users=console" to "allowed_users=anybody".
If you answer no, you will still be able to launch xservers - just as root. The other method is recommend.

Let me know if there are any bugs or problems.

Full command line options:
[CODE]-c Specify a custom xorg.conf to use with new xservers.
  -d	Specify the tty used to display the new xserver.
  -s	Set to stop the display manager after a new xserver
	  is executed. Supports both GDM and KDM.
  -u	Display this usage message.

#############
# Useful apps #
#############

If you experience screen flickering or would like to move windows around, add a window manager:
metacity
xfwm4

If you'd like to bring theme settings along:
gnome-settings-daemon
xfce-mcs-manager

Light file managers:
thunar
pcmanfm

Screens:
1) Geany and Metacity - Oh, the wild abandon!
2) Compiz, terminal, and a random Wine app.

---

### Post by Moustacha on 2007-09-19
so um...where can i download this from?

---

### Post by deadlydeathcone on 2007-09-19
Oh... right. That's probably important.

[Here you go.]("http://www.box.net/shared/rbx7aapzpf")

---

### Post by Moustacha on 2007-09-19
Thanks :D

---

### Post by deadlydeathcone on 2007-09-21
I uploaded a new version with one change - it now, when run via terminal, doesn't spam it like crazy with status messages. Sorry about that.

---

### Post by Joebob06 on 2007-10-29
I have Wow running with winefix and a nice value of 10, and have a couple of questions about the program Xswitch to go with it.  Does it only work with Nvidia cards or Ati also?  Also when you run Xswitch is it still possible to change the nice value?  I've tried to get it to work a few times this morning, and says Wow cannot start 3d rendering.  I have ati X330 video card.

Thanks,
Joseph

---

### Post by Super Jamie on 2008-04-13
Hi there

I love your work with Winefix, and discovered this is an awesome script too! Especially for playing fullscreen games on one monitor, whilst having a dual monitor setup for desktop work. However, I have a couple of requests:

1) would it be possible to include a commandline option to suppress the "Ctrl Alt Backspace" message? this is the only reason I see for loading a window manager in a new fullscreen X, it would be handy to just not have it

2) is it possible to specify a different xorg.conf for the new X server? as above, useful for dual screen desktop, but single screen games

at the moment, i'm using this script to overcome it (eg: unreal tournament)
```
#!/bin/bash
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo cp /etc/X11/xorg.conf-single /etc/X11/xorg.conf
xswitch "nvidia-settings --load-config-only" metacity /home/superjamie/ut/ut
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
but it's not particularly ideal

---

### Post by biriachan on 2008-06-10
This is great THANX!!!!

When I start a second Xserver for gaming and switch back to my first (Original) Xserver I am able to hear sound from the 2nd Xserver on the first Xserver, but I am unable to hear sound from the 1st Xserver on the 2nd Xserver.

Anyone know of a way to get the sound from my 1st Xserver to play on the 2nd Xserver???

I need to be able to hear Email notification sounds.

Update!!! ###################################################################

I found a Deb package here on ubuntuforums that fixed my problems with sound not passing in both directions between the two Xservers.

Not really sure how or why this fixed the issue, but I have tested it on 3 different computers and if fixed the sound on all three.

The PulseAudio Deb package can be found here
[http://ubuntuforums.org/showthread.php?t=759147]("http://ubuntuforums.org/showthread.php?t=759147")

---

### Post by deadlydeathcone on 2008-06-15
Hello everyone, sorry for my extended absence. My computer died and I haven't been able to get on the forums for a while.

Long overdue answers:

Joebob06 - It's still possible to change the nice value when using winefix along with this script. I don't have an ATI card to test with, but Nvidia cards work perfectly.

Super Jamie - Thanks for the encouraging words! I added a command line option to use custom xorg.conf files in the new version. Use it like this: ```
xswitch -c "path/to/xorg.conf" gamefoo
```. If the file's already in the /etc/X11 folder you can omit the full path.

biriachan - I think that's a pulseaudio problem, as it by default publishes the audio output of applications to their parent xserver. I'll try to figure out how to fix it sometime soon, as it IS pretty annoying.

---

### Post by szaqlon on 2008-07-07
I have been trying to run this: xswitch "winefix C:\Program Files\World of Warcraft\Launcher.exe" and have been getting this 
"/usr/bin/xswitch: line 276: nvidia-settings: command not found" Anyone know what is causing that?

---

### Post by jbsongaku on 2008-07-16
> **szaqlon said:**
> I have been trying to run this: xswitch "winefix C:\Program Files\World of Warcraft\Launcher.exe" and have been getting this 
"/usr/bin/xswitch: line 276: nvidia-settings: command not found" Anyone know what is causing that?

Do you have an NVIDIA card?

if you dont have an NVIDIA card you should remove the nvidia-settings part from the script(s)

---

### Post by biriachan on 2008-08-11
When using Xswitch my 2nd Xserver uses the default Keyboard shortcuts and not the custom setup I use in my own user account.

Gconf-editor was used to re-configure my keyboard short-cuts/modifiers.

I have modified My <ALT> Right Mouse, for gaming with WINE.  I believe the custom key mappings I created are stored somewhere in my Home Folder but I'm not sure where they are stored.

I think the 2nd Xserver is loading up root/default settings. If so which files do I need to copy from my Home folder and where should they go on Root??

Anyone have any ideas?

---

### Post by binger on 2008-08-18
The xswitch works, but when I exit my game, the screen goes black.  ctrl-alt-backspace does nothing.  I have to ctrl-alt-F7 and I can see xswitch end in the console, but it doesn't shutdown my second xserver fully because i still have X0 and X1 in /tmp/X11-unix/.

Also, when I am in a game in the 2nd xserver and switch back to my main xserver to IM/surf/etc  i can see the cpu drop alot, and when I switch back to the game, it has to reconnect.  Is there a way to make it keep the 2nd sever "alive" so to speak?

Thanks!

---

### Post by oldskool73 on 2008-08-30
Hi, really handy script. I'm using it to switch from a dual display to a single for games using the alternate config switch.

I had a bit of an issue once when a game crashed and took down the main xserver as well, and because Xswitch hadn't had a chance to clean up it left my xorg.conf in single screen mode on reboot, bit of a pain.

So I thought, wouldn't it be safer to use the -config switch when starting X if possible (ie, if it's in /etc/X11/ already) instead of moving the configs around? I've made a patch that seems to work ok, it's only a few lines so here's the diff, feel free to use it if however...

```

120c120
< 	if [ "$XORGCONF" ] && [ ! -r "/etc/X11/$XORGCONF" ]
---
> 	if [ "$XORGCONF" ]
236d235
< ALTCONFIG=""
249,250d247
< 	else
< 		ALTCONFIG="-config $XORGCONF"
275c272
< $ROOT X $ALTCONFIG :$DISPLAY -ac &>/dev/null &
---
> $ROOT X :$DISPLAY -ac &>/dev/null &

```

...to use it just start it with -c config_name.cfg, the config must be in /etc/X11/ already e.g.

```

xswitch -c xorg_single.conf gnome-terminal metacity

```

I've not tested much, but looking at the code I guess this should be a lot safer in situations where you need to have multiple xswitch sessions with different configs running at once, less chance of configs getting overwritten out of order?

Adam

---

### Post by glotz on 2008-10-08
[QUOTE=deadlydeathcone]This script tries to make it as easy as possible to run applications in another xserver[/QUOTE]Why did we want to do that again exactly? :confused:

---

### Post by kazimk1 on 2009-03-25
I apply all statements but I have no sound. aplay -l says me no sound card detected and lspci -v give audio card capabilities as acces denied.What is wrong with me?Any help great appreciate.

---

### Post by Baddreamz on 2011-07-24
i am trying to launch counter strike or steam
but i always got cannot start application ""

xswitch "winefix -d 1 /home/cristiano/.PlayOnLinux/wineprefix/Steam/drive_c/Programas/Steam/steam.exe" metacity

already tried without quotes.

i even tried these 

winefix -d 1"/home/cristiano/.PlayOnLinux/wineprefix/Steam/drive_c/Programas/Steam/steamapps/exo0m_/counter-strike/hl.exe"

and
/home/cristiano/Desktop/Steam



i am probably doing wrong something.


regards

---

### Post by Perfect Storm on 2011-07-24
Necromancy. Thread closed.

---

