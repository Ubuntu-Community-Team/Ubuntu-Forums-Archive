---
title: "Problem with KDE Display Settings and Nvidia TwinView"
date: 2006-06-03
forum: Desktop Environments
---

### Post by WickedImp on 2006-06-03
First some hardware Info:
P4 2.4GHz, 512MB DDR, NV GF4 Ti 4400

Some software/package infos:
linux-image-2.6.15-23-686 (with headers, and restricted modules)
nvidia-glx-1.0.8762+2.6.15.11-1 (seems to be latest, also)
kde is version 3.5.2
xserver-xorg is version 7.0.0

I do not know exactly since when I get this strange error - must be one of the last updates I did to get to kubuntu 6.06 LTS. Already tried and searched all this threads about nvidia and twinview, it finally seems that nobody got this problem :-?

The Problem:
It seems that KDE->Systemsettings->Display does not recognize all display modes anymore. I.e.: if I define MetaModes "1280x1024,1280x1024; 1280x1024,NULL" it should bring up a list like this: 2560x1024, 1280x1024. But it does not. It only shows 1280x1024. The strange thing aboutthis is, that in the xorg log nvidia says it changes display mode to 1280x1024,1280x1024. Actually the NVidia Logo is displayed on both screens, but KDM uses only one screen with (it seems to be - cause I can scroll the viewport) a virtual size of 2560x1024 - only uses a resolution of 1280x1024. Logging in brings up KDE with a mode set to 1280x1024 (also virtual screen size is the same - no scrolling)

What the heck is wrong with KDE now??? Did anybody got this problem, too??? How can I change and query the available screen resolutions from the command line???

---

### Post by WickedImp on 2006-06-03
Btw... this is my xorg.conf - maybe someone recognizes a mistake I did...

```

Section "ServerLayout"
    Identifier     "TwinView Layout"
    Screen         0 "CRT-0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "Xinerama" "Off"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
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

Section "Monitor"
    Identifier     "MD1998PB"
    Option         "DPMS"
    HorizSync      30-98
    VertRefresh    50-120
EndSection

Section "Monitor"
    Identifier     "LG902B"
    Option         "DPMS"
    HorizSync      30-61
    VertRefresh    50-160
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
    Driver         "nvidia"
    Option         "NvAGP" "2"
    Option         "RenderAccel" "1"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "ConnectedMonitor" "crt, crt"
    Option         "NoPowerConnectorCheck"
    Option         "TwinView" "1"
    Option         "TwinViewOrientation" "RightOf"
    Option         "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 720x400,720x400; 640x480,640x480; 1280x1024,NULL; 1280x960,NULL; 1152x864,NULL; 1024x768,NULL; 800x600,NULL; 720x400,NULL; 640x480,NULL"
    Option         "SecondMonitorHorizSync" "30-61"
    Option         "SecondMonitorVertRefresh" "50-160"
#    Option         "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
    Identifier     "CRT-0"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
    Monitor        "MD1998PB"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by asipi on 2006-06-03
[QUOTE=WickedImp]First some hardware Info:
P4 2.4GHz, 512MB DDR, NV GF4 Ti 4400

but KDM uses only one screen with (it seems to be - cause I can scroll the viewport) a virtual size of 2560x1024 - only uses a resolution of 1280x1024. Logging in brings up KDE with a mode set to 1280x1024 (also virtual screen size is the same - no scrolling)

What the heck is wrong with KDE now??? Did anybody got this problem, too??? How can I change and query the available screen resolutions from the command line???[/QUOTE]

I am using almost the same card (Abit Siluro GF4 Ti4200), but I have only one monitor configured. I have a similar result...

I took out some modelines from the config, and I realized, that the kdm login screen using the highest available resolution for the virtual screen, and for the real display (I mean the monitor) it is using what I have set for the desktop.

First I thought it is "feature" of the kdm, and I tried out gdm. It was the same :( 

I am searching for where kdm and/or gdm takes from the datas to start X. Unfortunatelly I am not a guru :-k so I haven't found it yet.

---

### Post by asipi on 2006-06-03
I've just now found this in the xorg log file:
```

(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4200 at PCI:1:0:0:
(--) NVIDIA(0):     Sony CPD-G420 (CRT-1)
(--) NVIDIA(0): Sony CPD-G420 (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1280x960@75"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1152x864@75"
(II) NVIDIA(0):     "1152x768@54"
(II) NVIDIA(0):     "1280x854"
(II) NVIDIA(0):     "1024x768@60"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "1280x960@60"
(II) NVIDIA(0):     "1024x768@75"
(II) NVIDIA(0):     "1280x960@85"
(II) NVIDIA(0):     "1024x768@85"
(II) NVIDIA(0):     "832x624@75"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "800x600@85"
(II) NVIDIA(0):     "800x600@75"
(II) NVIDIA(0):     "800x600@72"
(II) NVIDIA(0):     "800x600@56"
(II) NVIDIA(0):     "640x480@85"
(II) NVIDIA(0):     "640x480@75"
(II) NVIDIA(0):     "640x480@72"
(II) NVIDIA(0):     "640x480@60"
**(II) NVIDIA(0): Virtual screen size determined to be 1280 x 960**
```

I do not understand why it is setting the virtual screen size... :confused: I removed the line of it from xorg.conf. Could it be a bug?

---

### Post by wislon on 2006-06-08
I had a similar problem using gnome. I'd set the metamodes to something along the lines of "1280x1024,1280,1024","1280x1024" (I can't recall exactly, this was a coupla months ago). What I discovered, after going through the xorg log file is that it was working with the dual ("1280x1024,1280x1024") up until it displayed the greeter, waiting for me to log in. 

As soon as I logged in, it reverted to just using the single "1280x1024". I smashed my head on this for a LONG time, until I accidentally removed the option for just the single "1280x1024", so all I was left with was "1280x1024,1280x1024". 

Voila. It worked :)

I've tried putting it back in, in dapper, and exactly the same thing happened. 

I've found the best option for this is to ONLY allow metamodes related to a dual monitor setup. Remove any metamodes that describe options for only ONE screen. I'd paste my xorg.conf in here, but I'm in windoze at the moment and can't get to it.

I hope this helps you, coz God knows I spent long enough battling with this!

---

### Post by WickedImp on 2006-06-09
hmmm... it seems that something is wrong with xinerama and/or twinview stuff. the display config from kde is crashing cause auf an error it gets when doing a query on the second display. also (i.e.) xawtv is crashing while second screen is used. I think every app which queries x11 screens will crash with twinview and 2 screens.

also wrote a program to get information from x11 about xinerama and screens and supported modelines. the set command works, but it will not set the virtual size of the screen (do not know how to do it :P )
```

#include "local.h"

xdpyset_o::xdpyset_o() {
    this->m_pDisplay = 0;
    this->m_nIsXinerama = 0;
    this->m_nNumScreens = 0;
}

xdpyset_o::~xdpyset_o() {
    if( this->m_pDisplay ) {
        this->m_pDisplay;
    }
}

int xdpyset_o::init() {
    this->m_pDisplay = XOpenDisplay( "" );
    if( !this->m_pDisplay ) return 0;

#ifdef HAVE_LIBXINERAMA
    XineramaQueryVersion( this->m_pDisplay, &this->m_nXineramaVersion[0], &this->m_nXineramaVersion[1] );

    if( XineramaIsActive( this->m_pDisplay ) ) {
        int screen_exists[1024], i;
        XineramaScreenInfo *screen = XineramaQueryScreens( this->m_pDisplay, screen_exists );
        for (i=0; i==screen[i].screen_number; i++){}
        XFree(screen);
        this->m_nNumScreens = i;
        this->m_nIsXinerama = 1;
    } else {
#endif
        this->m_nNumScreens = XScreenCount( this->m_pDisplay );
#ifdef HAVE_LIBXINERAMA
    }
#endif

    return 1;
}

void xdpyset_o::info() {
    XF86VidModeModeLine mml;
    XF86VidModeModeInfo **mmi, *m;
    int i, a, clock, num;

    printf( "%s v%s\n\n", PACKAGE, VERSION );

#ifdef HAVE_LIBXINERAMA
    printf( "Xinerama: %s\n", ((this->m_nIsXinerama)?"ON":"off") );
    if( this->m_nIsXinerama ) {
        printf( "Xinerama Version: %d.%d\n", this->m_nXineramaVersion[0], this->m_nXineramaVersion[1] );
    }
#endif

    printf( "Screens: %d\n", this->m_nNumScreens );
    for( i=0; i<this->m_nNumScreens; i++ ) {
        printf( "Screen %d:\n", i );
        memset( &mml, 0, sizeof(mml) );
        clock = 0;
        num = 0;
        mmi = 0;
        XF86VidModeGetModeLine( this->m_pDisplay, i, &clock, &mml );
        XF86VidModeGetAllModeLines( this->m_pDisplay, i, &num, &mmi );
        printf( "  ModeLine: h(%d %d %d %d %d) v(%d %d %d %d) flags(0x%0X) @ %d\n",
            mml.hdisplay, mml.hsyncstart, mml.hsyncend, mml.htotal, mml.hskew,
            mml.vdisplay, mml.vsyncstart, mml.vsyncend, mml.vtotal, mml.flags,
            clock );
        printf( "  Supported: (%d)\n", num );
        for( a=0; a<num; a++ ) {
            m = mmi[a];
            printf( "    [%d]: h(%d %d %d %d %d) v(%d %d %d %d) flags(0x%0X) @ %d\n",
                a,
                m->hdisplay, m->hsyncstart, m->hsyncend, m->htotal, m->hskew,
                m->vdisplay, m->vsyncstart, m->vsyncend, m->vtotal, m->flags,
                m->dotclock );
        }
        XFree( mmi );
    }
}

void xdpyset_o::set( int screen, int mode ) {
    XF86VidModeModeInfo **mmi, *m;
    int num, x, y;

    if( screen < 0 || screen > this->m_nNumScreens ) {
        printf( "[error]: screen not valid\n" );
        return;
    }

    XF86VidModeGetAllModeLines( this->m_pDisplay, screen, &num, &mmi );
    if( mode < 0 || mode > num ) {
        printf( "[error]: mode not valid\n" );
        return;
    }
    m = mmi[mode];

    if( !XF86VidModeSwitchToMode( this->m_pDisplay, screen, m ) ) {
        printf( "[error]: mode switch failed\n" );
    } else {
        printf( "[info]: h(%d %d %d %d %d) v(%d %d %d %d) flags(0x%0X) @ %d\n",
            m->hdisplay, m->hsyncstart, m->hsyncend, m->htotal, m->hskew,
            m->vdisplay, m->vsyncstart, m->vsyncend, m->vtotal, m->flags,
            m->dotclock );

        XF86VidModeSetViewPort( this->m_pDisplay, screen, 0, 0 );
    }

    XFree( mmi );
    XFlush( this->m_pDisplay );
}

int main( int argc, char **argv ) {
    int a, z=1;

    xdpyset_o *xds = new xdpyset_o();
    if( !xds ) return 1;

    if( xds->init() ) {
        for( a=1; a<argc; a++ ) {
            if( !strcmp( argv[a], "set" ) ) {
                if( argc < 4 ) continue;
                xds->set( atoi(argv[2]), atoi(argv[3]) );
                a = argc;
                z = 0;
            } else if( !strcmp( argv[a], "info" ) ) {
                xds->info();
                a = argc;
                z = 0;
            }
        }
        if( z ) {
            printf( "usage:\n  set <screen> <modenum>\n  info\n" );
            a = argc;
        }
    }

    delete xds;

    return 0;
}

```

calling 'xdpyset info' gives me the following error:
```

xdpyset v0.1

Xinerama: ON
Xinerama Version: 1.1
Screens: 2
Screen 0:
  ModeLine: h(2560 0 0 0 0) v(1024 0 0 0) flags(0x0) @ 0
  Supported: (12)
    [0]: h(2560 0 0 0 0) v(1024 0 0 0) flags(0x0) @ 0
    [1]: h(1280 1344 1504 1728 0) v(1024 1025 1028 1072) flags(0x5) @ 157500
    [2]: h(2304 0 0 0 0) v(864 0 0 0) flags(0x0) @ 0
    [3]: h(1152 1216 1344 1568 0) v(864 865 868 911) flags(0x9) @ 121500
    [4]: h(2048 0 0 0 0) v(768 0 0 0) flags(0x0) @ 0
    [5]: h(1024 1072 1168 1376 0) v(768 769 772 808) flags(0x5) @ 94500
    [6]: h(1600 0 0 0 0) v(600 0 0 0) flags(0x0) @ 0
    [7]: h(800 832 896 1048 0) v(600 601 604 631) flags(0x5) @ 56300
    [8]: h(1440 0 0 0 0) v(400 0 0 0) flags(0x0) @ 0
    [9]: h(720 760 832 936 0) v(400 401 404 446) flags(0x6) @ 35500
    [10]: h(1280 0 0 0 0) v(480 0 0 0) flags(0x0) @ 0
    [11]: h(640 672 752 864 0) v(480 480 482 505) flags(0x25) @ 74250
Screen 1:
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  1 (XF86VidModeGetModeLine)
  Value in failed request:  0x105
  Serial number of failed request:  20
  Current serial number in output stream:  20

```

it correctly says xinerama is on. xinerama reports 2 screens. query on screen 0 gives all modes I recetnly set in metamodes option. screen 1 brings up this error.

does anybody know more about x11 and nvidia drivers? is this a bug? where to report? nvidia or x.org? how to get more info about this problem?

Is there a single person with current dapper release and twinview where everything works?

---

### Post by tkman on 2006-06-13
I am finding very similar problems.  I have twinview enabled too and things are messy.  I don't have proper video resolutions in KDE display manager, xawtv crashes, and other wierd things.  I really didn't want to listen to a few critics when they said dapper was a bit of a let down because of how many show-stopping bugs there are, but I'm beginning to agree.

This release was to compete with Windows, but I think it may have been a step backward unless a number of these bugs are taken care of.

---

