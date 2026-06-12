---
title: "compiz causing white screen O.o"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by kamasabi on 2007-11-06
well after much irritation and searching, I must ask due to this rather annoying issue.  

I installed fiesty on my laptop and so far it has been good.  my laptop is an hp zv6130us, aka sys specs:

AMD 3200+ (swapped with 3500 newcastle)
512MB memory (1.25gb now)
80GB HDD  (2 partitions, 60gb winxp, 15gb ubuntu)
**ATI Mobility Radeon 200m**  (a flaming pile)

I used the following guide to install my video drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)   
(section 3.1 to be exact)

I tried to enable my desktop effects, but I got this annoying little message:
"the composite extension is not available"

now following this, I would hoping everything would be fine and dandy and I could enable my desktop effects after a restart.  

tried to enable them, same error.  -_-.    Fine.

So after searching I looked into changing the option in the extension part of my xorg.conf from disable to enable.  ***PROGRESS!!!!*** 

Section "Extensions"
        Option  "Composite" "Disable ** (changed this to enable)**"
EndSection

Now it will actually give me the option to enable desktop effects.  When I click enable, however, my entire screen turns white, and all I can see is my cursor.  If i hit escape, it puts me back to where I was and it disables the change.  

It is 2:30am here, and after a couple hours of screwing with it, I am going to get some sleep, maybe tomorrow will bring better results.  If you have any suggestions, please give me a shout, either about compiz or a different way of installing the ATI drivers that may bring better results.

Thanks!!!!

Kama

---

### Post by TheKode on 2007-11-10
if you do fglrxinfo do you get openmesa or ati openGL? 

I also got a whitescreen when enabling compiz, and noticed I had the openmesa openGL. Reinstalled the ATI driver and it then used the ati openGL, and it worked.

---

### Post by Kymus on 2007-11-13
*fglrxinfo* makes my system crash :eek:

---

### Post by xeth_delta on 2007-12-10
Can you please post the output of glxinfo?

---

### Post by Kymus on 2007-12-10
> **xeth_delta said:**
> Can you please post the output of glxinfo?

I am not quite sure how to do that

---

### Post by xeth_delta on 2007-12-11
> **Kymus said:**
> I am not quite sure how to do that

Open a terminal / console and type
```
glxinfo
```

Copy the contents and paste it in your post, between code tags (when you write you'll see a button with the # symbol in the posting window).

This will help us see if your computer actually has hardware acceleration enabled.

Xeth

---

### Post by duskle on 2007-12-12
I am having a similar problem, let me give a full description:

I'm trying to get compiz/AIGLX working on an ATI x300 (in a Dell Optiplex GX280) with the new Catalyst drivers (7.11) in Ubunutu 7.10.  The result is that I get a white screen when I start compiz.  I have XGL *uninstalled*, and I have installed the new drivers in the following ways:

1. The simple way: [http://ubuntuforums.org/showthread.php?t=634104](http://ubuntuforums.org/showthread.php?t=634104)
Result: compiz wouldn't start, and would fall back to metacity.

2. The more complicated way: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Result: white screen, with functioning cursor.  I can recover by Alt-F2 and then "metacity --replace", but I have to do it blind.
If I run compiz --replace in a terminal, I get the following output (after I recover from the white screen, of course):
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b60 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048 ): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

3. Envy, manual install of ATI drivers.
Result: same as above.

I had previously tried the last version of the ATI drivers, but it made my system so unstable I didn't even really get a chance to try Compiz.
Any ideas?

Here is some more info that may be relevant:

fglrxinfo gives:
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.1.7059 Release

glxinfo gives:
> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.1.7059 Release
OpenGL extensions:
... and so on ...

glxgears ang fgl_glxgears both work, and seem reasonably fast.

---

### Post by xeth_delta on 2007-12-12
What happens when using the opn source drivers, radeon or ati?

---

### Post by duskle on 2007-12-13
If I use ati or radeon drivers, I don't get 3D acceleration; glxgears runs really slow and compiz won't start.

---

### Post by Necreia on 2007-12-25
Using an x300 (mobility), I have this exact same issue.

I have gone though everything in this thread with no luck.  I'm throwing in my lot here to help rule out hardware failure as the cause...

I'll poke around a bit and see if I can't figure it out as well.

---

### Post by terminal on 2007-12-25
I had this problem when i had fglrx in xorg.conf and there was a problem with fglrx module for kernel . Are you running RT kernel ? In shell type "sudo modprobe fglrx" and see if it gives any errors . Also post output of "tail /var/log/Xorg.0.log -n 300|grep fglrx" this will show you most important info . Do this when u have fglrx configured in xorg.conf .

when white screen comes just blindly press Alt+F2 and type "pkill compiz" u will be able to get to desktop :D then open cmd prompt and type metacity to have a basic window manager .

---

### Post by terminal on 2007-12-25
To ensure that u can run desktop fine with Ati radeon  i learned many things in last few days ( had a real hard time )

1) You should not be running rt kernel ( if you are then look for instructions here [http://ubuntuforums.org/showthread.php?t=591445&page=6](http://ubuntuforums.org/showthread.php?t=591445&page=6) and recompile kernel ) .

2) Aiglx should be on in xorg.conf

3) Composite should be off or disabled in xorg.conf 

4) "sudo modprobe fglrx" should not give any errors . 

5 ) ```
sudo gedit /usr/bin/compiz

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""

```


Follow this guide for installation of latest Ati radeon drivers

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

