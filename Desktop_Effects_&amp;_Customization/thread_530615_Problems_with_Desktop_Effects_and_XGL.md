---
title: "Problems with Desktop Effects and XGL"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by blueyelabs on 2007-08-20
Ok, I recently installed ubuntu on a secondary slave HD on my Dell Dimension 8400 with Radeon X800 GT graphics card.
I got the graphics drivers working, with fgrlx (or whatever it is) working, after considerable trouble.

However, try as I might I can't get ANY desktop effects.When trying to first access the "desktop effects" item in the system preferences menu, I get the message "Composite Extension not available".
Annoying.
Then I tried installing Beryl, Emerald and Compiz. Their settings managers work perfectly, but without effect, they don't *do* anything... I then tried installing/configuring XGL, which didn't work because when I start an XGL session I get a **really** messed up screen which I can't really distinguish anything on, so no XGL. How *do* I get a theme manager // desktop  effects thing going?

---

### Post by Parms on 2007-08-20
> **blueyelabs said:**
> Ok, I recently installed ubuntu on a secondary slave HD on my Dell Dimension 8400 with Radeon X800 GT graphics card.
I got the graphics drivers working, with fgrlx (or whatever it is) working, after considerable trouble.

However, try as I might I can't get ANY desktop effects.When trying to first access the "desktop effects" item in the system preferences menu, I get the message "Composite Extension not available".
Annoying.
Then I tried installing Beryl, Emerald and Compiz. Their settings managers work perfectly, but without effect, they don't *do* anything... I then tried installing/configuring XGL, which didn't work because when I start an XGL session I get a **really** messed up screen which I can't really distinguish anything on, so no XGL. How *do* I get a theme manager // desktop  effects thing going?

That is the same screen I'm getting on XGL.. I can tell it's my desktop but can't tell what anything is. I think it's because 64 bit maybe. The XGL guides I tried says 32bit.

---

### Post by mysticmatrix on 2007-08-20
> **blueyelabs said:**
> Ok, I recently installed ubuntu on a secondary slave HD on my Dell Dimension 8400 with Radeon X800 GT graphics card.
I got the graphics drivers working, with fgrlx (or whatever it is) working, after considerable trouble.

However, try as I might I can't get ANY desktop effects.When trying to first access the "desktop effects" item in the system preferences menu, I get the message "Composite Extension not available".
Annoying.
Then I tried installing Beryl, Emerald and Compiz. Their settings managers work perfectly, but without effect, they don't *do* anything... I then tried installing/configuring XGL, which didn't work because when I start an XGL session I get a **really** messed up screen which I can't really distinguish anything on, so no XGL. How *do* I get a theme manager // desktop  effects thing going?

Please give the output of this command i.e type it in terminal and paste the output
```

glxinfo
```

---

### Post by Parms on 2007-08-20
parms@parms-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
parms@parms-laptop:~$

---

### Post by Jouke74 on 2007-08-20
Given that it says "Mesa" means that your FGLRX is not working correctly yet...
First sort that out.

Use the restricted driver manager and the driver from the Feisty repository! The newest ATI driver does not work well with XGL with a garbled screen as a result (which is what you describe).

Then check : [http://ubuntuforums.org/showthread.php?t=511166&highlight=compiz+XGL+ATI](http://ubuntuforums.org/showthread.php?t=511166&highlight=compiz+XGL+ATI)

It is for Xubuntu, but there is a working note about Gnome as well.

---

### Post by Parms on 2007-08-20
> **Jouke74 said:**
> Given that it says "Mesa" means that your FGLRX is not working correctly yet...
First sort that out.

Use the restricted driver manager and the driver from the Feisty repository! The newest ATI driver does not work well with XGL with a garbled screen as a result (which is what you describe).

Then check : [http://ubuntuforums.org/showthread.php?t=511166&highlight=compiz+XGL+ATI](http://ubuntuforums.org/showthread.php?t=511166&highlight=compiz+XGL+ATI)

It is for Xubuntu, but there is a working note about Gnome as well.

I have just started from scratch (new install of ubuntu 7.04)

What is Xubuntu? I don't understand. I also don't see the part about the working part in gnome?

So if that driver doesn't work how should I download my driver? Should I use envy or the restricted device manager as referred to in the guide posted above?

---

### Post by Rupertronco on 2007-08-20
Parms, 

Xubuntu is Ubuntu, but a lighter version. It uses the XFCE desktop environment as opposed to Gnome (regular Ubuntu). 

Use the restricted driver manager that is in Ubuntu, and if that doesn't work, try envy. You have to make sure to remove pre-existing drivers before you install the new ones as well.

---

### Post by Parms on 2007-08-20
> **Rupertronco said:**
> Parms, 

Xubuntu is Ubuntu, but a lighter version. It uses the XFCE desktop environment as opposed to Gnome (regular Ubuntu). 

Use the restricted driver manager that is in Ubuntu, and if that doesn't work, try envy. You have to make sure to remove pre-existing drivers before you install the new ones as well.

OK that clears up one thing...

I tried both methods of above... still a garbled screen when I load into XGL

One thing I noticed... When I use code: glxinfo | grep direct
when direct rendering comes out no... I get the garbled screen.
when direct rendering is yes... XGL will not load into the desktop (just stays with the x's background and X mouse cursor for indefinate.

---

### Post by Rupertronco on 2007-08-20
What graphics card are you using? The built-in AiGLX works much better than XGL (It's a bit out-dated).

---

### Post by Parms on 2007-08-20
Success fully reinstalled Ubuntu, and updated, and did the drivers.

I installed my ATI drivers.
I installed XGL
I installed compiz

I am in XGL with Gnome now.. which finally works fine for some odd reason. Either way when I load compiz I have the following

parms@parms-laptop:~$ compiz
There is already the metacity win manager running, you should use the --replace option to override it
parms@parms-laptop:~$ compiz --replace
Backend     : ini
Integration : true
Profile     : default
Adding plugin snap (snap)
Adding plugin png (png)
Adding plugin rotate (rotate)
Adding plugin inotify (inotify)
Adding plugin decoration (decoration)
Adding plugin 3d (3d)
Adding plugin kiosk (kiosk)
Adding plugin tile (tile)
Adding plugin mblur (mblur)
Adding plugin resizeinfo (resizeinfo)
Adding plugin atlantis (atlantis)
Adding core settings (General Options)
Adding plugin flash (flash)
Adding plugin svg (svg)
Adding plugin workarounds (workarounds)
Adding plugin fakeargb (fakeargb)
Adding plugin colorfilter (colorfilter)
Adding plugin text (text)
Adding plugin plane (plane)
Adding plugin wobbly (wobbly)
Adding plugin expo (expo)
Adding plugin splash (splash)
Adding plugin blur (blur)
Adding plugin put (put)
Adding plugin resize (resize)
Adding plugin thumbnail (thumbnail)
Adding plugin keybinding (keybinding)
Adding plugin ring (ring)
Adding plugin imgjpeg (imgjpeg)
Adding plugin gotovp (gotovp)
Adding plugin scale (scale)
Adding plugin gears (gears)
Adding plugin cube (cube)
Adding plugin neg (neg)
Adding plugin bench (bench)
Adding plugin trailfocus (trailfocus)
Adding plugin animation (animation)
Adding plugin glib (glib)
Adding plugin scalefilter (scalefilter)
Adding plugin cubereflex (cubereflex)
Adding plugin bs (bs)
Adding plugin screenshot (screenshot)
Adding plugin crashhandler (crashhandler)
Adding plugin addhelper (addhelper)
Adding plugin switcher (switcher)
Adding plugin screensaver (screensaver)
Adding plugin clone (clone)
Adding plugin move (move)
Adding plugin quickchange (quickchange)
Adding plugin place (place)
Adding plugin minimize (minimize)
Adding plugin ezoom (ezoom)
Adding plugin firepaint (firepaint)
Adding plugin extrawm (extrawm)
Adding plugin zoom (zoom)
Adding plugin shift (shift)
Adding plugin winrules (winrules)
Adding plugin reflex (reflex)
Adding plugin fade (fade)
Adding plugin vpswitch (vpswitch)
Adding plugin water (water)
Adding plugin widget (widget)
Adding plugin mousegestures (mousegestures)
Adding plugin opacify (opacify)
Adding plugin annotate (annotate)
Adding plugin video (video)
Adding plugin regex (regex)
Adding plugin dbus (dbus)
Adding plugin scaleaddon (scaleaddon)
Adding plugin fadedesktop (fadedesktop)
Adding plugin showdesktop (showdesktop)
Adding plugin fs (fs)
Adding plugin group (group)
Adding plugin cheatsheet (cheatsheet)
Adding plugin wallpaper (wallpaper)
Adding plugin wall (wall)
Adding plugin snow (snow)
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity


then it stops? Don't know what to do or anything. Wonder if I need to install more things. Like the emerald or anythng else. Also what is the differnce between compiz and compiz-fusion.

This was the link I used for compiz [http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64](http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64)

This is what I had earlier for an error 

parms@parms-laptop:~$ KEY=DD800CD9; sudo gpg --keyserver subkeys.pgp.net --recv $KEY && sudo gpg --export --armor $KEY
Password:
gpg: requesting key DD800CD9 from hkp server subkeys.pgp.net
gpg: key 81836EBF: "Treviño (3v1n0) <trevi55@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBESfI64RBAC+CSSPbUzfo5RzoGrkuYGcmj/0mBS66QgaehMbd4Czbl32loMI
FSNKLWxS0yeyVMceiEm//NNUi+y7yFJVV9AuGJZx4ub1IG5YcAlpB3lcJ5G2nz3P
n3KGmjQ8sE8+w7zqkaICpDxyddyCIqUbKDbnJ7ti+nf4V9SnW4EcMQvJWwCg43TS
UvI+S2tbK/EVPl+YehpBTGcD/0Kaf6CDxFubZgm2jTGsvEOH1kyGQHXWKfDlHAq+
lygEHXR3OlcLDlSlOZ9DAU3+gfYU8Ukt+xEjTd97r6XHOxF3nuu6h1ZLVZ7k2Fqr
yEnt1dRMmhL2FA1xOaXvobHObg4UvgnMExR4MYpulKU5hMO8w4BO0Xy34CJg2J0a
5adEA/4nk8mWS2AYG2qUOgE0jvMgrWUsPbWtyNjz3u2xTi9Od5IscX72m8Vuy+4E
kYTHwj+/hDq/70Ee6OUKaMcyeLJm61EierAqWWDmT5gK+6jNIheqALhApSRJUS0k
TPzK1zLx8Nb/g+NCXKb9N4h9UAPe3hHwlY7lTDgTbOJsL3vd1LQkVHJldmnDsW8g
KDN2MW4wKSA8dHJldmk1NUBnbWFpbC5jb20+iEYEEBECAAYFAkVpNjwACgkQOn+U
ZZehGtLjEACcDOgpS2xcL3oG3C8q2CrjpU/fWBQAoNtk/fmA7Ai7z70PH8hP2WUM
hL+diEYEEBECAAYFAkXwLGwACgkQRdSMfNz8P9AqQACfZfXR93l+GJMiriB9agVv
62rUKQQAn2OFf3Vu8rrCIIBANpPOhtiFwQLhiF0EExECAB0FAkSfI64GCwkIBwMC
BBUCCAMEFgIDAQIeAQIXgAAKCRDoPQiUgYNuv4LnAJ9hZ6oRDLGYwOmELmad5eSI
L2w+YQCglomn/N6zwM7lDDG4XhdRaqMgtmCIYAQTEQIAIAYLCQgHAwIEFQIIAwQW
AgMBAh4BAheABQJFOBf0AhkBAAoJEOg9CJSBg26/wxoAoMZlKMPcyJ52gBXukLT2
U9DLk8J7AKDIQ0/p5LQbzOUvPhbOEuC7/hYBuokBIgQQAQIADAUCRTgW0AUDABJ1
AAAKCRCXELibyletfGTcB/0bzlU+MVHgqLZhoyT4DIxvrGHsxQIId9ACKiY3E81R
KKKcsA2IhE9/6ljVhS9QXiTyNjNEJYEQ3UKx7F30lckcD/JZ4JknaqFduVDcLLC0
3cKmvPtfItkG3975kIMOgGpV2JDH7drMcqwpXVKc5YUd7ufhptyHyMu/nf1Z6WXW
w6CEf/hZSkbnktAA1lMjxoGRO7MpiwCy9I8l7lAjIJ34QtmnGKG+EVKYIhF3RgnL
P004mlD1LSTtx461ArCPXBj1g2xLrtJ7Yb/VDg8jLSzhWYaXgbH6ZekF9gUMeLYq
kxyy5RugFkmV8X3qYOV598tjNLvFB4wYpzoSJZVMR0ExtDFNYXJjbyBUcmV2aXNh
biA8dHJldmk1NStNYXJjby5UcmV2aXNhbkBnbWFpbC5jb20+iGAEExECACAFAkU4
F+0CGyMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRDoPQiUgYNuv25sAKCqfS8L
Qp3BtTR+XL+QySFsbXWsZwCfZKCUhvCeyH5fwJls4urtL6wk3IS0OVRyZXZpw7Fv
IFVidW50dSBSZXBvc2l0b3J5IDx0cmV2aTU1K3JlcG9zaXRvcnlAZ21haWwuY29t
PohgBBMRAgAgBQJFOBfaAhsjBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQ6D0I
lIGDbr/EvwCg1AJbMAsBuxJQYVbSfN9M2Sc+B+8AoKznyvlQTbRGsZd6QnMckWXi
KwEruQGiBEU26EYRBADMfXn0Ryez2rK1k0WuRWRCb7IigRU/ikADW2W5hwil0RGU
+nV3WqxdA1TsG+3MwJSmi/v5Qm5EB7uNRl+MOGnuLwPXEFEadDfqfyO7L25uk0hE
3ZmcnAsSFNwTEDJ2SSO9OaU8gt0lUE90wasR0dKDGqjo58L47UFX1YFV/GDVMwCg
zvSkbQZyuxtq42lIBClc90ODRBED/RKK9nr1GtNV1RABftfraRV0i9hf4NbKE4N1
ZhvK4iPvEI+S4UveiH818fF2SZWXVJAKmxS7v/nlgyPwRi0Cz24TAkg2iYmcYrN7
PRsNN/7JoZQr7Y2qWM2rW3mGPaZHKMjo2OQFQsHB2cL68QEhWmpO+xaerZdhXYqd
Eh1sCeyeA/0QU3ZpPLlNhpN/JX9qo7iW8BAMEDzwNvq85syqIRGL3r2y4s5UaxJ2
nYlgcX2W93aiem5bsR2Ex0+ENcZKgE5Thkvh3eHeOGEzHEf3bXiRh6az4p8TuzXj
KW+JnTqBwSDVrhqS4m8muvk+vv7f7TEMu+VVlsz4kj/ZYEOWe9jlvYhJBBgRAgAJ
BQJFNuhGAhsCAAoJEOg9CJSBg26/aYIAn27ER8iOrrB3NbFt5Q72szaCFTPNAJ47
yJgSuYznWt9uVQTnWenZ8Bbr7bkEDQREnyPnEBAArhqGIGhPzr/uWpJSD6HWYacl
rGx/EuLe1B8cDVHiev8AYxojQVUZMIqE/hv12duzthw1uKTw3swtDjyihMGJIZzX
ltktW7I7dI+sI8IpzB9DAs43HNNKaz/vMilO6eZ2aGr+3EB+uaQpzNRMRwbZHf0N
7Vl+8ntTydxNGqNmirgXzUMmRMqHSTb+fJV+E8N2SKyB3Cv/BsyZva2iHEvWNyvp
4/InyHNfNlWgqykZqkvxQ437WVneOxFexdwmwGSP+j93cdM90cI7xf0ZMcgE1ioa
Ox2O2kxA+FURsV6VJFmyHotYBiIjkV8KwyruTJ08cDrBF10gspZOveuWCH7gegns
Cfi1UYrbUVvRheKmHT9wtJyTKMLJZq6tGo30XDMBRpg0KklHoji+NIkUzVf12IMK
UCQ9lSRqmT5mayYW+L5AT94xkWWUMze4sIcwexwkJMyuPkPxavRBIy95LGFirDXP
L4ltKhkRTCTaGu/2YVpqkNajr4qXdOxeSeeO4RB61FJI8lxv1+ZPjWz9Z06gVuqp
pHbTs8K51DWLHD0JN6LBqAFy5KKiqpDpsT7iUPuyowo0zH+kkFdmnxbeR55cE2cW
WNEFKK0eVj8644mKTZNANjT0YzxfiR4hwUJQk11tKzGJzN/WEpLwt37cQMu6BLJF
XBaNXc0XjYXwnaZN+nMAAwUQAJS9tuJqhGJAsPC+qherw2bG/WWtAM0wp8Mbqe9z
8zt0heBSnpA6SJBUbdFZAcEcFGSOjMQrCdfPv8ytQoT4e3D6cF5t7VFqdqfKprP7
+6dVGmOk3gjeUtn+J2/wExpc1mqkhzh1cm5kpiCRE4xJIj7Omr73ctiQma4LbO9H
mkvS/T3kbGQpSTb35yFw+bbEbaji3olU68tsM6ULytxPZVq5Rg/vT55xCRtoy9On
qJCAKJrs+ZD31lxQObv0H/JZlz0ViSOQp6vAw36BCnRAF1SVkk1FP0xBvK9My8WC
E8If6hGjsay1zecC/mQ9WXquLMH3mPawuzgCPYuynkip4GLPL85XEze885SDGaeX
f/XaTuuftI2HnFAEbOLCSJlR8p6YeSoqJZoA/emX8VtxORLI/7phQ4+X1WF/Pl92
2zniwL+WLklr8mNj8vxEvimEoodjUq8ahjXy8fmgOM1iqklDoPNM58r/3zISObIj
dYiI7YJXga0+pB6qT36EjVIW0ZpmuROa2W1ctzXFnlpR8DbGvEdTsfQe+hSJhBOW
cX9CSQAGPkemOeS/PJQkhjMSzjsVIiUYVi0SwN3tESYtd2YR5/DWp+of7TDJQtoM
pau9C/mOzV6kEA1L53CDWYaMU82q+2EpIgqgGXOkMtb1oztsHVxRq95w0C6Ycvcv
gWEUiEYEGBECAAYFAkSfI+cACgkQ6D0IlIGDbr/vggCfa2MTPcbMzsxveeDkNtxJ
TDZkCcEAoJaoA4YkpFmuGWlubK5JTha8BVC2
=Y8St
-----END PGP PUBLIC KEY BLOCK-----
parms@parms-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                    
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                    
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Sources
Fetched 14.4kB in 2s (5345B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
parms@parms-laptop:~$ 


Hmmmm... don't know what else to do? When I do load compiz I see my screen refresh, but nothing happens. 

So close, yet so far.

---

### Post by mysticmatrix on 2007-08-21
> Note: This repository is not officially supported.

It's maintened by Treviño, using this makefusiondebs script that fetches the latest git snapshot, and builds it with some patches and configuration ennhancements (all available here)...

This repo can be considered safe, but as we always say with bleeding edge software: Use at your own risk! Since the packages available on the repository are newer than the official releases, using it could cause breaking official upgrades, but you may always downgrade to standard versions using APT. 

This might be the reason of your trouble.
Please try the official repositories at[ Ubuntu wiki]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

STEP BY STEP:

1) Open terminal and type
```
sudo apt-get --purge remove compiz* libcompizconfig*
```

2) Then remove the previous repositories that you added in /etc/apt/sources.list

3) Follow the Ubuntu Wiki

EDIT: However, I don't think so that official repository is available for **AMD64**

---

### Post by Parms on 2007-08-21
I'm at a clean install now >> up the part with XGL. 
I'm logged in with Gnome - XGL (graphics are normal)

Do you know a guide that is up to date and works with 64bit? 

Because honestly I have re-installed 8 times today now. One time for each guide. 

These are the ones I tried so far.. 
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

Autoscript.. really messes up my compuer and refuses to load (guess it's buggy)
Amaranth's doesn't install any of the compiz packages
Trevino's doesn't install compiz packages
ATI cards one.. The script for installing the compiz files .. says it can't find them.

Are these compiz files down or what? How come there not found when I copy and paste these command line?

Is there anyone out there that has ran compiz-fusion with ATI 64bit successfully???

---

### Post by Jouke74 on 2007-08-21
You could just try to "enable desktop" effects under the "preferences" menu as a starter (I assume your XGL server is up and running now). The enable desktop effects is an older version of Compiz that is somewhat stable and you could check out if that one runs ok. It is delivered with Ubuntu Feisty Fawn so no need for fancy "go through others recipes" / scripting / compiling etc. (which is not for beginners, although you need start somewhere I have to admit :) )

Take note that in Ubuntu we have 64 bit (AMD64) and 32 bit (I386) software, which are not mixing well together as given in earlier posts. If you use AMD64, then use the 64 bit packages and posts / scripts / methods that use 64 bit as well.

Also read about the synaptic package manager and apt-get and know how to use it's functions. In order to compile the new compiz (which is basically what you *were* doing) you need for example the development libraries and the Build-essential package. Probably one or more of these "dependencies" is still missing.

Compiz is still in development, what could have worked fine two weeks ago, might be broken today...

Yes I have got it running fine (under two different methods even): AMD64 + Compiz + XGL + ATI X1600pro.

Finally, you don't need to reinstall Ubuntu everytime it crashes or a script stops, one reboot should be fine or even "ctrl-c". Afterwards clean-up what you installed (remove option of apt-get) and delete the compile directories and start over. To correct stuff you can still log into the normal Gnome session without the XGL server. Also I suggest that if you start to edit system files do a 

> "sudo cp <name of the file>.conf <name of the file>.back" first.

---

### Post by blueyelabs on 2007-08-21
Here are the glx results:

```

gid@Beast:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GT
OpenGL version string: 2.0.6747 (8.40.4)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object, 
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x3a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x42 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x45  8 pc  1  0  1 c  y  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x46  8 pc  1  0  1 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x47  8 gs  1  0  1 c  y  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48  8 gs  1  0  1 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by mysticmatrix on 2007-08-21
> **blueyelabs said:**
> Here are the glx results:

```

gid@Beast:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GT
OpenGL version string: 2.0.6747 (8.40.4)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object, 
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x3a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x42 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x45  8 pc  1  0  1 c  y  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x46  8 pc  1  0  1 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x47  8 gs  1  0  1 c  y  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48  8 gs  1  0  1 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

Your graphics drivers are all correctly set up. Now all you need is to start XGL and then start Compiz.
Please try to reinstall XGL by [use of this link.]("https://help.ubuntu.com/community/CompositeManager/Xgl")

Follow the method A for ATI card and then report if you get a usable XGL session. Once XGL is running, you will be able to get Compiz running.

---

### Post by blueyelabs on 2007-08-21
I tried, XGL still messes up the graphics (i can tell that there is a desktop and two panels, but that's it... all fuzzy etc) and I can't use ```
compiz --replace
``` because I get this:
```

gid@Beast:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

I tried to reinstall XGL etc, still doesn't work... help?

---

