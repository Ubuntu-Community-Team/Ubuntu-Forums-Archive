---
title: "upgrade 6.10 -&gt; 7.04 xdmcp failed"
date: 2007-03-25
forum: Desktop Environments
---

### Post by flyrc51 on 2007-03-25
Hi 

I have been  using 6.10, it has worked flawlessly.
Normally I connect via xdmcp from cygwins X server, anyway my Linux box is just for playing  with so I figured I would jump on the 7.04 Beta.
Everything went very smoothly, I used ```
update-manager -d
```
I played with it for a while in the basement and decided it was stable and so I turned off the monitor and went upstairs and tried to connect via my normal ```
 C:\cygwin\usr\X11R6\bin\XWin.exe   -query 192.168.1.103
``` but all I got was a gray screen where I expected an orange login screen.
I double checked that the Linux box had not picked up a different IP, and then I went back to the basement and used the xdmcp login option on the Linux box to log into its self and this worked fine. I double checked that I had changed the 'Style' from 'Remote login disabled' to same as local and I even tripple check that the firewall could not be a issue (I am behind a router firewall) with```
 iptables -F
``` to turn any firewall off.
Back upstairs (getting fit now!) I checked and my samba drives are all working, ssh is fine, but xdmcp gives the log below which shows the initial attempt and one retry.
This is not urgent, and I know it is a Beta, but I think the problem just needs me to reinstall or reset some elements, any suggestions  welcome as configuring this aspect of a Linux set up is black magic to me.

```
Welcome to the XWin X Server
Vendor: The Cygwin/X Project
Release: 6.8.99.901-4

Contact: cygwin-xfree@cygwin.com

XWin was started with the following command line:

/usr/X11R6/bin/XWin -query 192.168.1.103

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
winValidateArgs - g_iNumScreens: 1 iMaxConsecutiveScreen: 1
(II) XF86Config is not supported
(II) See http://x.cygwin.com/docs/faq/cygwin-x-faq.html for more information
winDetectSupportedEngines - Windows NT/2000/XP
winDetectSupportedEngines - DirectDraw installed
winDetectSupportedEngines - DirectDraw4 installed
winDetectSupportedEngines - Returning, supported engines 00000007
winSetEngine - Using Shadow DirectDraw NonLocking
winAdjustVideoModeShadowDDNL - Using Windows display depth of 32 bits per pixel
winFinishScreenInitFB - Masks: 00ff0000 0000ff00 000000ff
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shar
ed memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409)
(--) Using preset keyboard for "English (USA)" (409), type "4"
Rules = "xorg" Model = "pc105" Layout = "us" Variant = "(null)" Options = "(null
)"
(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap
(--) 5 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from
list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from
 list!
winPointerWarpCursor - Discarding first warp: 637 496
XDM: too many retransmissions, declaring session dead
FreeFontPath: FPE "/usr/X11R6/lib/X11/fonts/misc/" refcount is 2, should be 1; f
ixing.
(II) XF86Config is not supported
(II) See http://x.cygwin.com/docs/faq/cygwin-x-faq.html for more information
winDetectSupportedEngines - Windows NT/2000/XP
winDetectSupportedEngines - DirectDraw installed
winDetectSupportedEngines - DirectDraw4 installed
winDetectSupportedEngines - Returning, supported engines 00000007
winSetEngine - Using Shadow DirectDraw NonLocking
winFinishScreenInitFB - Masks: 00ff0000 0000ff00 000000ff
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shar
ed memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409)
(--) Using preset keyboard for "English (USA)" (409), type "4"
Rules = "xorg" Model = "pc105" Layout = "us" Variant = "(null)" Options = "(null
)"
(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap
(--) 5 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from
list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from
 list!
```

---

