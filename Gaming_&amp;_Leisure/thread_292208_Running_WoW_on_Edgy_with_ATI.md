---
title: "Running WoW on Edgy with ATI"
date: 2006-11-03
forum: Gaming &amp; Leisure
---

### Post by myname on 2006-11-03
Has anyone had any luck with ATI cards, WoW, Wine 0.9.24 and Edgy?

I have an ATI X1600 with 512 megs of RAM, and with a default install of Edgy, installed the ATI Drivers by following the information here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

Then installing Wine via Synaptec.  

WoW launches, but as soon as I go in, I start getting graphic anomolies and the system will lock up in about 10 seconds.

If anyone has any information on this, that would be great. If I am doing something wrong during the installation of one or all of the software above, please let me know.  

Thanx.

--Kevin

---

### Post by Ferrat on 2006-11-03
> **myname said:**
> Has anyone had any luck with ATI cards, WoW, Wine 0.9.24 and Edgy?

I have an ATI X1600 with 512 megs of RAM, and with a default install of Edgy, installed the ATI Drivers by following the information here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

Then installing Wine via Synaptec.  

WoW launches, but as soon as I go in, I start getting graphic anomolies and the system will lock up in about 10 seconds.

If anyone has any information on this, that would be great. If I am doing something wrong during the installation of one or all of the software above, please let me know.  

Thanx.

--Kevin

Im running WoW on Edgy with Wine 0.9.24 and ATi card.. 

First have clean install of Edgy 

The install wine deb from this link [http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz](http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz)  ( all creds to reiki for figuring out how to make a working .deb for Edgy and to Garyu for making one thread: [http://ubuntuforums.org/showthread.php?t=290761](http://ubuntuforums.org/showthread.php?t=290761) )

The get the [COLOR="Red"]ati-driver-installer-8.30.3.run[/COLOR] from ATi's homepage and install it bu using 

NOTICE: some things like module-assistant is in Multi och Univers resps so make sure you got them added and active (you can fix that in synaptic)

```

sudo apt-get update

sudo apt-get install module-assistant build-essential

sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

```

Now you got all you need to build

the do
```

sudo mv /bin/sh /bin/sh.old

sudo ln -s /bin/bash /bin/sh

```

This will make sure you don't get an error trying to create your ATi .debs

To creating and installing

CREATING:
```

sudo sh ati-driver-installer-8.30.3.run --buildpkg Ubuntu/6.10

```

this will output the ATi .debs 
Now you need to run [COLOR="Red"]sudo gedit /etc/X11/xorg.conf[/COLOR] and add this to the end of the file 

```

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Now you need to edit [COLOR="Red"]sudo gedit /etc/default/linux-restricted-modules-common[/COLOR] and make sure it says 
```

DISABLED_MODULES="fglrx"

```
in the end of the file.

Now install the deps by just opening them with GDebi Package installer, you should have that option when you click on them. 

if you can't install something it will say why, for ex. xorg-driver-fglrx might be installed (shouldn't but just incase it is, just make a complete removal in synaptic on that package. 

Now build the Kernel

```

sudo rm /usr/src/fglrx-kernel*.deb

sudo module-assistant prepare

sudo module-assistant update

sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo depmod -a

```

some cleanup
```

sudo mv /bin/sh.old /bin/sh

```

That should install the kernel and now run [COLOR="Red"]winecfg[/COLOR] to setup wine 

now restart you computer and wo'la you should be able to run wow and even in some places get a preformance boost and overall IMO it runs more smooth then in Dapper with 0.9.23

I don't think I forgot anything but I've might have so if it doesn't work say so here, might be that I forgot to meantion something =)

---

### Post by dbd on 2006-11-03
wow, I just used your howto to install the new drivers to replace the xorg-driver-fglrx and my fps in fgl_glxgears went from 675ish to 975ish! Thats incredible, thank you! :D

---

### Post by myname on 2006-11-03
Thanx for the detailed instructions, however, after doing a fresh install of Ubuntu Edgy 32, then installing wine by downloading from your link and double clicking the .deb file, I went to install the ATI drivers per your instructions.

I received the following:

kevin@homepc:~/download/drivers/ati$ install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
install: target `linux-headers-2.6.17-10-generic' is not a directory

Not sure what I did or didn't do right.  Any help would be appreciated.

--Kevin

---

### Post by Ferrat on 2006-11-03
> **dbd said:**
> wow, I just used your howto to install the new drivers to replace the xorg-driver-fglrx and my fps in fgl_glxgears went from 675ish to 975ish! Thats incredible, thank you! :D

ohh my bad sudo apt-get got lost ^^ fixed now

---

### Post by myname on 2006-11-03
Thanx, however, now when I issue the following:

sudo module-assistant build fglrx


I get the following error:

&#9474; Build log starting, file:                                                  &#8593; 
 &#9474; /var/cache/modass/fglrx-kernel-src.buildlog.2.6.17-10-generic.1162602899   &#9646; 
 &#9474; Date: Fri, 03 Nov 2006 20:14:59 -0500    


pardon my n00bness for this. 

> Now install the deps by just opening them with GDebi Package installer, you should have that option when you click on them. 
Should I have double clicked the debs, or should I have continued on with your command line installations?

The reason why I ask is, I've seen a hundred different ways to install the ATI drivers, and I'm not sure which way is better than the others.

--Kevin

---

### Post by Ferrat on 2006-11-03
> **myname said:**
> Thanx, however, now when I issue the following:

sudo module-assistant build fglrx


I get the following error:

&#9474; Build log starting, file:                                                  &#8593; 
 &#9474; /var/cache/modass/fglrx-kernel-src.buildlog.2.6.17-10-generic.1162602899   &#9646; 
 &#9474; Date: Fri, 03 Nov 2006 20:14:59 -0500    


pardon my n00bness for this. 

 
Should I have double clicked the debs, or should I have continued on with your command line installations?

The reason why I ask is, I've seen a hundred different ways to install the ATI drivers, and I'm not sure which way is better than the others.

--Kevin

the error is cause it's not installed, just right-click the debs and select open with GDebi Package installer :)

---

### Post by myname on 2006-11-03
Thanx, I did that.

Now a couple of things.  glxgears -printfps gives me uber fast FPS numbers, however, the following happens:

1)  when I drag windows on the screen they are REALLY slow at redrawing
2)  ati$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

3)  fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Should #2 be YES for direct rendering, and should #3 be ATI FGLRX drivers with Opengl?

--Kevin

---

### Post by Ferrat on 2006-11-03
> **myname said:**
> Thanx, I did that.

Now a couple of things.  glxgears -printfps gives me uber fast FPS numbers, however, the following happens:

1)  when I drag windows on the screen they are REALLY slow at redrawing
2)  ati$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

3)  fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Should #2 be YES for direct rendering, and should #3 be ATI FGLRX drivers with Opengl?

--Kevin

Ahh your right, I forgot one step, Dbd prolly didn't need to since he had tried installing the xorg-fglrx =)

Try running 

```

aticonfig  --initial

```

just to make sure re-do the step about xorg.conf and reboot, then check again =)

---

### Post by reiki on 2006-11-03
> **Ferrat said:**
> 
The install wine deb from this link [http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz](http://www.ubuntusociety.org/garyu_wine_0.9.24_WoW-patch_EdgyEft_deb.tar.gz)  ( all creds to reiki for figuring out how to make a working .deb for Edgy and to Garyu for making one thread: [http://ubuntuforums.org/showthread.php?t=290761](http://ubuntuforums.org/showthread.php?t=290761) )

Glad to be part of teh solution. However credits to Nick Law and AlanJ over at WinHQ as I really just put some pieces together but they did all the hard work :)

---

### Post by Ferrat on 2006-11-03
> **reiki said:**
> Glad to be part of teh solution. However credits to Nick Law and AlanJ over at WinHQ as I really just put some pieces together but they did all the hard work :)

Well putting pieces together is important as well =) 

That's how I solved this but screening thru the forums ect. and putting it all together and that's the real point with the support forum and linux in general, making ppl work together by building of others knowledge and making things work :) That's how I see it and ofc the guys at wineHQ should have big creds since without them this wouldn't be possible at all.

---

### Post by myname on 2006-11-04
> **Ferrat said:**
> Ahh your right, I forgot one step, Dbd prolly didn't need to since he had tried installing the xorg-fglrx =)

Try running 

```

aticonfig  --initial

```

just to make sure re-do the step about xorg.conf and reboot, then check again =)

I noticed that wasn't there, and when I did that, I got a message saying DRI not installed.  I uninstalled all the FGLRX drivers via Synaptic and am going to install them again to see what happens.  When all said and done, should fglrxinfo report back ATI or the DRI?

Here is the output of my FGLRXINFO:

kevinp@dugr:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)




--Kevin

---

### Post by Ferrat on 2006-11-04
Hmmm not really sure about that, know that some ppl with ATi has been having the same problem with DRI, I haven't had the problem so haven't looked in to it but try checking the video area or search, I'll try to find a fix aswell and see what we come up with, if you do find a fix please post it here so others can find it =)

---

### Post by myname on 2006-11-06
will do.  Thanx for your help.  I should have time to mess with it tonite after work.

---

### Post by myname on 2006-11-06
> **Ferrat said:**
> Hmmm not really sure about that, know that some ppl with ATi has been having the same problem with DRI, I haven't had the problem so haven't looked in to it but try checking the video area or search, I'll try to find a fix aswell and see what we come up with, if you do find a fix please post it here so others can find it =)

I installed the ATI drivers by following the directions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

They seem to work, as here is the output of fglrxinfo:

```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

Here is the output of glxinfo | grep render

```
glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1600 Series Generic
```

And glxgears -printfps is returning this:

```
 glxgears -printfps
1238 frames in 5.0 seconds = 247.404 FPS
1254 frames in 5.0 seconds = 250.791 FPS
1259 frames in 5.0 seconds = 251.791 FPS
1232 frames in 5.0 seconds = 246.389 FPS
1284 frames in 5.0 seconds = 256.792 FPS
1286 frames in 5.0 seconds = 256.909 FPS
1326 frames in 5.0 seconds = 265.143 FPS
1245 frames in 5.0 seconds = 248.991 FPS
1255 frames in 5.0 seconds = 250.991 FPS
1263 frames in 5.0 seconds = 252.591 FPS
```

By the above, I'm assuming I have successfully installed the ATI drivers?  Are these values (FPS may vary) what are you receiving?

time to go test WoW

EDIT:  No go, WoW locked up about 20 seconds after entering.  I did notice though before the hard system lock, that the fonts were all messed up.  Anyone else have this font problem?


--Kevin

---

### Post by Ferrat on 2006-11-06
> **myname said:**
> I installed the ATI drivers by following the directions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

They seem to work, as here is the output of fglrxinfo:

```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

Here is the output of glxinfo | grep render

```
glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1600 Series Generic
```

And glxgears -printfps is returning this:

```
 glxgears -printfps
1238 frames in 5.0 seconds = 247.404 FPS
1254 frames in 5.0 seconds = 250.791 FPS
1259 frames in 5.0 seconds = 251.791 FPS
1232 frames in 5.0 seconds = 246.389 FPS
1284 frames in 5.0 seconds = 256.792 FPS
1286 frames in 5.0 seconds = 256.909 FPS
1326 frames in 5.0 seconds = 265.143 FPS
1245 frames in 5.0 seconds = 248.991 FPS
1255 frames in 5.0 seconds = 250.991 FPS
1263 frames in 5.0 seconds = 252.591 FPS
```

By the above, I'm assuming I have successfully installed the ATI drivers?  Are these values (FPS may vary) what are you receiving?

time to go test WoW

EDIT:  No go, WoW locked up about 20 seconds after entering.  I did notice though before the hard system lock, that the fonts were all messed up.  Anyone else have this font problem?


--Kevin

Ahh yes font problem, that one is a know bug but easy to fix =) 

Taken from [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
> Corrupt or Missing Text - here's the fix for ATI cards

If you are suffering from corrupt or missing text you will need to add the DisabledExtensions key to the registry.

Here's how you do it ...

Open a terminal window, (konsole/terminal/x terminal etc..) and type regedit. This will start the wine server
and the wine equivalent of the windows registry editor will be displayed. If your familiar with using the registry
editor under windows then this is pretty much the same.

Find HKEY_LOCAL_MACHINE\Software\Wine\
If your doing a fresh install of 0.9.22 or 0.9.23 the Wine registery key may not exist. If it doesn't, create
it. Note, that the keys are case sensitive, so create "Wine" not "wine" ...etc.

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder

Click right on the wine folder and select [NEW] then [KEY]

Replace the text "New Key #1" with OpenGL

Click right in the right hand pane and select [NEW] then [String Value]

Replace "New Value #1" with "DisabledExtensions"
(Notice it's case sensitive)

Then double click anywhere on the line, a dialog box will open.
In the value field type "GL_ARB_vertex_buffer_object" (without the quotes).

Here's what regedit should look like once you have finished adding this new key and it's value.

appdb.winehq.org/appimage.php?iId=3746 

Try that and see what happens =)

---

### Post by myname on 2006-11-06
Ah, that's right, I remember doing that before now...  Thanx.

Now if I can only solve the problem if it locking up.  I even have the minimap turned off, which was causing problems.

Will keep testing.

--Kevin

---

### Post by Ferrat on 2006-11-06
> **myname said:**
> Ah, that's right, I remember doing that before now...  Thanx.

Now if I can only solve the problem if it locking up.  I even have the minimap turned off, which was causing problems.

Will keep testing.

--Kevin

Do you get any output, try running it in a terminal window, and tab so you have the terminal window above the wow one when it locks. 

Does everything stop responding?

Does the picture freeze? 

Does the mouse move?

---

### Post by myname on 2006-11-06
I do run WoW from a terminal:

wine WoW.exe -opengl

my system appears to lock tighter than a drum, when I press capslock, nothing happens.

EDIT:

I was able to jump in a server, then I exited real quick before the lock up.  Here is what was in the terminal window:

```

fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c3d0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c3d0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e4f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e550,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

Any ideas?  Is this something I can take care of on my system, or is this a Wine thingie?

would I have better luck with Crossover or Cedega?

--kevin

---

### Post by Ferrat on 2006-11-07
> **myname said:**
> I do run WoW from a terminal:

wine WoW.exe -opengl

my system appears to lock tighter than a drum, when I press capslock, nothing happens.

EDIT:

I was able to jump in a server, then I exited real quick before the lock up.  Here is what was in the terminal window:

```

fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c3d0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c3d0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e4f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e550,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

Any ideas?  Is this something I can take care of on my system, or is this a Wine thingie?

would I have better luck with Crossover or Cedega?

--kevin

Thats a normal output for wine, I have the same aswell 

Do you have a USB keyboard? 

I've found that sometimes wine/wow kills my USBs, the game and the comp still run but mouse, keyboard, WiFi ect. stops working, but it happens at random and not very often for me. 

could you start it again and let the terminal stay up so you see it and just let the game lock up and see if it says anything else then?

Well cedega works aswell, Crossover is just wine in a nice wrapping (not really true, but sort of) but sure it could work but both does cost money.

It might take some time but we get you up and running I think :)

---

### Post by Ferrat on 2006-11-07
BTW just remembered

you could check your Config.wtf  in the WoW folder WTF that's inside your wow dir (/World of Warcraft/WTF/Config.wtf), could you please post that and your /ect/X11/xorg.conf

and I could have a looksee =)

---

### Post by myname on 2006-11-07
Thanx, I will try to get the terminal to come up when WoW is in the background.  I will let you know what happens when I test that tonite after work.

I know it will take a while, I had it up and running on Dapper and had the same problems to start, but once I got it going, no problems at all.

Thanx again for helping, I wouldn't have thought it would have taken this long, but know I have a complete set of notes to go by if I do a complete install.  :)

--Kevin

---

### Post by Ferrat on 2006-11-07
> **myname said:**
> Thanx, I will try to get the terminal to come up when WoW is in the background.  I will let you know what happens when I test that tonite after work.

I know it will take a while, I had it up and running on Dapper and had the same problems to start, but once I got it going, no problems at all.

Thanx again for helping, I wouldn't have thought it would have taken this long, but know I have a complete set of notes to go by if I do a complete install.  :)

--Kevin

Hehe yeah, just make sure this is in your config.wtf 

```

SET gxWindow "1"
SET gxMaximize "1"

```

Then just ALT+TAB till you get the Terminal window and then just wait until it crashes =)

---

### Post by myname on 2006-11-07
really odd...  I know have the fonts in WoW, and the game is running just like it was in Dapper, no problems...so far.  Is Ubuntu a self aware system?  does it "test us" to see if we are going to keep it installed?  Why do I ask, let me tell you.

Install #1
Install Ubuntu Edgy Eft 
Sound works
Install ATI Drivers
Install Wine
copy WoW off windows drive
No sound
WoW have graphical glitches and freezes

Install #2 (follow same exact pages that I used in #1)
Install Ubuntu Edgy Eft 
Sound works 
Install ATI Drivers
No sound
Install Wine
No sound

Install #3 (follow same exact pages that I used in #1 and 2)
Install Ubuntu Edgy Eft
Sound works
Reboot
No sound

Install #4 (follow same exact pages that I used in previous installs)
Install Ubuntu Edgy Eft 
Sound works 
Install ATI Drivers
Sound works 
Install Wine
Sound works
copy WoW from windows drive
WoW crashes to desktop, buncho Wine errors

Install #5 (follow same exact pages that I used in previous installs)
Install Ubuntu Edgy Eft 
Sound works 
Install ATI Drivers with different steps
Sound works 
Install Wine
ATI drivers are not enabled

Install #6 (follow same exact pages that I used in #1 - #4)
Install Ubuntu Edgy Eft 
Sound works 
Install ATI Drivers
Sound works 
Install Wine
WoW runs but font is whack, and game is staggery
Install regedit hack
WoW runs font is better, game is smoother

After 6 installs WoW runs fine under Ubuntu

---

### Post by Ferrat on 2006-11-08
Some mysteries will never be solved and some solve themselfs, I usally blame love and care or bruteforce and tortyre ;D

I'm doing a clean system wipe, had problems with Edgy using my old dapper /home so =)

---

