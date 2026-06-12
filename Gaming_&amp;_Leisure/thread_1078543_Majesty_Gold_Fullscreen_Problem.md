---
title: "Majesty Gold Fullscreen Problem"
date: 2009-02-23
forum: Gaming &amp; Leisure
---

### Post by binbash on 2009-02-23
Last year i bought Majesty Gold : [http://www.linuxgamepublishing.com/info.php?id=8&](http://www.linuxgamepublishing.com/info.php?id=8&)

Today , i want to install and play Majesty Gold, i installed and updated the Majesty, but the game closes itself if i want to start the game with fullscreen (-f) , but i can start it at window mode (-w)


This is an old game so i guess this game needs something at xorg.conf (resolutions i guess) , here is the output of my xorg.conf : 

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Here is the error part : 

```

This is a BUG, please report it to http://support.linuxgamepublishing.com
Stack dump:
{
	[0xb8014400]
	/lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7d72268]
	/lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7d6972e]
	/usr/lib/libX11.so.6 [0xb7f19424]
	/usr/lib/libX11.so.6 [0xb7f195fd]
	/usr/lib/libX11.so.6(XWarpPointer+0x25) [0xb7f0f9a5]
	./majx [0x83a3c00]
	./majx(X11_ResizeFullScreen+0x68) [0x83a45a8]
	./majx(X11_EnterFullScreen+0x156) [0x83a4852]
	./majx [0x83827d4]
	./majx [0x838297a]
	./majx(SDL_SetVideoMode+0x1b3) [0x837f5b3]
	./majx(CreateOSWindow__10CYLinuxAppPUliiiiiPc+0x50) [0x827c938]
	./majx(main+0x25f) [0x81eabbb]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d5b685]
	./majx(XMapRaised+0x39) [0x813b901]
}



```

---

### Post by Perfect Storm on 2009-02-23
Got the exact same error output (or very similiar as I'm using 64-bit). I bug-report it over a year ago to LGP and nothing is done even though they was working on a patch to fix this.
You might want to do the same, so we can get a patch :( (last patch 2006)

```
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cd0891]   
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf7ea8494]               
#3 majx(SDL_XF86VidModeQueryVersion+0x8f) [0x83a52b3]               
#4 majx(X11_GetVideoModes+0x161) [0x83a3ea9]                        
#5 majx [0x8381930]                                                 
#6 majx(SDL_VideoInit+0x284) [0x837ed78]                            
#7 majx(SDL_InitSubSystem+0x39) [0x83765a5]                         
#8 majx(SDL_Init+0x18) [0x8376684]                                  
#9 majx(Instance__10CYLinuxApp+0x5f) [0x827cceb]                    
#10 majx(main+0xd5) [0x81eaa31]                                     
#11 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#12 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cd096e]     
#2 /usr/lib32/libX11.so.6 [0xf7ea7619]                              
#3 /usr/lib32/libX11.so.6(XMatchVisualInfo+0x40) [0xf7e9d530]       
#4 majx [0x83a3c43]                                                 
#5 majx(X11_GetVideoModes+0x403) [0x83a414b]                        
#6 majx [0x8381930]                                                 
#7 majx(SDL_VideoInit+0x284) [0x837ed78]                            
#8 majx(SDL_InitSubSystem+0x39) [0x83765a5]                         
#9 majx(SDL_Init+0x18) [0x8376684]                                  
#10 majx(Instance__10CYLinuxApp+0x5f) [0x827cceb]                   
#11 majx(main+0xd5) [0x81eaa31]                                     
#12 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#13 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cd0891]   
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf7ea8494]               
#3 majx(SDL_XineramaIsActive+0x77) [0x83a99f7]                      
#4 majx(X11_GetVideoModes+0x665) [0x83a43ad]                        
#5 majx [0x8381930]                                                 
#6 majx(SDL_VideoInit+0x284) [0x837ed78]                            
#7 majx(SDL_InitSubSystem+0x39) [0x83765a5]                         
#8 majx(SDL_Init+0x18) [0x8376684]                                  
#9 majx(Instance__10CYLinuxApp+0x5f) [0x827cceb]                    
#10 majx(main+0xd5) [0x81eaa31]                                     
#11 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#12 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cd096e]     
#2 /usr/lib32/libX11.so.6 [0xf7ea7619]                              
#3 /usr/lib32/libX11.so.6(XCreateColormap+0x26) [0xf7e7c1d6]        
#4 majx [0x8381a5d]                                                 
#5 majx(SDL_VideoInit+0x284) [0x837ed78]                            
#6 majx(SDL_InitSubSystem+0x39) [0x83765a5]                         
#7 majx(SDL_Init+0x18) [0x8376684]                                  
#8 majx(Instance__10CYLinuxApp+0x5f) [0x827cceb]                    
#9 majx(main+0xd5) [0x81eaa31]                                      
#10 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#11 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cd0891]   
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf7ea8494]               
#3 majx(SDL_XF86VidModeGetGamma+0x96) [0x83a556e]                   
#4 majx [0x83a2db4]                                                 
#5 majx(X11_SaveVidModeGamma+0x37) [0x83a2e57]                      
#6 majx [0x8381ae8]                                                 
#7 majx(SDL_VideoInit+0x284) [0x837ed78]                            
#8 majx(SDL_InitSubSystem+0x39) [0x83765a5]                         
#9 majx(SDL_Init+0x18) [0x8376684]                                  
#10 majx(Instance__10CYLinuxApp+0x5f) [0x827cceb]                   
#11 majx(main+0xd5) [0x81eaa31]                                     
#12 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#13 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cd096e]     
#2 /usr/lib32/libX11.so.6 [0xf7ea7619]                              
#3 /usr/lib32/libX11.so.6(XCreateWindow+0x26) [0xf7e9dbc6]          
#4 majx [0x83814e9]                                                 
#5 majx [0x8381b0e]                                                 
#6 majx(SDL_VideoInit+0x284) [0x837ed78]                            
#7 majx(SDL_InitSubSystem+0x39) [0x83765a5]                         
#8 majx(SDL_Init+0x18) [0x8376684]                                  
#9 majx(Instance__10CYLinuxApp+0x5f) [0x827cceb]                    
#10 majx(main+0xd5) [0x81eaa31]                                     
#11 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#12 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf7cd0891]   
#2 /usr/lib32/libX11.so.6(_XReply+0x254) [0xf7ea8494]               
#3 majx(SDL_XF86VidModeQueryVersion+0x8f) [0x83a52b3]               
#4 majx(SDL_XF86VidModeGetModeLine+0x5d) [0x83a5645]                
#5 majx [0x83a3ab7]                                                 
#6 majx(X11_EnterFullScreen+0x76) [0x83a4772]                       
#7 majx [0x83827d4]                                                 
#8 majx [0x838297a]                                                 
#9 majx(SDL_SetVideoMode+0x1b3) [0x837f5b3]                         
#10 majx(CreateOSWindow__10CYLinuxAppPUliiiiiPc+0x50) [0x827c938]   
#11 majx(main+0x25f) [0x81eabbb]                                    
#12 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]           
#13 majx(XMapRaised+0x39) [0x813b901]                               
Locking assertion failure.  Backtrace:                              
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7cd07c7]                         
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf7cd096e]     
#2 /usr/lib32/libX11.so.6 [0xf7ea7619]                              
#3 /usr/lib32/libX11.so.6(XMoveResizeWindow+0x25) [0xf7e7b435]      
#4 majx(X11_EnterFullScreen+0xd2) [0x83a47ce]                       
#5 majx [0x83827d4]                                                 
#6 majx [0x838297a]                                                 
#7 majx(SDL_SetVideoMode+0x1b3) [0x837f5b3]
#8 majx(CreateOSWindow__10CYLinuxAppPUliiiiiPc+0x50) [0x827c938]
#9 majx(main+0x25f) [0x81eabbb]
#10 /lib32/libc.so.6(__libc_start_main+0xe5) [0xf7ce9685]
#11 majx(XMapRaised+0x39) [0x813b901]
majx: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Majesty: The Northern Expansion 1.1.0, built on x86
SIGABRT caught: "My service ends....."

This is a BUG, please report it to http://support.linuxgamepublishing.com
Stack dump:
{
        [0xf7f97400]
}

orion@universe:~/Desktop/My Tribe$ /bin/bash: line 0: kill: (8367) - No such process
/bin/bash: line 0: kill: (8367) - No such process
/bin/bash: line 0: kill: (8367) - No such process

```

---

### Post by binbash on 2009-02-23
I will fill a bug report for SURE, but i found this at README : 

```

Q) When running full-screen, the game runs in the center of the screen, 
surrounded by black bars.

A) SDL, the graphics and sound library used by the game, attempts to switch 
the X server to the game's resolution.  If the X server does not support the 
required resolution, it will draw the game's video area in the middle of the
display area and fill the remainder of the screen with black.

You may use your distribution's configuration tools to alter the resolution 
of your X server, or you can edit the X configuration files by hand.  (If 
you choose the latter, please back up your X configuration files before 
making any changes!)

If you are using XFree86, you can edit /etc/X11/XF86Config-4 and look for 
a section like:

Section "Screen"
    Identifier "screen1"
    Device      "Generic SVGA"
    Monitor     "Generic VGA"
    DefaultColorDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x1024"
	ViewPort    0 0
    EndSubsection
EndSection

Change the "Modes" line to include additional resolutions, e.g.:

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
	ViewPort    0 0
    EndSubsection

The PPC version does not always switch resolutions correctly.

```

I guess majesty does not pull the resolution from the xorg, and it crashes.

---

### Post by binbash on 2009-03-26
This is fixed at ubuntu jaunty, i can play fullscreen now

---

