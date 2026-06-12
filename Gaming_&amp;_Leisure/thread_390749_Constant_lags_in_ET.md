---
title: "Constant lags in ET"
date: 2007-03-22
forum: Gaming &amp; Leisure
---

### Post by 1/0 on 2007-03-22
I realized after some 4 years with Gentoo that I spend too much time updating and configuring. So I decided to switch distro and now I've got Xubuntu installed and working. So far its been a good experience though I'm used to having all apps in the installer.

Anyway, here's my problem. I installed enemy territory 2.60 from a binary. The install went smooth but when I started playing I got lags every 1-2 minutes for about 20 seconds at a time. That spells out: impossible to play. 

These are my specs:

Compaq Presario 8440EA Desktop
P4 1.8 GHz
512 Mb RAM
400 Gb HD (Seagate 200 Gb Barracuda 7.200.10 and 7.200.9)
Nvidia Geforce Ti200
SB Live 5.1
Xubuntu Edgy

I'm not having any errors in dmesg, no messages in /var/log/messages, no errors on the ET console. Glxgears works fine (except I'm not getting any numbers/fps but I guess that's distro specific):
```
$ glxinfo |grep direct
direct rendering: Yes
```

This is really worrying me since it could be anything, including hardware error. So, I really need some help figuring out what's the problem or even what's not the problem.

---

### Post by frodon on 2007-03-22
First thing is that it could be related to you ET settings and the server where you play.

Try to ping the server where you play to see if you have a decent ping, then in game open the console and type /rate it should give you back the value you have for this variable, a decent rate is 20000 or 40000 if your value is under this then set it to 40000.
Look also if the server where you play use punkbuster which is an anti-cheating software and is known to generate some problems when you don't have an up to date version.

---

### Post by 1/0 on 2007-03-23
Thanks for the reply. I get the same symptom on all/several servers. I tried a non-punkbuster server and got the same symptoms. My ping is usually around 35 - 50. 

I didn't know about rate; mine is 25000. What does that measure? 

I guess that rules out a few errors?

---

### Post by frodon on 2007-03-23
Hum, if you get the same problem everywhere then the problem is surely elsewhere. About the  rate 25000 is good, players who have a low rate value in their ET config may issue some ping problems from time to time but this is not your case with a rate of 25000.
And if you start the game in terminal, do you see some error output after closing the game and parsing the log ?

---

### Post by 1/0 on 2007-03-23
There are no error messages in terminal. Just the regular

```

Sys_LoadDll(ui) found **vmMain** at  0xae2c1f40  
Sys_LoadDll(ui) succeeded!
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

I'll try to install AA to see that its not all online games. I guess that's not in synaptic either... Man, portage was good in Gentoo!

---

### Post by frodon on 2007-03-23
Could you post here you xorg.conf just in case ? and what about your internet connection, is it fast and reliable ?
Other possibility is firewall, if you have one check that you are not blocking one of the ports used by ET.

---

### Post by 1/0 on 2007-03-23
I've got an ADSL 8/1 mbit connection behind a Smoothwall firewall but I'm not sure which ports should be opened. One should never trust anything but the connection has been good before. I moved my computer a bit further away but I've checked with an extra cable that the cable is good. I'm downloading files fast. 

Here's the config:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "COMPAQ S920"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Monitor        "COMPAQ S920"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by frodon on 2007-03-23
Your xorg looks good for me.
About the firewall ET uses the port from 27950 to 27970 with udp protocol, check that you don't block the udp traffic on these ports.

---

### Post by asipi on 2007-03-26
Hi Boys,

(hello frodon, I am RifleRat :) )

I also had problems with this type of lag "ages" ago :) but I found some processes in my system, here what I did (could be that similar causes you have too):

There are some tasks what regularly run in *ubuntu distros, but could be happen that some of them stucks due to an error and the distro maker doesn't know about it :(.

For the first check all the daemons running, try to stop some what are do not necessarry for your everyday work. By default I had smbd, mysql, etc. because they put themselves in the startup sequence when I installed them.

2nd: Check crontables and the /etc/cron.* direytories check if you have something unuseful in them.

3rd: install htop package it is a very good alternative for the standard top, and paralelly start it when you started et, and check what processes are starting and stopping during et runs.

You will find that pretty one which eats up resources... 

I had a stucked apt updater or whatever it called. My apt cache was damaged and it could not finish its update sequence and crashed all the time. Its controller realized it and started over it in every minute so I had about 2-4 secs lags in lagometer in every 20-40 seconds. It eated processor and disk resources not network, but from the playing point of view I realized "lag".

Hope it could help...
Please refer to us if you found your causes.

---

### Post by 1/0 on 2007-03-26
Well, I've opened the ports for UDP and I get the same problem...

As for processes, this is what I find.

```
 $ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:03 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   87 ?        00:00:00 kseriod
  120 ?        00:00:00 pdflush
  121 ?        00:00:00 pdflush
  122 ?        00:00:00 kswapd0
  123 ?        00:00:00 aio/0
 1751 ?        00:00:00 khpsbpkt
 1760 ?        00:00:00 khubd
 1765 ?        00:00:00 knodemgrd_0
 1862 ?        00:00:01 kjournald
 1941 ?        00:00:00 logd
 2088 ?        00:00:00 udevd
 2841 ?        00:00:00 shpchpd
 2845 ?        00:00:00 kpsmoused
 3013 ?        00:00:00 kgameportd
 3737 tty1     00:00:00 getty
 3739 tty3     00:00:00 getty
 3740 tty4     00:00:00 getty
 3741 tty5     00:00:00 getty
 3742 tty6     00:00:00 getty
 3953 ?        00:00:00 acpid
 4076 ?        00:00:00 dd
 4078 ?        00:00:00 klogd
 4150 ?        00:00:00 gdm
 4151 ?        00:00:00 gdm
 4162 tty7     00:34:58 Xorg
 4216 ?        00:00:00 hpiod
 4219 ?        00:00:01 python
 4267 ?        00:00:00 dbus-daemon
 4282 ?        00:00:03 hald
 4283 ?        00:00:00 hald-runner
 4289 ?        00:00:00 hald-addon-acpi
 4300 ?        00:00:04 hald-addon-keyb
 4304 ?        00:00:00 hald-addon-keyb
 4313 ?        00:00:00 hald-addon-keyb
 4316 ?        00:00:00 hald-addon-keyb
 4325 ?        00:00:01 hald-addon-stor
 4327 ?        00:00:05 hald-addon-stor
 4347 ?        00:00:01 dhcdbd
 4364 ?        00:00:00 NetworkManager
 4379 ?        00:00:00 NetworkManagerD
 4407 ?        00:00:00 perl
 4495 ?        00:00:00 atd
 4508 ?        00:00:00 cron
 4577 ?        00:00:00 dhclient
 4621 ?        00:00:00 dhclient3
 4630 ?        00:00:00 sh
 4661 ?        00:00:00 ssh-agent
 4664 ?        00:00:00 dbus-launch
 4665 ?        00:00:01 dbus-daemon
 4671 ?        00:00:01 xscreensaver
 4674 ?        00:00:01 xfce4-session
 4679 ?        00:00:01 xfce-mcs-manage
 4681 ?        00:00:00 gnome-keyring-d
 4683 ?        00:00:00 gconfd-2
 4685 ?        00:00:04 xfwm4
 4687 ?        00:00:04 xfdesktop
 4689 ?        00:00:06 gam_server
 4694 ?        00:00:09 xfce4-panel
 4696 ?        00:00:04 nm-applet
 4698 ?        00:00:04 nm-applet
 4700 ?        00:00:04 nm-applet
 4701 ?        00:00:02 xfce4-mailwatch
 4702 ?        00:00:25 xfce4-cpugraph-
 4703 ?        00:00:21 xfce4-netload-p
 4704 ?        00:00:02 xfce4-mixer-plu
 4705 ?        00:00:00 thunar-tpa
 4710 ?        00:00:00 Thunar
 5435 ?        00:00:00 syslogd
 5832 ?        00:00:00 xfrun4
 6416 ?        00:00:00 gnome-vfs-daemo
 6526 ?        00:29:44 firefox-bin
 6539 ?        00:00:00 netstat <defunct>
 7113 ?        00:00:00 cupsd
 7165 tty2     00:00:00 getty
 7199 ?        00:00:00 xfce4-terminal
 7201 ?        00:00:00 gnome-pty-helpe
 7202 pts/0    00:00:00 bash
 7218 pts/0    00:00:00 ps

```

Crons are:

```

$ ls /etc/cron.daily/
0anacron         bsdmainutils     man-db           standard       apport
chkrootkit    sysklogd             apt              find.notslocate  prelink          
aptitude         logrotate        slocate  

$ ls /etc/cron.hourly/

$ ls /etc/cron.weekly/
0anacron  man-db  popularity-contest  sysklogd

$ ls /etc/cron.monthly/
0anacron  scrollkeeper  standard

```

The only cron script I've added is prelink. I'm not sure how to use htop. It seems much similar to the regular top.

---

### Post by asipi on 2007-03-26
start et on a separate X server, and connect to a game server as spectator. it will be on virtual terminal 8 or 9 depending on your system settings, then switch back to your desktop with ctrl+alt+F7. then open a terminal and start htop. switch back to et with ctrl+alt+F8 or F9 and put lagometer onto your screen and watch for lags. you should see red lines in the lower running green line. when you realized how often the lag occurs, switch back to your desktop and monitor htop. Look the firstsome processes. if regularly you can see the same process jumping to the first 1-3 processes then that will be a problem. try to write down the name of the program and start search the cause of its running.

I am using a small script to start et on a separate X server I will post it from home (because I am at workplace now :) ) if you could not manage it.

something similar you need:
xinit -- /usr/local/games/enemy-territory/et :1 >/dev/null

if  you do not see red lines in your lagometer, that would be another type of problem...

good luck, see ya later

---

### Post by asipi on 2007-03-26
here is the script I promised:
```
ati@atihome:~$ cat /usr/local/bin/x.et
## Start another X server, pipe anything not returned by et to /dev/null (otherwise
## something presses enter until we kill the terminal we executed it from
xinit /usr/local/games/enemy-territory/et $* -- :1 > $HOME/x.et.log
```

to start another X server first you have to set this in your /etc/X11/Xwrapper.config file:
```
allowed_users=anybody
```

as I remember could happen that gdm blocks the starting of another X, if so plz dig in the forum, because I don't use gdm, I am a Kubuntu user wich uses kdm as default display manager. (something magic-cookie authorization could need I guess)

If you will not find a suspected process regarding the lag thingy, we should examine your network environment (devices, net type, etc.)

---

### Post by frodon on 2007-03-26
Full instructions here (nice script riflerat ;) ) :
[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

---

### Post by 1/0 on 2007-03-27
I didn't know about the lagometer, I thought it was a joke but google told me otherwise. I'm getting big red histograms, so yeah, I'm lagging. 

I'm having somewhat difficulties seeing exactly which process causes this. When I finally end up in vt7 the lag is over but the top one is either ./et.x86, X :1 or /usr/bin/X:0 -br -auth /var/lib/gdm:o.Xauth -nolisten tcp vt7.

---

### Post by asipi on 2007-03-27
how about the upper blue line in lagometer?
do you have a shared network connections?
do you have firewall or net packet optimizer installed?
do you use a router?

do you use a personal autoexec.cfg to start et with?

give me your videoram & swap-size
OK I found some details in a previous post about your hardware:
P4 1.8 GHz
512 Mb RAM
400 Gb HD (Seagate 200 Gb Barracuda 7.200.10 and 7.200.9)
Nvidia Geforce Ti200
SB Live 5.1
Xubuntu Edgy
^^^^^^^^^^^^^^^^^^^
these are not sounds to "good" some graphic tweaking need sure in et

attach your etconfig.cfg from ~/.etwolf/etmain/profiles/your_profile/

and finally give me wich server you try to gaming on or is it a problem on all servers?

---

### Post by 1/0 on 2007-03-28
The blue line doesn't change much at all. Sometimes I get blue and yellow spikes, yet smaller and not always at the same time. 

I've got a shared connection via a Netgear GS105 switch and a Smoothwall firewall (P3 600/256). I'm not using any network package optimizer (that I know of). There are three computers on the network but they are usually turned off when I try to play. This problem occurs on all servers. 

I'm not using any autoexec.cfg to start et. 

Here's my etconfig.cfg from my profile
```
// generated by ET, do not modify
unbindall
bind TAB "+scores"
bind ESCAPE "togglemenu"
bind SPACE "+moveup"
bind , "mapzoomout"
bind - "zoomout"
bind . "mapzoomin"
bind 0 "weaponbank 10"
bind 1 "weaponbank 1"
bind 2 "weaponbank 2"
bind 3 "weaponbank 3"
bind 4 "weaponbank 4"
bind 5 "weaponbank 5"
bind 6 "weaponbank 6"
bind 7 "weaponbank 7"
bind 8 "weaponbank 8"
bind 9 "weaponbank 9"
bind = "zoomin"
bind ` "toggleconsole"
bind a "+moveleft"
bind b "+zoom"
bind c "+movedown"
bind d "+moveright"
bind e "+leanright"
bind f "+activate"
bind g "+mapexpand"
bind l "openlimbomenu"
bind m "mvactivate"
bind q "+leanleft"
bind r "+reload"
bind s "+back"
bind t "messagemode"
bind u "messagemode3"
bind v "mp_quickmessage"
bind w "+forward"
bind x "+prone"
bind y "messagemode2"
bind z "mp_fireteammsg"
bind ~ "toggleconsole"
bind CAPSLOCK "+speed"
bind ALT "+stats"
bind CTRL "+topshots"
bind SHIFT "+sprint"
bind F1 "vote yes"
bind F2 "vote no"
bind F3 "ready"
bind F4 "notready"
bind F11 "autoscreenshot"
bind F12 "autorecord"
bind KP_LEFTARROW "selectbuddy 3"
bind KP_5 "selectbuddy 4"
bind KP_RIGHTARROW "selectbuddy 5"
bind KP_END "selectbuddy 0"
bind KP_DOWNARROW "selectbuddy 1"
bind KP_PGDN "selectbuddy 2"
bind KP_ENTER "mp_fireteamadmin"
bind KP_INS "selectbuddy -2"
bind KP_DEL "selectbuddy -1"
bind MOUSE1 "+attack"
bind MOUSE2 "weapalt"
bind MWHEELDOWN "weapprev"
bind MWHEELUP "weapnext"
seta com_hunkMegs "56"
seta com_maxfps "85"
seta com_watchdog "60"
seta com_watchdog_cmd ""
seta com_introplayed "0"
seta com_recommendedSet "1"
seta in_mouse "1"
seta in_dgamouse "1"
seta in_subframe "1"
seta in_joystick "0"
seta joy_threshold "0.15"
seta in_shiftedkeys "1"
seta vm_cgame "0"
seta vm_game "0"
seta vm_ui "0"
seta sv_hostname "ETHost"
seta sv_punkbuster "0"
seta sv_minguidage "0"
seta sv_maxRate "0"
seta sv_minPing "0"
seta sv_maxPing "0"
seta sv_floodProtect "1"
seta g_friendlyFire "1"
seta g_maxlives "0"
seta sv_allowDownload "1"
seta sv_master2 ""
seta sv_master3 ""
seta sv_master4 ""
seta sv_master5 ""
seta sv_lanForceRate "1"
seta g_altStopwatchMode "0"
seta g_complaintlimit "6"
seta g_fastres "0"
seta g_fastResMsec "1000"
seta g_antilag "1"
seta sv_dl_maxRate "42000"
seta sv_wwwDownload "0"
seta sv_wwwBaseURL ""
seta sv_wwwDlDisconnected "0"
seta sv_wwwFallbackURL ""
seta sv_fullmsg "Server is full."
seta bot_enable "0"
seta con_debug "0"
seta con_autoclear "1"
seta cl_autoupdate "1"
seta cl_yawspeed "140"
seta cl_pitchspeed "140"
seta cl_maxpackets "30"
seta cl_packetdup "1"
seta cl_run "1"
seta sensitivity "5.000000"
seta cl_mouseAccel "0"
seta cl_freelook "1"
seta cl_allowDownload "1"
seta cl_wwwDownload "1"
seta cg_autoswitch "0"
seta cg_wolfparticles "1"
seta r_inGameVideo "1"
seta cl_doubletapdelay "350"
seta m_pitch "0.022000"
seta m_yaw "0.022"
seta m_forward "0.25"
seta m_side "0.25"
seta m_filter "0"
seta cl_maxPing "800"
seta cg_drawCompass "1"
seta cg_drawNotifyText "1"
seta cg_quickMessageAlt "1"
seta cg_popupLimboMenu "1"
seta cg_descriptiveText "1"
seta cg_drawTeamOverlay "2"
seta cg_drawGun "1"
seta cg_cursorHints "1"
seta cg_voiceSpriteTime "6000"
seta cg_crosshairSize "48"
seta cg_drawCrosshair "1"
seta cg_zoomDefaultSniper "20"
seta cg_zoomstepsniper "2"
seta name "mike"
seta rate "25000"
seta snaps "20"
seta cl_anonymous "0"
seta cl_punkbuster "1"
seta cg_predictItems "1"
seta cg_autoactivate "1"
seta cg_viewsize "100"
seta cg_autoReload "1"
seta cl_language "0"
seta r_glDriver "libGL.so.1" unsafe
seta r_allowExtensions "1" unsafe
seta r_ext_compressed_textures "1" unsafe
seta r_ext_gamma_control "1" unsafe
seta r_ext_multitexture "1" unsafe
seta r_ext_compiled_vertex_array "1" unsafe
seta r_glIgnoreWicked3D "0" unsafe
seta r_ext_ATI_pntriangles "0" unsafe
seta r_ati_truform_tess "1" unsafe
seta r_ati_truform_normalmode "GL_PN_TRIANGLES_NORMAL_MODE_LINEAR" unsafe
seta r_ati_truform_pointmode "GL_PN_TRIANGLES_POINT_MODE_LINEAR" unsafe
seta r_ati_fsaa_samples "1" unsafe
seta r_ext_texture_filter_anisotropic "0" unsafe
seta r_ext_NV_fog_dist "0" unsafe
seta r_nv_fogdist_mode "GL_EYE_RADIAL_NV" unsafe
seta r_ext_texture_env_add "0" unsafe
seta r_clampToEdge "1" unsafe
seta r_picmip "0"
seta r_roundImagesDown "1"
seta r_rmse "0.0"
seta r_detailtextures "1"
seta r_texturebits "32" unsafe
seta r_colorbits "32" unsafe
seta r_stereo "0" unsafe
seta r_stencilbits "0" unsafe
seta r_depthbits "24" unsafe
seta r_overBrightBits "0"
seta r_ignorehwgamma "0"
seta r_mode "6" unsafe
seta r_oldMode ""
seta r_fullscreen "1"
seta r_customwidth "1600"
seta r_customheight "1024"
seta r_customaspect "1"
seta r_simpleMipMaps "1"
seta r_subdivisions "4"
seta r_smp "0" unsafe
seta r_ignoreFastPath "0"
seta r_lodCurveError "250"
seta r_lodbias "0"
seta r_flares "1"
seta r_ignoreGLErrors "1"
seta r_fastsky "0"
seta r_drawSun "1"
seta r_dynamiclight "1"
seta r_dlightBacks "1"
seta r_finish "0"
seta r_textureMode "GL_LINEAR_MIPMAP_LINEAR"
seta r_textureAnisotropy "1.0"
seta r_swapInterval "0"
seta r_gamma "1.300000"
seta r_facePlaneCull "1"
seta r_railWidth "16"
seta r_railCoreWidth "1"
seta r_railSegmentLength "32"
seta r_primitives "0"
seta r_trisColor "1.0 1.0 1.0 1.0"
seta r_normallength "0.5"
seta cg_shadows "1"
seta r_highQualityVideo "1"
seta r_lastValidRenderer "GeForce3/AGP/SSE2"
seta s_volume "0.8"
seta s_musicvolume "0.5"
seta s_separation "0.5"
seta s_doppler "1"
seta s_khz "22"
seta s_mixahead "0.2"
seta s_mixPreStep "0.05"
seta s_defaultsound "0"
seta s_wavonly "0"
seta s_bits "16"
seta s_channels "2"
seta snddevice "/dev/dsp"
seta com_soundMegs "24"
seta ui_glCustom "0"
seta ui_ffa_fraglimit "20"
seta ui_ffa_timelimit "0"
seta ui_team_fraglimit "0"
seta ui_team_timelimit "20"
seta ui_team_friendly "1"
seta ui_ctf_capturelimit "8"
seta ui_ctf_timelimit "30"
seta ui_ctf_friendly "0"
seta g_spScores1 ""
seta g_spScores2 ""
seta g_spScores3 ""
seta g_spScores4 ""
seta g_spScores5 ""
seta g_spAwards ""
seta g_spVideos ""
seta g_spSkill "2"
seta ui_teamArenaFirstRun "1"
seta ui_master "0"
seta cg_brassTime "2500"
seta cg_drawCrosshairNames "1"
seta cg_drawCrosshairPickups "1"
seta cg_marktime "20000"
seta server1 ""
seta server2 ""
seta server3 ""
seta server4 ""
seta server5 ""
seta server6 ""
seta server7 ""
seta server8 ""
seta server9 ""
seta server10 ""
seta server11 ""
seta server12 ""
seta server13 ""
seta server14 ""
seta server15 ""
seta server16 ""
seta ui_dedicated "0"
seta cg_selectedPlayer "0"
seta cg_selectedPlayerName ""
seta ui_netSource "1"
seta ui_menuFiles "ui/menus.txt"
seta ui_gametype "3"
seta ui_joinGametype "-1"
seta ui_netGametype "4"
seta ui_mapIndex "0"
seta ui_currentMap "0"
seta ui_currentNetMap "0"
seta ui_browserMaster "0"
seta ui_browserGameType "0"
seta ui_browserSortKey "4"
seta ui_browserShowEmptyOrFull "2"
seta ui_browserShowPasswordProtected "2"
seta ui_browserShowFriendlyFire "0"
seta ui_browserShowMaxlives "0"
seta ui_browserShowPunkBuster "0"
seta ui_browserShowAntilag "0"
seta ui_browserShowWeaponsRestricted "0"
seta ui_browserShowTeamBalanced "0"
seta ui_serverStatusTimeOut "7000"
seta cg_drawBuddies "1"
seta cg_drawRoundTimer "1"
seta cg_showblood "1"
seta cg_bloodFlash "1.0"
seta cg_noAmmoAutoSwitch "1"
seta cg_useWeapsForZoom "1"
seta cg_complaintPopUp "1"
seta cg_announcer "1"
seta cg_printObjectiveInfo "1"
seta cg_useScreenshotJPEG "1"
seta cg_drawReinforcementTime "1"
seta cg_crosshairPulse "1"
seta cg_crosshairColor "White"
seta cg_crosshairAlpha "1.0"
seta cg_crosshairColorAlt "White"
seta cg_coronafardist "1536"
seta g_warmup "60"
seta g_lms_roundlimit "3"
seta g_lms_matchlimit "2"
seta g_lms_followTeamOnly "1"
seta g_heavyWeaponRestriction "100"
seta ui_currentCampaign "0"
seta ui_currentNetCampaign "0"
seta ui_campaignIndex "0"
seta ui_currentCampaignCompleted "0"
seta cg_crosshairAlphaAlt "1.0"
seta bot_minplayers "0"
seta g_ipcomplaintlimit "3"
seta g_doWarmup "0"
seta g_inactivity "0"
seta refereePassword "none"
seta g_teamForceBalance "0"
seta g_spectatorInactivity "0"
seta match_latejoin "1"
seta match_minplayers "4"
seta match_mutespecs "0"
seta match_readypercent "100"
seta match_timeoutcount "3"
seta match_timeoutlength "180"
seta match_warmupDamage "1"
seta server_autoconfig "0"
seta server_motd0 " ^NEnemy Territory ^7MOTD "
seta server_motd1 ""
seta server_motd2 ""
seta server_motd3 ""
seta server_motd4 ""
seta server_motd5 ""
seta team_maxPanzers "-1"
seta team_maxplayers "0"
seta team_nocontrols "0"
seta vote_allow_comp "1"
seta vote_allow_gametype "1"
seta vote_allow_kick "1"
seta vote_allow_map "1"
seta vote_allow_mutespecs "1"
seta vote_allow_nextmap "1"
seta vote_allow_pub "1"
seta vote_allow_referee "0"
seta vote_allow_shuffleteamsxp "1"
seta vote_allow_swapteams "1"
seta vote_allow_friendlyfire "1"
seta vote_allow_timelimit "0"
seta vote_allow_warmupdamage "1"
seta vote_allow_antilag "1"
seta vote_allow_muting "1"
seta vote_limit "5"
seta vote_percent "50"
seta ui_r_mode ""
seta ui_r_gamma ""
seta ui_rate ""
seta ui_handedness ""
seta ui_sensitivity ""
seta ui_profile_mousePitch ""
seta ui_showtooltips "1"
seta ui_autoredirect "0"
seta com_recommended "0"
seta ui_r_colorbits ""
seta ui_r_lodbias ""
seta ui_r_subdivisions ""
seta ui_r_picmip ""
seta ui_r_texturebits ""
seta ui_r_depthbits ""
seta ui_r_ext_compressed_textures ""
seta ui_r_dynamiclight ""
seta ui_r_detailtextures ""
seta ui_r_texturemode ""
seta com_zoneMegs "24"

```

I found an old UT cd, installed it and got similar lags in UT...

---

### Post by asipi on 2007-03-29
blue line is the server side, so it looks like the problem is inside in your machine
I guess the reason is the weakness of your graphic hardware so we need some graphic tweaks to be set. it will a little bit decrease your ingame graphic quality
but it worth a try.

so here is my advise:
- make a file in your ~/etwolf/etmain directory called autoexec.cfg
- copy this into it:
```
//
// GRAPHICAL SETTINGS
//
	seta r_ignoreGLErrors "1"
	seta r_mode "4"
	seta r_textureMode "GL_NEAREST_MIPMAP_NEAREST"
	seta r_dynamiclight "0"
	seta r_fastsky "0"
	seta r_flares "0"
	seta r_drawSun "0"
	seta cg_atmosphericEffects "0"
	seta cg_wolfparticles "0"
	seta cg_fov "90"
	seta cg_shadows "0"
	seta cg_gibs "0"
	seta r_depthbits "24"	// (24-bit depth buffer)
	seta r_colorbits "32"	// (32-bit color)
	seta r_texturebits "32"	// (32-bit color texture sampling)
	seta r_primitives "0"	// (Use glDrawElements on vertex arrays)
	seta r_gamma "1.70"		// (Gamma up a tad)
	seta r_intensity "1.1"	// (Brightness up a bit)
	seta r_picmip "3"		// (Textures blurred and faster)
	seta r_mapoverbrightbits "3" // (Another brightness improvement)
	seta r_overbrightbits "0"	// (This brightness haX is bad, mmmk)
	seta r_detailtextures "0"	// (Don't show high-LOD textures when close)
	seta r_simpleMipMaps "0"	// (Reduce mid-mapping)
	seta r_vertexlight "0"	// (Per-vertex lighting - not lightmaps)
	seta r_dlightBacks "1"	// ()
	seta r_subdivisions "12"	// (Decrease the complexity of curves etc)
	seta r_lodbias "3"		// level of detail
	seta r_lightmap "1"
	seta r_stencilbits "0" unsafe
	seta r_drawfoliage "0"
	seta r_finish "0"

	seta cg_coronas "0"
	seta cg_brassTime "0"
	seta cg_marktime "12500"

	seta r_ext_texture_filter_anisotropic "0"
	seta r_ext_compressed_textures "1"
	seta r_ext_compiled_vertex_array "1"

	seta cg_bloodDamageBlend "0"
	seta cg_showblood "0"
	seta cg_bloodFlash "0"

```
- when et started bring down et console with button "~" or whatever you have been set it for and type 
```
/exec autoexec.cfg
/vid_restart
```
this only for be sure that all graphic tweaks would have been set

then try to connect to a server and refer here was the lag issue had been improved or not

cheers

PS: don't give up, et is the best multiplayer teamgame ever, at the and we will find your lag reason ;)

---

### Post by 1/0 on 2007-03-29
It is a good game, isn't it! 

So I created the autoexec.cfg and did as you said but still lags. When I executed the script i got the following errors:

```

Unknown command "mmmk)"
Unknown command "when"
Unknown command "curves"

```

Also when I closed the game I got some errors I've never seen before:

```
Error ui/playonline.menu, line 199: unknown menu keyword EDITFIELDACTION
```
I got errors for several keywords and lines. What bugs me is that even UT lagged without playing online.

---

### Post by asipi on 2007-03-29
somethings could come from the character encoding by copying the text from the webpage int you editor :S
i think it is the handling of the " sign could cause the problem... (what the name of this sign in english? I don't know :) ) tip: quotation mark?

what editor did you use? try another one, use gedit or vi on terminal, and check the quotation marks, only the normal type is allowed, some editors and encodings differentiates opening and closing quotation marks, but in english they are the same.

all text after "/" are remarks and et ignores them, so what you experienced could not appear in normal way if you check the text.

as an emergency solution try to remove all remarks from the file, but it should work because I copied it from my autoexec.cfg what I use every day

---

### Post by 1/0 on 2007-03-30
I used nano before so I did the same with ooo and removed the first /. No errors. I still gets lags. After I exit ET the computer stalls the shell that loaded x.et won't respond for 20 seconds or so. I guess that's due to the extra xorg-server.

---

### Post by asipi on 2007-03-30
I guess u need a stronger videocard :(

---

### Post by 1/0 on 2007-03-30
Are you sure? I'm just asking so I don't buy one in vain. ET worked before I switched to Xubuntu, that's why. On the other hand it makes sense that some hardware is broke. Its what I feared from the beginning. 

I've been looking at some cards:

Sparkle Geforce 6200 256 MB DDR2
Sparkle Geforce 7300GT 256 MB DDR2

Any suggestion on which? The cost about 55 and 95 € respectively. 

Anyway, thanks both of you for the effort to help me out! That makes a forum good.

---

### Post by asipi on 2007-03-30
> **1/0 said:**
> Sparkle Geforce 6200 256 MB DDR2
Sparkle Geforce 7300GT 256 MB DDR2

I have GF6200 but with 128 MB ram and ET runs smoothly, so it's price is nearly half than 7300, but if you could afford I suggest the better one.

If on another distro ET was better maybe first try an older release of ubuntu could be a solution.
Ubuntu Edgy has 2.6.11 kernel and upstart instead SysV init also X has a newer release in it, and newest HAL and udev etc... Ok that newer linux  versions could run on older architecture but it is only for say "compatibility" reason, they are better on newer hardware sure (and this bring up some other resource requirements too ;) )

Maybe with a distro with 2.4 kernel release you could not see such problems, but I don't know I am only thinking aloud.

But for sure when I changed my videocard from GeForce Ti5500 64MB to GeForce 6200 128MB I gained about 30-40 FPS and also could set some more detailed graphics.

---

### Post by berserker on 2007-03-30
I didn't see this in any of the responses so far:

Have you tried turning off "wall markings" in the ET settings?

Another problem is called "fire lag" which has to do with automatic weapons fire during online play.  Something about not being able to adjust sound to 22 KHz (the default is 44 KHz).

I have this for my startup script:

```
et +set fs_game tcetest +set com_hunkMegs 1024 +set s_khz 22
```

---

### Post by 1/0 on 2007-03-31
OK, I tried the settings and script with some changes. The red bars in the bottom of the lagometer happens less. The green line disappears when the lags occur. Sometimes I get no line, sometimes narrower red lines  most of the time narrow green lines. 

I also noticed the error message in the console is back when I've disconnected from a server:

```
Sys_LoadDll(ui) succeeded!
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword EDITFIELDACTION
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 8
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword +
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword .5
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword *
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword .75
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword *
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 608
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword -
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 18
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword -
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 6
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword +
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 2
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword +
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 2
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 140
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword .5
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword *
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword .75
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword *
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword (
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 608
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword -
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 18
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword -
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 6
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 10
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ServerName filter:
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword .2
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 8
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ui_browserFilterHost
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 15
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword 15
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword uiScript
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword RefreshFilter
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ;
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword setcvar
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ui_filterdescription
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword Filter affecting servernames
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword ,
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword Includes only the server with a (partial) stringmatch in the servername
^1ERROR: ui/playonline.menu, line 199: unknown menu keyword )
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword EDITFIELDACTION
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword (
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 8
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 48
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword (
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 400
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword -
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 12
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword )
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword -
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 4
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 10
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword Player Alias:
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword .2
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 8
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword limboname
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 36
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword 28
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword ,
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword copyCvar
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword limboname
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword Enter the name that you wish to be known by to others on servers
^1ERROR: ui/options_customise_game.menu, line 48: unknown menu keyword )
^1ERROR: ui/ingame_vote_misc.menu, line 59: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 59: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 60: unknown menu item keyword modStringNot
^1ERROR: ui/ingame_vote_misc.menu, line 60: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 64: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 64: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 65: unknown menu item keyword modStringNot
^1ERROR: ui/ingame_vote_misc.menu, line 65: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 75: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 75: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 84: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 84: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 95: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 96: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword EDITFIELDLEFTEXT
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword (
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 8
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 176
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword +
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 2
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword .80
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword *
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword (
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 296
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword -
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 18
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword )
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 10
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword Poll question:
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword .2
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 8
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ui_poll
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 50
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 19
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword voteFlag
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword 1048576
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword Enter the question you want to call a poll vote for.
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu keyword )
^1ERROR: ui/ingame_vote_misc.menu, line 101: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 101: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 59: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 59: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 60: unknown menu item keyword modStringNot
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 60: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 64: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 64: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 65: unknown menu item keyword modStringNot
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 65: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 83: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 83: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 94: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 95: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword EDITFIELDLEFTEXT
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword (
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 8
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 176
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword +
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 2
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword .80
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword *
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword (
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 296
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword -
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 18
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword )
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 10
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword Poll question:
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword .2
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 8
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ui_poll
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 50
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword 19
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword modString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword ,
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword Enter the question you want to call a poll vote for.
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu keyword )
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 99: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 99: unknown menu item keyword etpub
^5PunkBuster Client: Not Connected to a Server
WARNING: music file sound/music/menu_server.wav is not 22k stereo
```

---

### Post by 1/0 on 2007-03-31
I decided to create a new user, so I moved .etwolf and started with the sound settings above. The error messages where gone but the lags still present. I even got lags in the main window, not connected...

I'm just writing this so I don't go and buy a new card that doesn't solve this. (I might get one anyway but I'd like to wait until I start working this summer.)

---

### Post by asipi on 2007-03-31
hmm, sounds like incomplete install of et and/or mod (etpub as seen above) try to download et 2.60 installer for linux again from a different location, remove all et files then install again with the new installer. I had a 800MHz machine before, and with degraded graphic quality I was able to play at 30-40 FPS without lag so you could be right not to upgrade the hardware. Isay again that your lag should come from a periodically run process what you should find. Could be that the runtime of it is under 1 sec so it would not be easy to find it.

anyway the sounds in et mostly with 22khz sample rate so that sound setting above doesn't counts imho...

---

### Post by 1/0 on 2007-03-31
I uninstaleld/deleted all et files and got a copy from another server. Installed and got lags again...

I also installed stratagus and that lags as well. That is stratagus, ut, and et lags (but I'm interested in why et lags). With all checks and all those games lagging I'm thinking it's got to be something causing this. It might be some xorg setting (except it seemed fine), some software problem  or maybe a hardware problem. 

Could it be some check that ext3 does? Could the hard drives (although pretty new) be causing something (I checked them with Seatools and they passed there). Could it be some setting in xorg/nvidia, such as virtual screen size, composite, wacom (?), /usr/lib/xserver/SecurityPolicy or something...

My /var/log/Xorg.0.log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux soma 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 31 12:41:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "COMPAQ S920"
(**) |   |-->Device "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.0
        X.Org XInput driver : 0.6
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 05 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 05 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 0e11,2411 rev 05 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 0e11,2411 rev 05 class 0c,03,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 0e11,2411 rev 05 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0201 card 1462,5100 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 0e11,0012 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 10ec,8139 card 10bd,0320 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 1102,0002 card 1102,806b rev 07 class 04,01,00 hdr 80
(II) PCI: 02:0a:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 02:0b:0: chip 104c,8020 card 1113,1394 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:0d:0: chip 14f1,2f00 card 13e0,8d85 rev 01 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xfd000000 - 0xfe1fffff (0x1200000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf8000000 - 0xfc2fffff (0x4300000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x00001000 - 0x000010ff (0x100) IX[B]
        [1] -1  0       0x00001400 - 0x000014ff (0x100) IX[B]
        [2] -1  0       0x00001800 - 0x000018ff (0x100) IX[B]
        [3] -1  0       0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfc300000 - 0xfc5fffff (0x300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xfd000000/24, 0xf8000000/26, 0xfc200000/19
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xfc300000 - 0xfc30ffff (0x10000) MX[B]
        [1] -1  0       0xfc310000 - 0xfc313fff (0x4000) MX[B]
        [2] -1  0       0xfc315000 - 0xfc3157ff (0x800) MX[B]
        [3] -1  0       0xfc315800 - 0xfc3158ff (0x100) MX[B]
        [4] -1  0       0xfc314000 - 0xfc314fff (0x1000) MX[B]
        [5] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [6] -1  0       0xfc200000 - 0xfc27ffff (0x80000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [9] -1  0       0x00001468 - 0x0000146f (0x8) IX[B]
        [10] -1 0       0x00001460 - 0x00001467 (0x8) IX[B]
        [11] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [12] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [13] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [14] -1 0       0x00002460 - 0x0000247f (0x20) IX[B]
        [15] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [16] -1 0       0x00002480 - 0x0000248f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfc300000 - 0xfc30ffff (0x10000) MX[B]
        [1] -1  0       0xfc310000 - 0xfc313fff (0x4000) MX[B]
        [2] -1  0       0xfc315000 - 0xfc3157ff (0x800) MX[B]
        [3] -1  0       0xfc315800 - 0xfc3158ff (0x100) MX[B]
        [4] -1  0       0xfc314000 - 0xfc314fff (0x1000) MX[B]
        [5] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [6] -1  0       0xfc200000 - 0xfc27ffff (0x80000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [9] -1  0       0x00001468 - 0x0000146f (0x8) IX[B]
        [10] -1 0       0x00001460 - 0x00001467 (0x8) IX[B]
        [11] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [12] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [13] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [14] -1 0       0x00002460 - 0x0000247f (0x20) IX[B]
        [15] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [16] -1 0       0x00002480 - 0x0000248f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfc300000 - 0xfc30ffff (0x10000) MX[B]
        [5] -1  0       0xfc310000 - 0xfc313fff (0x4000) MX[B]
        [6] -1  0       0xfc315000 - 0xfc3157ff (0x800) MX[B]
        [7] -1  0       0xfc315800 - 0xfc3158ff (0x100) MX[B]
        [8] -1  0       0xfc314000 - 0xfc314fff (0x1000) MX[B]
        [9] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [10] -1 0       0xfc200000 - 0xfc27ffff (0x80000) MX[B](B)
        [11] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [12] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00001468 - 0x0000146f (0x8) IX[B]
        [16] -1 0       0x00001460 - 0x00001467 (0x8) IX[B]
        [17] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [18] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [19] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [20] -1 0       0x00002460 - 0x0000247f (0x20) IX[B]
        [21] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [22] -1 0       0x00002480 - 0x0000248f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9631
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9631
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfc300000 - 0xfc30ffff (0x10000) MX[B]
        [5] -1  0       0xfc310000 - 0xfc313fff (0x4000) MX[B]
        [6] -1  0       0xfc315000 - 0xfc3157ff (0x800) MX[B]
        [7] -1  0       0xfc315800 - 0xfc3158ff (0x100) MX[B]
        [8] -1  0       0xfc314000 - 0xfc314fff (0x1000) MX[B]
        [9] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [10] -1 0       0xfc200000 - 0xfc27ffff (0x80000) MX[B](B)
        [11] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [12] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00001468 - 0x0000146f (0x8) IX[B]
        [16] -1 0       0x00001460 - 0x00001467 (0x8) IX[B]
        [17] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [18] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [19] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [20] -1 0       0x00002460 - 0x0000247f (0x20) IX[B]
        [21] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [22] -1 0       0x00002480 - 0x0000248f (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfc300000 - 0xfc30ffff (0x10000) MX[B]
        [5] -1  0       0xfc310000 - 0xfc313fff (0x4000) MX[B]
        [6] -1  0       0xfc315000 - 0xfc3157ff (0x800) MX[B]
        [7] -1  0       0xfc315800 - 0xfc3158ff (0x100) MX[B]
        [8] -1  0       0xfc314000 - 0xfc314fff (0x1000) MX[B]
        [9] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [10] -1 0       0xfc200000 - 0xfc27ffff (0x80000) MX[B](B)
        [11] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [12] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x00001468 - 0x0000146f (0x8) IX[B]
        [19] -1 0       0x00001460 - 0x00001467 (0x8) IX[B]
        [20] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [21] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [22] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [23] -1 0       0x00002460 - 0x0000247f (0x20) IX[B]
        [24] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [25] -1 0       0x00002480 - 0x0000248f (0x10) IX[B]
        [26] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [27] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce3 Ti 200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.20.00.21.01
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce3 Ti 200 at PCI:1:0:0:
(--) NVIDIA(0):     COMPAQ S920 (CRT-0)
(--) NVIDIA(0): COMPAQ S920 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (112, 112); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xfc200000 - 0xfc27ffff (0x80000) MX[B]
        [1] 0   0       0xf8000000 - 0xfbffffff (0x4000000) MX[B]
        [2] 0   0       0xfd000000 - 0xfdffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xfc300000 - 0xfc30ffff (0x10000) MX[B]
        [8] -1  0       0xfc310000 - 0xfc313fff (0x4000) MX[B]
        [9] -1  0       0xfc315000 - 0xfc3157ff (0x800) MX[B]
        [10] -1 0       0xfc315800 - 0xfc3158ff (0x100) MX[B]
        [11] -1 0       0xfc314000 - 0xfc314fff (0x1000) MX[B]
        [12] -1 0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [13] -1 0       0xfc200000 - 0xfc27ffff (0x80000) MX[B](B)
        [14] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x00001468 - 0x0000146f (0x8) IX[B]
        [22] -1 0       0x00001460 - 0x00001467 (0x8) IX[B]
        [23] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [24] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [25] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [26] -1 0       0x00002460 - 0x0000247f (0x20) IX[B]
        [27] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [28] -1 0       0x00002480 - 0x0000248f (0x10) IX[B]
        [29] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [30] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+se+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(II) NVIDIA(0): Setting mode "800x600"
(II) NVIDIA(0): Setting mode "1600x1200"
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): Setting mode "1600x1200"
(II) NVIDIA(0): Setting mode "800x600"
(II) NVIDIA(0): Setting mode "1600x1200"

```

---

### Post by 1/0 on 2007-04-02
Well, I decided to get a new card and I found a special price on a Gigabyte GeForce 7600GS 256MB so now I'm just waiting for the new card. I hope it'll be better.

---

### Post by 1/0 on 2007-04-04
Got the card and installed it but the problems remain... The graphics are much better so its not a bad buy but the lags continue.

This can't be related to ET. There's got to be something wrong with Ubuntu, Nvidia or something else in my hardware. I've used Envy to install the Nvidia driver and I used the legacy drivers before and the regular Nvidia drivers with the new card (1.0.9755).

Could it be the hard drive doing some built in start/stop sequence to save energy or something?

---

### Post by 1/0 on 2007-04-08
I guess I'll have to install Arch to see if the problem is due to Ubunutu/settings or not.

---

### Post by 1/0 on 2007-04-09
I installed Arch Linux and I still got the same problem.

---

### Post by 1/0 on 2007-04-17
I've run the long tests in Seatools on the harddrives and they both passed without errors. Now I really don't know what's going on. Supertux works fine, pinball not ok, et not ok, ut not ok... I noticed that GRUB was removed/damaged when I run the linux version of Seatools. 

Maybe it is something generic with the 3d acceleration, i.e. the nvidia drivers and not the cards.

I'm not in control of my computer anymore...

---

### Post by 1/0 on 2007-04-18
I think I've solved it. I disabled the power save in BIOS, rebuilt the computer. I re-seated the RAMs, removed an extra NIC and a PCI modem. I removed some dust that was stuck in the middle of the CPU fan and now it seems to be fine again! Hope it helps if anyone gets similar symptoms.

---

### Post by asipi on 2007-04-25
nice to hear it :) Congratulations! Welcome on battlefield :)

Visit our server if you have time: 85.25.130.154:27960
Clan homepage is: [http://vwvclan.extra.hu/](http://vwvclan.extra.hu/)
Dual language homepage so you can read all the important things there
What is your nickname in ET?

I do not understand why I did not receive emails from the forum because I am subscrided to this thread, but no alerts I recived about your posts... maybe google spamfilter took them out, who knows

---

