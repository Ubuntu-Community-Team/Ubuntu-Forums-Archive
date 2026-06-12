---
title: "nvidia twinview vs. 9.04"
date: 2009-04-23
forum: Desktop Environments
---

### Post by trudnai on 2009-04-23
Hi There,

Just installed the 9.04 on my laptop and have some problems with the twinview mode with ubuntu/gnome/nvidia. Actually I have many problems...

1. I have two mouse cursors - one of each screen...
2. If I click on menu and try to start any app on the external monitor then the app starts up in the internal one -- it is ok if I do Alt+F2 and type a command, like xterm, then it opens up in the actual monitor
3. If I run FireFox on one screen, I cannot start another instance on the other screen
4. I had problems with the nvidia-settings -- basically I had to edit the menu to put gksu in front of the tool otherwise it cannot write into the xord.conf, but then when I click on save settings the app crashes with seg fault.

I think that's for now. Please wise me up if you have any idea where to look for solution, or if I have to raise a ticket for that.

---

### Post by Haise on 2009-04-23
I have the same problem regarding multiple cursors, only I'm not running twinview, I'm running multiple x sessions (one on each monitor).  Also, GNOME applications (e.g, empathy, rhythmbox, evolution) will always start on my middle monitor, regardless of which one of my x sessions I try to run them from.

I've switched back to gutsy in the meantime, since not having my applications start where I want to and having two extra cursors at any given point in time that don't do anything is completely unacceptable to me.

---

### Post by trudnai on 2009-04-24
Thanks for you input, Haise,

I think then the problem is in a different level than X drivers.

Actually, are you using more independent input devices? I mean do you have 1 PC while 3 people can work at the same time on it or is it only for 1 person config?

Oh, and the other question is that is possible to replace an already opened window onto another screen?

Thanks
Tamas

---

### Post by Red Dot on 2009-04-24
I'm running into the same problem across 3 monitors with Xinerama enabled on 9.04.

---

### Post by Haise on 2009-04-24
> I think then the problem is in a different level than X drivers.

Yep.  This configuration works fine without the aforementioned problems on my Lenny box, and it's running the same version of X and nv that are here.

> Actually, are you using more independent input devices? I mean do you have 1 PC while 3 people can work at the same time on it or is it only for 1 person config?

No, there's only one input device.

```
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

> Oh, and the other question is that is possible to replace an already opened window onto another screen?

Firefox is a special case; it doesn't normally let you do that, and has been that way for quite some time.  You can, however, run it with -p and create one profile for each screen, which is what I'm doing now.  That doesn't bother me, really, since it starts and binds to whatever screen you ran it from.

I'm more worried about the behaviour of it not letting me run gnome-terminal/evolution/any GNOME apps on any screen other than 0; i.e, if I start it from screen 2 or 1, it still starts up on screen 0.

---

### Post by Almighty on 2009-04-24
Add me to the list of unhappy users who can't use 3 monitors. Using the nvidia-settings app seems easy enough but just doesn't seem to work.

---

### Post by aze555666 on 2009-04-24
Hi.
I just upgraded to Jaunty and i'm having the same problems:
- with gusty, hardy and interpid, I had the nvidia drivers, and had the option "separate X screen", which was enabling me to use my 2 monitors separately, being able to use the 2nd one as if it was another computer when having a fullscreen app running on the first one (Guild Wars for example). It was working very well (except some odd things since Intrepid : some apps were launching on 1st screen when using a shortcut or menu-item on the second screen, and the Firefox problem solved by using Firefox+Epiphany)

- Now I'm using a brand new Jaunty ... and i'm unable to use Separate X screen, which makes the first screen black! Plus, I have 2 mouse pointers (not a very big deal but not realy cool). When I log-in, both screesn display the wallpaper, then the 1st screen displays the toolbars, then the 2nd screen displays the toolbars and the 1st one becomes black ! 
And both screens work when I use twinview or xinerama, but those options don't do what I want, since I can't use my 2nd screen once guild wars is running (no more task bar, no more menu bar...)

Could someone help me to make my "separate x screen" work properly please?
Haise, when you tried your separate x screen with jaunty, did you have my problem? Or just the apps not running where you want  and the muliple pointers?

thank you

---

### Post by Haise on 2009-04-24
> It was working very well (except some odd things since Intrepid : some apps were launching on 1st screen when using a shortcut or menu-item on the second screen

That's the problem I'm having now.  What did you do to fix that?

> Haise, when you tried your separate x screen with jaunty, did you have my problem? Or just the apps not running where you want  and the muliple pointers?

No; however, I've never used TwinView in my life, since I have more than one graphics card.  I've always never used Xinerama, since Compiz doesn't work with it across more than one device.

I've only ever used three separate X sessions.

They all start up fine, although it does take them noticeably longer to do so in Jaunty.  

My only problems are the lack of proper session awareness by applications and the fact that I have three pointers at any given point in time.

> Could someone help me to make my "separate x screen" work properly please?

Is there anything interesting in your xorg log?

---

### Post by aze555666 on 2009-04-24
For you problem : I can't say anything about the muliple pointer, it started with jaunty (and occurs whatever the multiple screen options is: twinview or xinerama or separate x screen alone (xinerama cancels separate x screen)) . For the apps : a firefox shortcut on desktop on the 2nd screen makes firefox run on this screen, I always had to use the Computer menu-item to run nautilus (don't know how tis menu item is called in english ... it's the place where you can see all your disks and your file system) cause it's the only one working fine with the multi-screen, and I didn't have any problem with the other applications. However, when I tried to use separate x screen with jaunty, I was under the impression that most other applications were running on the wrong screen (the 1st one, which was completely black so that i can't know what realy happened).

For my pultiple X sessions : as I said, I use this option alone without xinerama as you do. When the 2nd one finished starting, the 1st one becomes black (but doesn't crash, since I can see my mouse pointer in it or even move the windows that I don't see by using alt+left click, and it becomes normal when it shuts down : when I stop the computer, I can see it again during 1 second)

Here I post my xorg.conf, since I don't understand everything in it and can't say if there is something interesting about my problem
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Oct  1 15:09:35 PDT 2008
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "keyboard"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "keyboard"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "ServerLayout"

    # commented out by update-manager, HAL is now used
    #    InputDevice    "Keyboard0" "CoreKeyboard"
    # commented out by update-manager, HAL is now used
    #    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
    Option         "DontZap" "False"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD HX191D"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Siemens MCF 3811 TA"
    HorizSync       30.0 - 50.0
    VertRefresh     55.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024_75 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
As you can see, there a many commented line that must have been added by nvidia-settings when I tried every options available.

---

### Post by smokyink on 2009-04-24
Hi thats my first post in this forum and i think i can help you...
Here is how it works for me:

Open Terminal and write:
**[COLOR=black]"sudo nvidia-settings"[/COLOR]**[COLOR=black]
that opens the Nvidia X Server Settings menu

click on: >X Server Display configuration > Display > Configure...

than: check TwinView

click OK

than click :Save to X Configuration file

Save.

Quit and restart

[/COLOR]Windows and stuff open in proper screens
no mouse in both screens
you can move windows from one screen to another freely and so on...

Sory if i misunderstood and just lost your time

---

### Post by aze555666 on 2009-04-24
Twin view doesn't make 2 several desktops ... with twinview I have 1 normal desktop on my 1st screen (as if it was the only screen), and just a wallpaper on the other screen.  So if I want to use my 2nd screen, I have to open a window then drag it to the 2nd screen ... so that if i'm running a fullscreen guild wars on my main screen, I don't see the menu bar and the task bar anymore, then I can't use several windows on my secondary screen (firefox, totem ...)
That's why I always use separate X screen, with which the 2 screens are 2 different desktops, with a different cube on each, each of them working as if it was a singe-screen configuration -> I am under the impression to control 2 PCs with 1 mouse.
The probleme being that the main screen if completely black when I use separate x screen with jaunty...

---

### Post by smokyink on 2009-04-24
Well when you right click on the panel that you have on the original window and select 

New panel

> drag it to the second screen,

 > right click on it 

>select "add to panel" to add any icons,main menus, date and time, ecs..

This works for me...this way i watch movies while browsing in internet for example,but i don't know about fullscrean games though

...Maybe your screen wont go black...

 I mean if you still see the desctop on the second screen it should be ok i suppose. and about the cube i havent tryed it so dont  know...

---

### Post by aze555666 on 2009-04-24
I alreayd tried ... I don't know why,; I can't drag panels to the other screen.
I can't drag them at all, I can just right click-> properties -> orientation -> one edge of the main screen...

---

### Post by smokyink on 2009-04-24
hmm yea thats a bit buggy i think you could in 8.10...
but you can make many tabs (it first creates up, left, right then second screen: down, up ...)
thats how i did it

---

### Post by smokyink on 2009-04-24
i meant that you create many tabs then remove the ones you don't use

---

### Post by aze555666 on 2009-04-24
Yeah, it seems to work ! I now have 2 screens with 2x2 panels.
I'll just have to find how to have 2 different cubes... Thank you very much.

But still, if someone has the solution to make it work with "separate x screen", I would like it even more... and the solutions to erase the multiple mouse pointers.

edit : no way to activate compiz ! It says that "the composite extension isn't available" ! So I can have only 2 desktops, the 2 screens being changed at the same time when I switch desktop.
I think I'll go to bed (1 am here) and keep on trying to fix this tomorrow.

---

### Post by aze555666 on 2009-04-25
I tried some things and it will maybe solve my problem
- separate x screen + xinerama -> separate x screen is ignored, it works as a twinview, the desktop being 2screens wide ... I can add panels to the 2nd screen, but the apps still run on the 1st one, plus switching desktop switches it one the 2 screens at the same time -> if I run GW fullscreen on my main screen, then try to run something on the other one, the new app runs under the gw. I have to move gw to 2nd desktop, then drag the new app to 2nd screen (1st desktop) then get gw back to 1st desktop so that gw and the other app are displayed together. I just hate that, I would like my real separate x screen back, with independant desktop switching. Plus, it is impossible to use compiz ("searching drivers ..." (I use nvidia 180, and they are activated...) -> "extension xxx isn't available" -> effets arnt activated)

-> I went back to separate x screen without xinerama. Of course, my main screen was black BUT I fould soemthing in terminal : I typed x +double tab and found a command called "x-window-manager" . The option --replace get my display back, and I have 2 screens working ... but not as expected : I have 2 separate X, but I can't get compiz back (before x-window-manager --replace, compiz was working properly on my 2nd screen with the options I had before upgrading to Jaunty). Now if I try to activate effects, it says they can't be activated. So it would be cool to find another command which restarts the window managers properly instead of replacing them with "metacity" (dunno exactly what it is, it's what the x-window-manager --help says). Another problem is that everything runs on the 1st screen regardless on which screen I click on a shorcut ! (It worked with gutsy and hardy, the problem began with intrepid but wasn't realy annoyous, and with jaunty it's horrible : only alt+f2 lets me open something on the 2nd screen). Since I use separate x screen, I can't drag a window from a screen to another.

edit : I reboot computer and I can see that the replacement of the window manager by metacity is still there : I have my separate x screen, 2 screens working (ie the 1st one isn't black), and can't activate compiz.

---

### Post by Haise on 2009-04-25
> **smokyink said:**
> Hi thats my first post in this forum and i think i can help you...
Here is how it works for me:

Open Terminal and write:
**[COLOR=black]"sudo nvidia-settings"[/COLOR]**[COLOR=black]
that opens the Nvidia X Server Settings menu

click on: >X Server Display configuration > Display > Configure...

than: check TwinView

click OK

than click :Save to X Configuration file

Save.

Quit and restart

[/COLOR]Windows and stuff open in proper screens
no mouse in both screens
you can move windows from one screen to another freely and so on...

Sory if i misunderstood and just lost your time

I have more than two monitors.  Twinview is a nonstarter for me, and so is xinerama/xRandR until they get fixed to handle multiple devices.

---

### Post by Haise on 2009-04-25
> **aze555666 said:**
> 
edit : I reboot computer and I can see that the replacement of the window manager by metacity is still there : I have my separate x screen, 2 screens working (ie the 1st one isn't black), and can't activate compiz.

Xinerama won't work dual-head (i.e, across multiple devices) with compiz.  This is normal, expected behavior.  It was supposed to be fixed with the RandR extensions in 1.6, but they pushed it back.

That's pretty much why I'm running it the way I am, but that implementation seems grossly broken by Jaunty.

---

### Post by aze555666 on 2009-04-25
I knw xinerama dosn't work with compiz, but i'm not using xinerama anymore.
I just have "separate x scree" without xinerama, and typed "x-window-manager --replace" in a terminal, which replaced my window manager with metacity, which enables my 1st screen (no black anymore)
But I think i've understood someting : the cube extension in compiz makes my 1st screen crash for a reason I ignore, that's why it was black. How did I know that? I installer fusion-icon (discovered by reading some other topics in thos forum) , which can take back compiz as a window manager instead of metacity (or restart the window manager). The first time it worked, then I tried to activate the cube and the 1st screen crashed ... I had to reboot my PC (metacity came back automaticaly) and now if I try to activate fusion-icon (alt+f2 -> fusion-icon), the 1st screen crashes ... i'm about to try to activate compiz with fusion-icon after having unactivated that cube.

edit : it worked : now I have my separate x screen with compiz ... but it's a bit comlicated, i'll have to do many things after each boot : normal boot + alt+f2 + fusion-icon + reload window manager ! 
Does someone know how I can reverse the effect of the command I typed (x-window-manager --replace) ??? Since I fixed the issue that mde my 1st screen black when using separate x screen with compiz, I don't need to use metacity anymore, so I would like to set compiz as the default window manager, so that i won't have to use fusion-icon after each reboot !

---

### Post by trudnai on 2009-04-25
I have some workaround about the menus. Once again, the problem is that when I start an application from the Application menu then the window opens up in the :0.0 screen no matter whcih screen I was using.

I have downloaded Opera web browser and it works correctly. It turns out that actually they use a bash script to start the application so I had a thought and it seems to be working. If I edit a menu item and put a 'bash -c' in front of the command then the application opens up on the correct screen.

Now have to find an easy way to replace all menu items to that or it also might help to find the problem and fix it.

---

### Post by aze555666 on 2009-04-25
This bug has be reported : [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783)

Thank you very much for the command making the app runing on the right screen, I'll try it as soon as I can .
In order to put it in all menu items, the best way would be to edit the config file for the menu ... i'm currently searching. It would maybe be possible to use a search+replace or make a script.

edit : found some menu-related files in my home folder, but they target files somewhere else in the system, that don't contain what i'm searching for (the commands to launch the apps).
BUT, I fould /home/ME/.gconf/.desktop/gnome/session/required_components/%gconf.xml, which seems to contain the defauls window manager : I replaced "metacity" with "compiz", hope it will cancel what I made by typing "x-window-manager --replace" ... i'll see that after next reboot. Oddly, the default window manager set in /home/ME/.gconf/.desktop/gnome/applications/window_manager/%gconf.xml was still compiz, even if I know the default manager was set to metacity (which runs when i reboot).

edit again : I fould /usr/share/applications : it's a folder where there are files which describe the menu items ... BUT I don't think they are the menu items for the user (they mush be default ones) since there are files belonging to root and we don't need password to modify the menu, plus I tried to modify a menu and edit the corresponding /usr/share/applications/xxx.desktop, and the modifications wern't there. Still can't find the place to edit the menus with a script :'( 
I'll keep on searhcing, cause I just tried your tip with bash -c, and it works.

edit : I tried to find the menu config files with command line (cause finding those files would make easy to make an automated add of "bash -c" everywhere) . I tried "ls -R | grep .desktop" -> nothing interesting, so either the menu modifications arn't saved in my folder or they don't use .desktop files as for the default menus. I tried "ls -Rl /usr | grep ME" and "ls -Rl /etc ME" to find the files that i own in those folders (I assumed the files in which my menu modifications are saved are files I can modify, so maybe files that i own) ... nothing interesting again . and google didn't help me : I found some possible paths for menu config files, but there are only paths that don't exist in unbuntu or the path to the default menu config.

---

### Post by trudnai on 2009-04-25
Hi,

Just written a small perl hack to change all menu items. You need to do that for each user though, or feel free to modify the script.

Thanks
Tamas

```
#!/usr/bin/perl

my $home = $ENV{'HOME'};
if ( not $home ) {
	$home = `ls -d ~`;
	chomp($home);
	die "Error: Could not determine HOME folder, try run this script from a terminal window" if( not $home );
}

my $glb = "/usr/share/applications";
my $loc = "$home/.local/share/applications";
die "Error: There is no \"$home/.local/share/applications\" directory" if (not -d "$home/.local/share/applications" );

printf "Creating local copy of the following menu items:\n";
opendir(GDIR, $glb);
foreach my $file ( grep { /^[^.].*\.desktop$/ && -f "$glb/$_" } readdir(GDIR) ) {
	chomp($file);
	if( not -f "$loc/$file") {
		print "  $file\n";
		print `cp \"$glb/$file\" \"$loc/$file\"`;
	}
}
closedir(GDIR);

opendir(LDIR, $loc);
foreach my $file ( grep { /^[^.].*\.desktop$/ && -f "$loc/$_" } readdir(LDIR) ) {
	chomp($file);
	# creating UNDO file
	my $i;
	for ($i = 0; -f "$loc/$file.undo-$i"; $i++) {}
	rename("$loc/$file", "$loc/$file.undo-$i") or die "Error: Could not create UNDO file \"$loc/$file.undo-$i\"";

	# modifying menu files
	open(IN, '<', "$loc/$file.undo-$i") or die "Error: Could not open file \"$loc/$file.undo-$i\"";
	open(OUT, '>', "$loc/$file") or die "Error: Could not create file \"$loc/$file\"";

	while(<IN>) {
		s/^Exec=(.*)$/Exec=bash -c \"$1\"/ if(not /Exec=bash/);
		print OUT $_;
	}
	close(IN);
	close(OUT);
}
closedir(LDIR);
```

Usage: 

1. Create a file menuFixer.pl in your home directory and copy the content from the code view above
2. Open a terminal window, and change the file te executable with chmod command
3. run the script

```
$ chmod 755 menuFixer.pl
$ ./menuFixer.pl
```

---

### Post by aze555666 on 2009-04-26
I read and exec that script , but it doesn't work: it creates in the folder in which the script is, a copy of the .desktop default (/usr/...) file and a modified one with the bash -c in it (so the file modification works)
1 odd thing :the script is meant to create all those files in $loc, which is /home/me/.local/share/applications . BUT the files are in the same folder than the script. I don't understand why.
I'll try to change the code the $ENV{HOME} with a /home/me .

edit : I just executed the script with a nautilus window showing the ~/.local/share/applications folder : all the files were created in it, and disappreared when the script was finished. I can't understand why, never used perl and don't know how the open/close operation in this language work. I'll just move the files. IT WORKS . Thank you very much :-)

---

### Post by trudnai on 2009-04-26
Hi,

Thanks for your reply. You have some odd problems. Did you run it from a terminal window or just clicked on the file from Nautilus?

The first problem (creating the files in the script's folder) might be related to that the $HOME environment was not set. It should have set by the .profile in your home directory when you open a shell (like when you open a terminal window).

With the file disappearing: That is really odd really. Sound like the files were created as temp files so that it was deleted.

Anyway, Just modified the script above a bit to put some error checkings and a bit better home folder determination. Also there was a bug in the folder usage around creating the undo files - fixed that one as well.

Thanks again!
Tamas

---

### Post by aze555666 on 2009-04-26
I just copied the code in  a file, made a chmod, then executed it from terminal.  .desktop files were created in the proper folder, then oddly moved to the script's folder ! Same behavior if I exec the script as you posted it previously or if I replace the $env{home} with "/home/me" in the script.
Don't understand either why it had this behavior, I just moved files from script's folder to right folder , and it worked (cd scripts; mv *desktop* ../.local/share/applications)
Now most things work exept for the fact that "bash -c" affectect the behavior of some apps : for example if I open a torrent with transmission from firefox, transmission doesn't open the window to add new torrent, I have to save the torrent file on desktop, then open it with "torrent -> add" in Transmission.

---

### Post by trudnai on 2009-04-27
> I just copied the code in  a file, made a chmod, then executed it from terminal.  .desktop files were created in the proper folder, then oddly moved to the script's folder ! Same behavior if I exec the script as you posted it previously or if I replace the $env{home} with "/home/me" in the script.

That is strange. For me it works no matter how I start the script. So even the `ls -d ~` does not work for you? Could you please check what is this one liner prints out? (type the command in a terminal window)
```
perl -e "print \$ENV{'HOME'} .\"\n\";"
```

> Now most things work exept for the fact that "bash -c" affectect the behavior of some apps : for example if I open a torrent with transmission from firefox, transmission doesn't open the window to add new torrent, I have to save the torrent file on desktop, then open it with "torrent -> add" in Transmission.

Yes, it can happen, unfortunately with this woraround that's how far I can go. Hopefully Ubuntu or Gnome developers will find the problem soon and then you can just delete those desktop files and everything will be back to normal.

---

### Post by aze555666 on 2009-04-27
the line returns "/home/ME" ...

---

### Post by trudnai on 2009-04-27
> **aze555666 said:**
> the line returns "/home/ME" ...

So it works, then I can't see what happens on your side. Could you please confirm that you have the second 'fixed' script that starts with the initialisation of the $home variable like this: 'my $home = $ENV{'HOME'};' ... and then later on the script you have the correct 'rename' as 'rename("$loc/$file", "$loc/$file.undo-$i")' with the $loc everywhere in front of the $file variables?

---

### Post by aze555666 on 2009-04-27
As I said, even if I replace the $env in the older version of the script with the real path, the behavior is the same, so the cause isn't the vairable containing the path (plus , the files are written in the right folder, they  are just moved when the script stops.
I think it comes from the imlementation of open/close in perl, there should be something that make the files created after opening a dir move in the script's folder when you close this dir.

---

### Post by trudnai on 2009-04-27
I think it is more with the first version of the script which had this kind of bug -- sorry about that. I used this rename function but forgot the $loc variable in front of the $file, so that after it copied the menu files into the right folder then it moved into the current one (aka the script's folder) with the '.undo-0' extension. But this problem fixed in the new version and according to my tests it works as expected.

Now I have no idea what to do -- unless writing a 'debug version' of this script to print out messages where the program flow goes and what values the variables are getting.

---

### Post by rijk.stofberg on 2009-04-30
I have another workaround.
Go to System >> Preferences >> Main Menu.
- this will start 'alacarte' menu editor
Find the menu item you want to change.
Click the 'Properties' button.
Change the command to use 'sh -c exec' to start the required application.
example:
- Old Evolution entry: evolution --component=mail
- New Evolution entry: sh -c 'exec evolution --component=mail'
Close alacarte

The first one to change is obviously the 'Main Menu' item :)

---

### Post by trudnai on 2009-04-30
Hi,

> **rijk.stofberg said:**
> Change the command to use 'sh -c exec' to start the required application.

More or less that's what that perl hack do. It replaces the menu items with bash -c ... -- but I like that 'exec' :-) Actually you can modify the script very easily to insert your 'sh -c exec' solution instead of the 'bash -c' so that you do not need to modify all menu items manually one by one with that alacarte editor.

Tamas

---

### Post by cboling on 2009-05-06
For ad-hoc application launching, I found that you can also add the "Run Application" applet to a panel on the 2nd screen; anything (including menu items) run from that applet will appear in the correct display by default.

---

### Post by p_fr1968 on 2009-06-01
I recently bought a Benq G2400W to use it on a Ubuntu 9.04 together with my Laptop on a Twinview basis.
First the monitor could not acquire a VGA Signal (I use a Nvidia Geforce 8600M GT) at a resolution of 1680x1050 but when I changed the resolution to 1280x1024 everything works fine. For that I went into the nvidia control and set evrything up.
The driver is 180.44

Maybe this helps.

Peter

---

### Post by apcks on 2009-07-18
Ubuntu 9.04 twinview, got it to work.  

 1. Used Envy, to install nvdia driver in 9.04 and got it to work after entering this.  
 
2.
  sudo mv /etc/X11/xorg.conf xorg.conf.bak 
sudo nvidia-xconfig 
sudo nvidia-settings  

 These commands are from here [http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html?showComment=1248120263705#c7102946423319289664](http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html?showComment=1248120263705#c7102946423319289664) 

  Envy Link 
This helped  to get twinview to work with my DVI and VGA on nvidia TI4200.      
 
From Google search: Dual Monitors With Ubuntu ~ Linux Fanatics Over and over, I hear people asking me “how do I get dual monitors working in Ubuntu“. Well today, I will show you (note the video) how to make this easy ...t;
 link  [http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/](http://www.lockergnome.com/linux/2007/06/18/dual-monitors-with-ubuntu/)  
 
 Without using Envy, twinview went really really slow.  It also reset every time because i could not save the xorg.conf file because of a parse error which those commands fixed.

---

### Post by JTLJudoMan on 2009-07-29
What would be even better is if they got twinview to support rotating one of the two monitors.

Currently you can only do it with separate x-views... Which causes all sorts of problems... Such as not being able to use the graphics card to enhance your desktop experience.

---

### Post by VladimirCZ on 2009-07-30
I have noticed that some contributors of this talk could benefit from reading:
[http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html)
[http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-o.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-o.html)

---

### Post by tenjin1 on 2009-09-26
It seems to be a bug in gnome, but I got seperate X screens working but only with compiz turned off, if I turn it on I get a wide vertical black border on the far right on Screen1. I think this border will go away if you downgrade nvidia driver from 180 to 174.I think this is a seperate bug with nvidia driver 180, but not sure. Everytime I go back to 180 the black bar is there. I'm beginning to think maybe its something in gconf-editor that needs to be configured.

To get seperate X screens working you have to replace libglib2.0-0
 libglib2.0-0-dbg. Can find more info about that [here]("https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380")

---

