---
title: "Dual Monitor Dual Workspace"
date: 2008-08-13
forum: Desktop Environments
---

### Post by creporiton on 2008-08-13
Hi all.
I have a Dell 14.1 inch widescreen laptop with nvidia graphics card and a 15 inch tft monitor.
What I want is to set it up as dual monitor display such that I have two workspaces with one workspace on each display. Can anyone point me out to the right tutorial to get this set up.

I am sorry if this has been already discussed but I am a newbie to ubuntu and these forums.

Thanks

---

### Post by sillyxone on 2008-08-13
perhaps this is what you're looking for:
[http://ubuntuforums.org/showthread.php?t=826717](http://ubuntuforums.org/showthread.php?t=826717)

Basically, from that thread, I'd edit /etc/X11/xorg.conf, and modify the "Screen" section (add red text):

```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "lcddisp"
        Device          "Configured Video Device"
        DefaultDepth    24
[COLOR="Red"]
        SubSection "Display"
                Virtual 3120 1050
        EndSubSection
[/COLOR]
EndSection

```

3120 is the sum of both monitor's resolution width (1680 + 1280), 1050 is the max of the resolution's height (1050 > 800).

Restart X (Ctrl-Alt-Backspace), then go to System > Preferences > Screen Resolutions. From there, you can turn on/off one of your monitor, or turn on both cloned, or turn on both side by side (as in dragging windows from one to another).

The only downside to me is that my Intel 965 has a 3D buffer size of 2048x2048 so 3D Compiz looks weird if I have two monitors in side-by-side mode (3120px is way too big to fit on 2048px buffer).

Read that post for more detail.

---

### Post by creporiton on 2008-08-13
Thanks for the reply but it isnt exactly what I am looking for. I have managed to set up a dual monitor display with nvidia-config.
My problem is that I do not want the two monitors to be an extension of each other but two different workspaces. That is to say that if the number of workspaces I choose in gnome be 2, I want one workspace on each display with its own set of desktop icons and panels.

---

### Post by lesbianpenguin on 2008-08-14
any luck?... i was looking for this solution too

---

### Post by airtonix on 2008-08-15
on my nvidia 8800gt, nvidia-settings lets me choose an option called twinview. does exactly what you want.

---

### Post by creporiton on 2008-08-16
hi airtonix.
I have an 8400 gs card.
nvidia-settings offers twinview but I can only stretch the same workspace across the two screens, not different workspace on each of the screens which is what I want.

Still looking for an answer

---

### Post by creporiton on 2008-08-16
hello guys.
still looking for a solution

---

### Post by ad_267 on 2008-08-16
Exactly why do you want this?

I can't see what the difference is between this and twinview. I use twinview and I have added a second panel to the bottom of the other screen and added a window list to that. You can also add a menu and have the panels set up exactly the same if you want.

How is that different to having another workspace?

---

### Post by doas777 on 2008-08-17
ok, there are 2 ways to do dual monitors, one uses Twinview, and the other uses sepperate X screens, which sounds like exactly what you want. be warned however, you cannot drag apps from one screen to the other.  

you can configure these with nvidia-settings, though be sure to run with sudo. there are lots of tutorials available, so I would google it which ever way you want to go. 
I have a copy of an nvidia xorg set up for seperate x screens posted here:
[http://ubuntuforums.org/showthread.php?t=851626]("http://ubuntuforums.org/showthread.php?t=851626")

check it out, but please don't just copy it in blindly and expect it to work. for instance this one is geared toward a TV out.

hope that helps, and good luck.
franklin

---

### Post by richbl on 2009-01-25
Hello all,

Has a solution to this question been found?

I see some discussion around the original posters question, but no specific solution (or, if it's there, I don't see it).

To restate the question:

--I have two monitors (one laptop LCD and one external LCD)
--I want to assign one workspace to the laptop LCD, and one workspace to the external LCD

Is this possible?

This is not the same as twinview, xinerama, et. al., which "glue" together two displays into one very large display. 

Rather, I want to keep the monitors separate, and switch to them via X workspaces.

Thanks much.

rich

---

### Post by StanleySerbia on 2009-01-26
i was just thinking, how could you control it?
Two workspaces -> one keyboard and mouse, it could be tricky.
I've seen the same thing that you want, only in windows...
it could be done in ubuntu for sure!!!

---

### Post by jtliii on 2009-03-03
I understand exactly why you would want two independent workspaces.  I like to run apps full screen (not stretched across two monitors but full screen in one) and I hate messing with resizing.  I have certain apps I always load on a specific monitor and I like them full screen.  For example I run e-mail full screen on my right monitor and vi client full screen on my left.  No resizing of screens to make them fit.

Now that I have said that the resolution to this issue is fairly simple.  The key is to run the nvidia control panel with sudo.

1. Open a terminal (see I am doing it now.  This is open on the right and terminal on the left)
2. type "sudo nvidia-settings"
3. Enter your password
4. Select "X Server Display Configuration" (I am assuming both monitors are enable and that Twinview will stretch across them)
5. Select the "Configure" button
6. Select "Separate X screen)
7. Select "OK"
8. Select "Save to X Configuration File"
9. Reboot

Once you have rebooted you should have two independent workspaces.

If you don't run this with sudo and instead access it by System/Administration/NVIDIA X Server Settings then when you attempt to save the x configuration file you will be denied.

I just went through this and it worked for me.

---

### Post by Ng Oon-Ee on 2009-03-04
This depends what is meant by workspaces. In Ubuntu 'workspace' refers to the multiple-workspace model, most easily illustrated by Compiz' desktop cube (each face is one workspace).

With Separate X Screen configuration, its slightly different. Each monitor is a separate X Screen (or separate X Server), each with its own set of workspaces etc. The problem with that is, unlike Ubuntu workspaces, it isn't possible to transfer windows from workspace to workspace, and program switchers only list programs running on their own workspace.

I use separate X Screen myself, but its not necessarily what the OP and others want.

---

### Post by mackay on 2009-04-15
I agree, I don't think it is possible to every first workspace to monitor 1 and every second workspace to monitor 2...

BTW 1680(2) = 3360  :D

Anyway I thought I would just post my xorg.conf just in case it might help someone. I have dual 22 inch monitors with a nVidia 9800 gtx.

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Hope this helps!

---

### Post by Pasdar on 2009-05-14
I've been looking for a way to do this, but it doesn't seem possible. Having the ability to do this would be very useful. It sucks to have an extended screen. I'd rather have two workspace, the first one my monitor the second my TV.

---

### Post by roborend on 2009-10-02
Hi all,
I need to  do this too because of:

1- I have CRT monitor to do my works, 
2- I have a second large monitor To display advertisements in our shop, in behind of my head and forward to people who come inside from the door. 

then I can successfully install them by nvidia-settings as TwinView, there is no problem anything works nice.

an I can drag and drop windows between two screens.

but, if we can assign "X workspace 1" to "monitor 1"
and "workspace 2" to "monitor 2"

the switch from 1 to 2 can be faster and easier.

Thanks.

---

### Post by d0b33 on 2009-11-20
> **jtliii said:**
> I understand exactly why you would want two independent workspaces.  I like to run apps full screen (not stretched across two monitors but full screen in one) and I hate messing with resizing.  I have certain apps I always load on a specific monitor and I like them full screen.  For example I run e-mail full screen on my right monitor and vi client full screen on my left.  No resizing of screens to make them fit.

Now that I have said that the resolution to this issue is fairly simple.  The key is to run the nvidia control panel with sudo.

1. Open a terminal (see I am doing it now.  This is open on the right and terminal on the left)
2. type "sudo nvidia-settings"
3. Enter your password
4. Select "X Server Display Configuration" (I am assuming both monitors are enable and that Twinview will stretch across them)
5. Select the "Configure" button
6. Select "Separate X screen)
7. Select "OK"
8. Select "Save to X Configuration File"
9. Reboot

Once you have rebooted you should have two independent workspaces.

If you don't run this with sudo and instead access it by System/Administration/NVIDIA X Server Settings then when you attempt to save the x configuration file you will be denied.

I just went through this and it worked for me.

Tried this on karmic, no luck... still won't save to the xorg file when run as sudo.

Help would be appreciated.

Edit: got it working by installing the latest nvidia driver manually.

---

### Post by orngjce223 on 2009-12-06
> **jtliii said:**
>  2. type &quot;sudo nvidia-settings&quot;
  I think you're supposed to use gksudo for graphical dialog boxes and programs and such...?

---

### Post by m10 on 2009-12-15
I have the same issue [COLOR="Gray"](feature request?)[/COLOR].
The main problem [COLOR="Gray"](I think)[/COLOR] is that the virtual workspace switcher is buggy [COLOR="Gray"](/not feature complete)[/COLOR] in this regard.

I would like the switcher to behave in the following way with **any** dual [COLOR="Gray"](or more)[/COLOR] head setup [COLOR="Gray"](be it separate X screens,xinerama,xrandr,bigdesktop,twinview, etc etc)[/COLOR]:

[LIST]
[*]it should setup [COLOR="Gray"](at least)[/COLOR] **a row of virtual workspaces for each screen**.
[*]**all workspaces** should be **visible from all screens** as to enable drag&drop in the switcher from one screen to/from another.
[COLOR="DimGray"]or,said in another way, all switchers, regardless of the screen they are placed on, should display and control all workspaces of all screens.But they should not "sync" the switching of workspaces from different screens, instead they should be able to switch them independently[/COLOR]
[*]each screen should be able to have its own **independent number of workspaces** [COLOR="Gray"](columns/rows)[/COLOR]
[*]it should **remember** the last multi-display **configuration** [COLOR="Gray"](e.g. after unplugging and replugging the additional screen(s) or a restart)[/COLOR]
[/LIST]
I made a little simple scheme for this to be as clear as possible [COLOR="Gray"](see attachment)[/COLOR].

This seems the obvious way [COLOR="Gray"](to me)[/COLOR] to handle workspaces on a multi-display setup and lots of people seem to have issues with the current way.
There are lots of [COLOR="Gray"](as old as from 2007)[/COLOR] bug reports across launchpad and gnome bugzilla but they are all confusing/messy [COLOR="Gray"](suboptimal descriptions)[/COLOR] and I could not find any solution or workaround.

launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/110899]("https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/110899")

For reference I am using Twinview on a dual head setup with an Nvidia 8600GS.Using the 190.42 binary-only driver on Karmic.

---

### Post by spiritofelric on 2010-01-14
This is a feature i'd be very interested in having (alternate workspaces able to display on different monitors).

jtliii: I know how to setup separate x screens; however, everything displayed must be setup in that screen, which is hard when the other monitor is not in front of you.  

Are there any work-arounds?  Is there any way to view an x-screen from another monitor?  Or toss applications from one x-screen space to another?

---

### Post by firfin on 2010-01-17
> **ad_267 said:**
> Exactly why do you want this?

I can't see what the difference is between this and twinview. I use twinview and I have added a second panel to the bottom of the other screen and added a window list to that. You can also add a menu and have the panels set up exactly the same if you want.
How is that different to having another workspace?

I don't think things like "move to workspace right/left" will work with this setup? Other than that this sounds like a solution that would work for me.

How did you set up the second panel and add the window list?

---

### Post by firfin on 2010-01-17
Gotta Love the forums ;-)

Found out how to add panel to the secondary display.

[http://ubuntuforums.org/showthread.php?t=1158627&highlight=adding+panel](http://ubuntuforums.org/showthread.php?t=1158627&highlight=adding+panel)

basically just add a panel (right-click an existing one) and then drag it (holding ALT )

---

### Post by mylesw on 2010-02-02
I have to add that having the ability to tie one or more workspaces to a screen in a multi-monitor setup like this is something I would kill for.  There are some 3rd party software programs in Windows that do this (Maxivista) but nothing in the Linux world I can see.  I love Workspaces as a concept.  Its a great way to compartmentalize what I'm doing.  But since I can put a couple of monitors on my rig, I like to be able to see each workspace on its own monitor and be able to move windows from one workspace to another.

If there is anyway this could be done, please tell me.  Otherwise what can we do to get this into upcoming releases?

Myles

---

### Post by ezzieyguywuf on 2010-02-23
I just want to chime in and say that I too would love to have this feature. Just like the guy in front of me said, having multiple workspaces is great, but being able to see them on multiple monitors and interact with either one is great.

---

### Post by kjano on 2010-05-05
i would also love if the Workspace Switcher could use multiple screens! For instance, the Show Desktop Button would only minimize WS 1 and you can still have a maximized window in WS2...

---

### Post by wantime on 2010-05-26
I'm also interested in this feature.  I would also like to be able to dedicate the first workspace as an overview workspace that sees all and is much the same as it is now.  By changing to the second workspace I would then be able to see it from the first screen, with workspace panel and control for switching windows between workspaces, and from the second screen (no panel required).  Ie, a monitor screen with the whole configuration in first/control desktop view connected to a screen cluster with only a workspace dedicated to each screen.

Does anyone know any work around for this style of configuration?

---

### Post by ceti331 on 2010-05-27
I'd like this too!

How about writing a switcher which iterates all the windows & rotates their Desktop Index if they're on the current screen. Can anyone whos worked with any of the code comment on what the most natural approach would be ?

I think you should default to 2 sets of workspaces when there are 2 monitors of different size, but for 2 identically sized monitors you should be able to show any pair of workspaces

Do any of the alternative/minimalist) window manages (fluxbox etc) handle anything like this.

Would it get too messy with windows that have been moved to stradle screens... would it be cleaner to disalow that and use a snapping scheme to keep windows entirely on one screen when shifting horizontally between monitors.. maybe clamp them to the screen they're most on when the switch happens

---

### Post by Paretje on 2010-07-31
> **jtliii said:**
> I understand exactly why you would want two independent workspaces.  I like to run apps full screen (not stretched across two monitors but full screen in one) and I hate messing with resizing.  I have certain apps I always load on a specific monitor and I like them full screen.  For example I run e-mail full screen on my right monitor and vi client full screen on my left.  No resizing of screens to make them fit.

Now that I have said that the resolution to this issue is fairly simple.  The key is to run the nvidia control panel with sudo.

1. Open a terminal (see I am doing it now.  This is open on the right and terminal on the left)
2. type "sudo nvidia-settings"
3. Enter your password
4. Select "X Server Display Configuration" (I am assuming both monitors are enable and that Twinview will stretch across them)
5. Select the "Configure" button
6. Select "Separate X screen)
7. Select "OK"
8. Select "Save to X Configuration File"
9. Reboot

Once you have rebooted you should have two independent workspaces.

If you don't run this with sudo and instead access it by System/Administration/NVIDIA X Server Settings then when you attempt to save the x configuration file you will be denied.

I just went through this and it worked for me.

This sounds intresting for me, but what about the keyboard and the mouse. As you run two diffrent x screens, I assume you need two mouses and keyboards. How do you make X wise so the one is only for this server, and the other for the other?

---

### Post by juska on 2010-08-14
> **Paretje said:**
> This sounds intresting for me, but what about the keyboard and the mouse. As you run two diffrent x screens, I assume you need two mouses and keyboards. How do you make X wise so the one is only for this server, and the other for the other?

You don't need multiple mice nor keyboards for this configuration. Keyboard works where the focus is and focus is controlled with mouse (which you can drag from monitor to other).
At least it works for me like this out-of-the-box on jaunty.

---

### Post by Tinka on 2010-08-31
Just thought I would chime in here. I run Awesome WM, [http://awesome.naquadah.org/]("http://awesome.naquadah.org/"), which does exactly what you are asking. By default you get 9 workspaces for each monitor. You can be on any workspace you want on either monitor at any time, as well as move applications back and forth between separate workspaces/monitors. This is a extremely productive setup that I think would be very beneficial for Gnome/KDE to implement.

Most of the tiling WM's, [http://en.wikipedia.org/wiki/Tiling_window_manager]("http://en.wikipedia.org/wiki/Tiling_window_manager"), include this functionality.

That said, if Gnome implemented at least separate workspace switching on multiple monitor setups and tabbing windows I would switch back in a second!

---

### Post by Pithikos on 2010-09-10
I would also love this! Bought a new TFT 23'' and I plugged it to my pc with my old 17'' TFT. Tryied both seperate x and twinview but nothing pleasures me. The twinview makes the workspaces on the panel down, look extremely long. It's very impractical also as for example if you want to change workspace you maybe want to still keep the old one in the other monitor.
The cons with seperate x are quote obvious. It's just like having two different computers. I get the feeling like if I open firefox on one monitor I have to do the same on the other :p

 Would be cool if each workspace could have its own monitor. Can't be that hard to make reality :KS

---

### Post by Nythain on 2010-09-10
this hasnt been answered yet?

gkus nvidia-settings
Xserver display configuration
on the right... Configuration <configure>

Seperate X screens is what you want... that will load each monitor as its own X screen, its own panel, its own backgrounds, etc

this can also be done in the /etc/X11/xorg.conf by setting up the two devices and the two monitors setting up 2 screen sections instead of just one screen using both devices and monitors

---

### Post by nualp on 2010-09-19
I do not know if that is what they were looking for however i have looked at several other postings on other forums but they are not looking for this. Here is a list of traits i believe all these people are looking for

1) set up for two monitors 
2) one workspace per screen
3) ability to move items from one screen to the other easily by telling it to move to the other workspace
4) not twinview or separate x servers

If anyone knows how to write the xorg.conf to set the screens up like this please help i do not have as much experience as i would like in writing this type of code or know how to set this up like this.

---

### Post by hrickh on 2010-09-20
> **nualp said:**
> I do not know if that is what they were looking for however i have looked at several other postings on other forums but they are not looking for this. Here is a list of traits i believe all these people are looking for

1) set up for two monitors 
2) one workspace per screen
3) ability to move items from one screen to the other easily by telling it to move to the other workspace
4) not twinview or separate x servers

If anyone knows how to write the xorg.conf to set the screens up like this please help i do not have as much experience as i would like in writing this type of code or know how to set this up like this.
Using a combination of System/Preferences/Monitors and CompizConfig Settings Manager you can accomplish all these fairly easily.

R.
==

---

### Post by mcbiff on 2010-09-20
[quote="Tinka"]Just thought I would chime in here. I run Awesome WM, [http://awesome.naquadah.org/](http://awesome.naquadah.org/), which does exactly what you are asking. By default you get 9 workspaces for each monitor. You can be on any workspace you want on either monitor at any time, as well as move applications back and forth between separate workspaces/monitors. This is a extremely productive setup that I think would be very beneficial for Gnome/KDE to implement.[/quote]

How do you do this with awesome? It has the same problem GNOME does, i.e. you can't share tags/workspaces. For example, you can't view screen 2's tag 1 on screen 1.

---

### Post by Sean Hayes on 2010-09-20
> **hrickh said:**
> Using a combination of System/Preferences/Monitors and CompizConfig Settings Manager you can accomplish all these fairly easily.

R.
==

How? Nobody else seems to have an answer. I've looked through the CompizConfig Settings Manager and didn't see anything about moving windows between multiple desktops.

---

### Post by corcomp84 on 2010-09-20
I dont know how much this will help you but you can open multiple X-servers. weather you can get your monitor to see them as separate is another story but you might find it interesting.. hit alt+Ctrl F8  then log in using your user name and password.. then type ( startx -:1 vt8 ) this will start another season which you can change from by using alt+Ctrl F7 or alt+Ctrl F8.. However I dont know how simple it would be to connect the two.. you might be able to change the default monitor under each different session but I am not sure its just an Idea.. sorry if its a dead end..

---

### Post by corcomp84 on 2010-09-20
also did you try the desktop cube.. U can have lots of workstations with that, granted its all on the same monitor but all you have to do to change work station is alt+ctrl Right or Left with the arrow keys.. It sounds like that would work for you..

---

### Post by happyzapp on 2010-10-10
[SIZE=2]Well, not sure what most here are trying to achieve. I am running Karmic with Nvidia 9600 on Toshiba laptop (5 years old).

I have my external Samsung monitor above my laptop monitor. Using TwinView option. I made the Samsung the primary display for the X screen. When I set it up I used position 'Top'. The screen on my laptop has position 'absolute' and the checkbox for primary display is unchecked.

Now with this configuration my main panel is in the Samsung screen. The laptop screen is totally void of anything. I can open programs and just drag and maximize to that screen. I can switch between workspaces (have four of them) and everything works just fine.

To do all this I had to start with a clean, minimal xorg.conf file. This thread may help:[/SIZE]

[http://awesomelinux.blogspot.com/2009/11/ubuntu-910-karmic-nvidia-settings-parse.html#comment-form](http://awesomelinux.blogspot.com/2009/11/ubuntu-910-karmic-nvidia-settings-parse.html#comment-form)

[SIZE=2]I posted there but continued on my own and am to this point.

Now what I have to do each time I wish to change my settings is to overwrite my xorg file with the default setting. Sometimes the 'merge with existing file' feature, even when unchecked adds more to the file mixing things up. A pain but only work around which works for me at moment.

Anyway, once you have a generic xorg file reboot, go to terminal and type sudo nvidia-settings. This will bring up your Nvidia Server Settings. Make all your adjustments as you desire, click apply and see what happens. Should you get your effect, apply before it times out and click to save settings. Your terminal 'should' not come up with any errors. Hit quit and the terminal should go back to command line. Reboot to see if the settings took. 

Should you have what you set then go back to terminal and again type in sudo nvidia-settings. You Nvidia Server Settings dialog box should appear. Just quit and you are set to go.

[I]Note: Every time you need to change your settings you will need to use the terminal route. Trying from the panel is not root. You will come up with all kinds of 'parsing' and 'cannot save' problems due to not being root.
[/I] 
This is what my current settings look like:
[/SIZE]

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+900"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

[SIZE=2]I am now trying to figure out how to save workspace settings so programs initialize in the same workspace they were used during the previous session. That is still on my plate.

I hope this helps in at least getting two independent screens happening for you. It has increased my productivity. You need to play around with it a bit.

Have fun.

Jeff.[/SIZE]

---

### Post by S_V on 2010-11-06
Thanks for your help! Dual monitors with dual workspace works for me fine (by sudoing nvidia-settings and setting two separates monitors). 

I have a problem though with controlling brightness after this set up. The fn-key works when I use only one monitor, it fails after using two separates (the change bar is visible, but brightness it not changing).

Anyone can help with that?

---

### Post by sandikaxp on 2010-11-15
this is the same problem that I have. can we put two separate workspaces in two deferent monitors. with out stretching the same workspace

---

### Post by Hyvi on 2010-11-28
HI, I has the same problem .   I don't want to stretch every workspace .

---

### Post by TeeRoy32 on 2010-11-29
hi i'm usind lucid 32bit with a geforce 6600 i have two screens a 17" monitor and a 22" high def wide screen lcd tv i have seperate x servers per screen working but in one the wide screen 22 " i start xbmc so i can watch my high def videos wich don't work very well for me even in vlc so xbmc is my only option. the only problem is when i have xbmc running i can't exit back to my other screen so i can surf the net and do my work. is there a button short cut combination to get my mouse back to the 17" or any other work around. i have some ability with the command line and am very capable of cutting and pasting to edit config files.

cpu 3.0ghz p4
2gb ram
256mb g6600 pcie

---

### Post by cheetos316 on 2010-12-11
So I'm guessing that there hasn't been a definitive solution to this yet?  I am pretty new to Ubuntu and would love to see this type of functionality.  If there is a solution, can someone explain step by step?  Also, it seems that all of the posts have talked about Nvidia gpus and TwinView.  What about other gpus?  I am (sadly) running an Intel gpu at the moment.  Is there a way to do it universally?

---

### Post by herasheron on 2010-12-15
Hi,
I have a Sony laptop and a Samsung monitor with a much better resolution than the laptop. Ordinarily I just leave the same image in both monitors so I can have the desktop menu available. If I switch to the Samsung monitor and switch the resolution my menu stays on the Sony monitor and the windows are open only on the Samsung monitor. The Sony does not seem to have any Nvidia controls so the Nvidia info is useless to me. HOWEVER, the Monitor Preferences window stays open on the Samsung monitor when I switch to it. If I close that window I lose control of which monitor I can use. I could just leave that window open to be able to switch back and forth. 

Does anyone know what the command would be to restore the Monitor Preferences window if it were closed?

The OS is Ubuntu 10.10 running with a gnome desktop.

---

### Post by vikat on 2010-12-15
I use Jupiter to easily adjust the monitor preferences. It has some other useful options too. It's prefect for laptop usage.

[http://auroraos.org/project/jupiter](http://auroraos.org/project/jupiter)

EDIT: Better link.

---

### Post by lambroger on 2010-12-20
> **vikat said:**
> I use Jupiter to easily adjust the monitor preferences. It has some other useful options too. It's prefect for laptop usage.

[http://auroraos.org/project/jupiter](http://auroraos.org/project/jupiter)

EDIT: Better link.

That link goes to AuraOS and a description page telling about *Jupiter*. Unfortunately they don't have a link for us to download the program.

---

### Post by burton247 on 2010-12-26
Can people stop hijacking this thread please.

I have been trying to this for a while too. Unfortunately I have not found a way to do this is gnome, well metacity to be more specific. 

It is possible, well default, in other window managers. For example Xmonad will automatically be set up like this, my external monitor will start with workspace 2 on it and my laptop will be 1. If my laptop screen is active and I chose for workspace 2 there they will switch. If I ask for workspace 3 it will change to that but the external monitor will still have workspace 2 on it. 

It is possible to integrate Xmonad into gnome, however, many people will probably not get on with it as it is very keyboard driven and a tiling window manager. I used it for a while but use normal metactiy again mainly. 

I think we people wanting to so this will have to use an alternative window manager. I will try and find out what mangers allow this functionality or find a way for metacity (or mutter) to do this. If I find anything I'll post it here

---

### Post by S_V on 2011-01-11
> So I'm guessing that there hasn't been a definitive solution to this yet? Isn't it already resolved?

Did u read this thread or am I missing smth u want to do? 
Setting (as root) 2 monitors as separate works for me fine (2 x 8 workspace), isn't it what you want to do?

---

### Post by jabalsad on 2011-02-04
> **S_V said:**
> Isn't it already resolved?

Did u read this thread or am I missing smth u want to do? 
Setting (as root) 2 monitors as separate works for me fine (2 x 8 workspace), isn't it what you want to do?

Can you move windows between a workspace on the one monitor and a workspace on the other monitor?

---

### Post by The Linux Cynic on 2011-02-04
What is the goal behavior?

Two [gnome workspaces]("http://library.gnome.org/users/user-guide/2.29/overview-workspaces.html.en"), each one being displayed at the same time, on two different monitors. How is [switching]("http://library.gnome.org/users/user-guide/2.29/gosoverview-41.html.en") between them controlled? That is, what determines where mouse&keyboard focus is? The same way as it is now?

What advantages does this have over using a two X servers, one per monitor?

---

### Post by burton247 on 2011-02-06
Basically whatever workspace your active window is on is what workspace your mouse and keyboard are binded to. A lot of tiling managers support "sloppy focus" so you could say whichever monitor your mouse is on.

The advantage is easier to see when the windows are tiled. say I have 4 workspaces, internet, code window, gimp and music - roughly.

If I have this set up on gnome say the first workspace has internet on one monitor and code window on the other. Then the other two things in another workspace using both the monitors. If I'm coding but need to work on a graphic then I have to switch workspace, this means my code window and internet have both gone and I have gimp and music. Not that useful.

What we are talking about is being able to switch the interent workspace for the gimp one. Then I can have the code in front of me. Or switch out the code for gimp and be able to get look at graphics online or something. 

The seperate Xserver doesn't allow drag dropping. Also I can have something on mon1 then switch it to mon2. This is more apparent if you have different size monitors. A document may be on a smaller screen (or internet) and a abiword doc on the other. So you can type or research something. But it is handy to be able to hit super+2 and have the internet workspace pop onto the bigger monitor and switch with the document. 

You can have say 8 workspaces and get any of them on any monitor at any time, just not have the same one displayed on both. And you can drag and drop windows between workspaces. It's so flexible and more productive in my opinion.

---

### Post by Ol' Craig on 2011-03-11
Burton, this is exactly what we are looking for!

It doesn't seem as though this would be all that difficult. 

I currently have two displays and 4 workspaces that are set to wrap around. The problem is that one workspace occupies both monitors.

Ideally, this set up would have the option to change half of a workspace, so that the right half of my current workspace moves to the left monitor, and the left half of the next workspace (to the right) appears on my right monitor.

---

### Post by jonyee7 on 2011-04-09
Burton. I get what you mean.
I'm new to ubuntu, in face i haven't gone ubuntu yet. I'm trying to find a free OS to work on my HP mini. And ubuntu is perfect for that.

What i need from ubuntu is what burton needs as well. One workspace for one monitor.

In my case, i'm a teacher. And it is useful for me to have different workspace i can "work on".

I'd like to have one workspace on my desk and the second displaying on a projector.

Sometimes i want to prepare a lesson on the spot without the kids seeing part of it. And then dragging it over to the second workspace (Expo does that) to continue whatever work i have open there and just work from that workspace.

---

### Post by burton247 on 2011-04-11
Yet to find something that has this functionality. Well that's not strictly too, most tiling WM have it and there are probably some light weight WM that are feature rich, for example primarily floating but support tiling and tabs or something. But I can't find any extensions for metacity that do it. I asked a lecturer of mine who helps develop gnome and he didn't know of any. 

Could you not just do your lessons on one monitor anyway? then drag it over? If you like having multiple workspaces to plan your lessons and you want something visible on the screen for the kids all the time then you can right click the menu bar and set it to visible on all workspaces. Hope that may be of some use to you.

---

### Post by hakamade on 2011-04-13
I was also looking for a feature like this. I take it there isn't one for Gnome, at least.

I've got a display and a TV, which I (not surprisingly) use only for watching videos. On that note, it would be great to be able to configure audio output separately for each workspace. TV built-in speakers for TV workspace and display built-in speakers for the display.

The two have different resolutions, which is causing some problems for  me. I'd like to be able to configure the workspace(s) on each with its  own resolution. I don't think there's any need to move workspaces between screens.

---

### Post by ninjasinloaf on 2011-06-08
This is exactly what I expected would happen when I set up my shiny new second monitor.  

I sort of got what I wanted with separate X screens + Xinerama, but the desktop icons don't appear on both screens, it's a pain to switch between workspaces, when I minimize all the windows on one screen they ALL minimize, and I can never quite tell onto which screen an application will open.  Not to mention the trouble I've had duplicating the gnome panels from one screen to the other.  Now every time I log in the panels are all a-jumble (although I've somehow stopped the duplicate launchers from showing up on the main screen's panels.  I still can't get indicators (eg. for Dropbox) on both upper panels -- anyone got suggestions for that?)

At any rate, what you folks are suggesting, and what Burton has articulated is precisely what I'm after. I would like to be able to scroll between workspaces again.  They're very helpful for organizing/compartmentalizing my work.  I'd love to scroll workspaces from screen to screen, but I'm not sure if that's a practical hope when the resolutions are different (I have differently sized monitors).  As it stands, when I move a very large window from the big screen to the small screen (which is, I suppose, just the right half of the large screen) it doesn't get resized proportionately.  Would this be different if the second screen held another workspace?  What I mean is, could moving a window from Screen1/Workspace1 to a smaller Screen2/Workspace2 rescale the window appropriately?

---

### Post by s-p-n on 2011-07-10
I can't believe there's no way to do this yet... 
[U][I][B]
[burton247]("http://ubuntuforums.org/member.php?u=605134") hit the desired functionality on the head with a hammer.[/B][/I][/U]

Please Lord, LET THIS FEATURE BE THE DEFAULT IN Ubuntu 11.10/12.04!!!

---

### Post by jpthompson23 on 2011-09-06
I'm just adding that I would also like this functionality and I was surprised when I set up my second monitor and, instead of seeing workspace 1 on the primary and workspace 2 on the secondary, I just saw a stretched desktop across my two monitors.

How has this feature not been implemented yet??? It is so intuitive, so obvious, and clearly, very much in demand!

---

### Post by Ol' Craig on 2011-10-13
Just checking in on the status of this thread. I've gotten quite used to using a single workspace spanning two desktops, but the aforementioned functionality would be nice.
Also, it would be nice if different workspaces could, in fact, be different. Such as different desktop icons.

---

### Post by Luke490 on 2012-02-07
I'm just a beginner in Linux, been using Slackware 1997, then Ubuntu 2003, and back 2010. 
  
;) But this window manager for X might be what you want... [http://awesome.naquadah.org/](http://awesome.naquadah.org/)

---

