---
title: "Graphics card problem"
date: 2005-04-06
forum: Desktop Environments
---

### Post by wxm505 on 2005-04-06
It seems strange. I updraded the box from Warty to Hoary several days ago.
The graphics card (intel 82852/855 )does not seem work well.
I run tuxracer to test the 3D capability. It was running extremly slowly.
But it ran very well under Warty.The other problem about running tuxrace
is the processor in use rised to 100% in a second.
Then I found the font and window of skype is much bigger than the skype
I used under Warty.
I thought it might be some configure about graphics card or display of 
Gnome.
any help??? Thank u very much.
This updrade brought some trouble to me.Does anyone suffer the same 
thing?

---

### Post by alastair on 2005-04-06
For any X/graphics issues, it might be worth to check the X logs :

/var/log/Xorg.0.log

and see if any errors or warning messages appear.

Also check that DRI is enabled :

glxinfo

As for fonts etc. - is it the same version of the application? I think Gnome lets you change desktop/app fonts? Might be worth a look.

---

### Post by StacyWebb on 2005-04-06
I have the same cpu issues, running an ATI M10, I have full 3d accel but the cpu pegs, If anyone does come up with an answer I would love to know it. One note this happens with the 2.6.10-5 kernel and not the 2.6.8 for me.

---

### Post by wxm505 on 2005-04-06
[QUOTE=alastair]For any X/graphics issues, it might be worth to check the X logs :

/var/log/Xorg.0.log

and see if any errors or warning messages appear.

Also check that DRI is enabled :

glxinfo

As for fonts etc. - is it the same version of the application? I think Gnome lets you change desktop/app fonts? Might be worth a look.[/QUOTE]
This is maybe the problem:  I checked out that direcory /var/log
There was not Xorg.log in it instead a Xfree86.log in it. It seems not right.
I updraded the box by Synaptic.Was it supposed to convert to Xorg???
Any help??

---

### Post by wxm505 on 2005-04-07
Does anyone have any idea about this ??

---

### Post by wxm505 on 2005-04-07
What did it really change from Warty to hoary??

---

### Post by LongTooth on 2005-04-07
Was it supposed to convert to Xorg? Yes most definitely. When you upgraded, did you do a dist-upgrade, via apt-get, or 'Smart Upgrade', via Synaptic? If not, you did not upgrade to Hoary. I know because I did - or not do- the same thing. With Warty as well as other distros, dist-upgrade really messed up my system. As a result I did not do it. Well, to my astonishment I found that to upgrade, this was a necessary step. Of course with the neccessary changes to your repository list before you do so. 

To find out if you have indeed done a full upgrade click on the top panel System > About Gnome and do the same with About Ubuntu. Gnome should show 2.10 and of course Ubuntu should show Hoary.

---

### Post by feloc on 2005-04-07
I had the same problem with games (very slow) when I upgraded to Hoary, and now I finally managed to get them to work again.

Make sure you don't have multiple video drivers installed on your system.
I looked for any gl drivers I had installed using Synaptic, and found some ati-drivers I don't need, uninstalled them and everything works very well now.

---

### Post by wxm505 on 2005-04-07
[QUOTE=LongTooth]Was it supposed to convert to Xorg? Yes most definitely. When you upgraded, did you do a dist-upgrade, via apt-get, or 'Smart Upgrade', via Synaptic? If not, you did not upgrade to Hoary. I know because I did - or not do- the same thing. With Warty as well as other distros, dist-upgrade really messed up my system. As a result I did not do it. Well, to my astonishment I found that to upgrade, this was a necessary step. Of course with the neccessary changes to your repository list before you do so. 

To find out if you have indeed done a full upgrade click on the top panel System > About Gnome and do the same with About Ubuntu. Gnome should show 2.10 and of course Ubuntu should show Hoary.[/QUOTE]
I checked it out.It is Gnome 2.10. But there is not a option in the list of system about Ubuntu. I typed in 
 uname -a . System said:
Linux ubuntu 2.6.10-5-686 #1 Fri Apr 1 16:48:32 UTC 2005 i686 GNU/Linux
Do u think it is all right or not?

---

### Post by wxm505 on 2005-04-07
[QUOTE=feloc]I had the same problem with games (very slow) when I upgraded to Hoary, and now I finally managed to get them to work again.

Make sure you don't have multiple video drivers installed on your system.
I looked for any gl drivers I had installed using Synaptic, and found some ati-drivers I don't need, uninstalled them and everything works very well now.[/QUOTE]
Would u like to tell me how to do it in details? I am so sorry I am quite new to Ubuntu
and Debian based linux.
I am really appreciate it:)

---

### Post by LongTooth on 2005-04-08
One of the most obvious thing about Hoary is at the top panel. It will have three settings: Applications, Places, and System unlike Warty which had only two. System>Administration>Ubuntu Update Manager is a sure shot you've upgrade to Hoary. Warty doesn't have a Ubuntu Update Manager. So you've got Gnome 2.10. It doesn't sound like you have Hoary. Did you do a dist-upgrade after you changed your 'Warty' to 'Hoary' in the repository list? 

I use the command line quite often but find, at least for adding and deleteing packages, Synaptic is so much easier. You can do all this with Synaptic. Don't forget to do a 'Smart Upgrade'. That translates into dist-upgrade in Synaptic speak:) Don't forget to comment out (#) any repositories you might have added to Warty. Better yet, delete them.

---

### Post by wxm505 on 2005-04-08
[QUOTE=LongTooth]One of the most obvious thing about Hoary is at the top panel. It will have three settings: Applications, Places, and System unlike Warty which had only two. System>Administration>Ubuntu Update Manager is a sure shot you've upgrade to Hoary. Warty doesn't have a Ubuntu Update Manager. So you've got Gnome 2.10. It doesn't sound like you have Hoary. Did you do a dist-upgrade after you changed your 'Warty' to 'Hoary' in the repository list? 

I use the command line quite often but find, at least for adding and deleteing packages, Synaptic is so much easier. You can do all this with Synaptic. Don't forget to do a 'Smart Upgrade'. That translates into dist-upgrade in Synaptic speak:) Don't forget to comment out (#) any repositories you might have added to Warty. Better yet, delete them.[/QUOTE]
I am afride something messed up in my box. I do have three settings in my top panel.
But there is not a Ubuntu Update Manager in the System>Administration.
I used "smart-upgrade" when I upgraded from Warty to hoary. But Synaptic said he can not download all the packages from server.Actrually it downloaded all the packages from HTTP servers but FTP. I use proxy to connect internet.It seems
work fine with HTTP but FTP. I do not know why. Everything seemed work well under
warty.
This is my /etc/apt/source.list file. can u seen what the wrong is

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/ 
deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/ 

thanks a lot mate

---

### Post by wxm505 on 2005-04-08
I checked out Synaptic. I found all the Xfree86 packages are there.
But For Xorg packages only Xorg-common was installed.
It seems not good.
What should I do?

---

### Post by wxm505 on 2005-04-08
any idea friends??
I had converted xfree86 to xorg. Now xorg is running.
But the graphics card problem is still there.
:(   :(

---

### Post by alastair on 2005-04-08
See my second comment - post 

 - the log file /var/log/Xorg.0.log
 - glxinfo output
 - /etc/X11/xorg.conf file
 - output of : lspci -v

---

### Post by wxm505 on 2005-04-08
This is what showed up after I typed in glxinfo

[COLOR=Blue]satan@ubuntu:/var/log $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  1 0 Slow
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
[/COLOR]

This is what showed up after I typed in lspci -v
[COLOR=Navy]
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 17
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at e0200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 3400 [size=128]
        Capabilities: <available only to root>

0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 3000 [size=256]
        Memory at e0200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 30001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30400000-307ff000 (prefetchable)
        Memory window 1: 30800000-30bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

[/COLOR]

Do u think there is any wrong setting???
thanks for help :)

---

### Post by Jezze on 2005-04-08
Be sure you have the xorg-driver-fglrx package. You can install it with synaptic. Try to reboot. If it still doesnt work check to see if the /etc/X11/xorg.conf file has the line: Driver "fglrx" and not something else... if it does, change it.

---

### Post by feloc on 2005-04-09
Funny...

I got it to work like this (I'm using an Intel i830 video chip on my laptop)

Started Synaptic.

Searched for gl (found a lot of stuff).

Uninstalled xorg-driver-fglrx and  xorg-driver-fglrx-dev.

Rebooted.

---

### Post by wxm505 on 2005-04-09
[QUOTE=Jezze]Be sure you have the xorg-driver-fglrx package. You can install it with synaptic. Try to reboot. If it still doesnt work check to see if the /etc/X11/xorg.conf file has the line: Driver "fglrx" and not something else... if it does, change it.[/QUOTE]
I did what u recommanded. The driver was i810 , I changed it to fglrx then reboot
the box. The error message said I can not enter X server because something wrong 
with my graphics card setting.
So I had to change it back.
any idea??

---

### Post by wxm505 on 2005-04-09
[QUOTE=feloc]Funny...

I got it to work like this (I'm using an Intel i830 video chip on my laptop)

Started Synaptic.

Searched for gl (found a lot of stuff).

Uninstalled xorg-driver-fglrx and  xorg-driver-fglrx-dev.

Rebooted.[/QUOTE]
I did what u recommanded and run tuxracer for test. I typed tuxracer in command line.It halted the game interface had never showed up. any idea??

---

### Post by feloc on 2005-04-09
Maybe this webpage would help:

[http://wiki.linuxquestions.org/wiki/OpenGL#OpenGL_on_Linux](http://wiki.linuxquestions.org/wiki/OpenGL#OpenGL_on_Linux)

---

### Post by wxm505 on 2005-04-09
I read it. It may not help. But thank u all the same mate.

---

### Post by wxm505 on 2005-04-10
any idea?

---

### Post by wxm505 on 2005-04-11
It did upgraded from the install disk again. The problem is still there.
any help?

---

### Post by wxm505 on 2005-04-13
any ideas??? cheers

---

### Post by wxm505 on 2005-04-20
any help??thanks a lot

---

### Post by LongTooth on 2005-04-21
wxm505, God know I don't want to dissuade you from using Ubuntu or Linux in general, but you might think about wiping out you HD and starting from scratch. Don't think of it as a failure but rather as part of the learning experience that comes with somethng new like Linux. I can't tell you how many times I've installed Ubuntu. At least 4 times with Warty and twice with Hoary. Make that three times; this last time I've got everything working like a fine Swiss watch. Do the Swiss still make watches? 

Why did I install so many times? Mostly because I jumped the gun and screwed up my system and it was easier to reinstall. And each time it was easier and faster to do. I've done the same thing with several other distros. The first was Mandrake and it continued with SuSE and Fedora Core and quite a few other in between. And everytime I picked up some tidbit that made my understanding of that distro and Linux better. 

At some other forum, one of the posters described himself as a permanent intermediate user. I'm a far cry from being a Guru like others here.  I guess that's me in a nut shell - a permanent intermediate user. And I wouldn't be where I am, (knowledge wise) if I hadn't hit all those snags along the way. 

You've gotten some good advice from this forum and still you have the problem. Maybe you haven't told us something important and that is why you still have it. But that is not important. What is, is that at sometime one has to cut their losses and start from the begining. Or else one ends up spending more effort then it's worth. A fresh install would be cheaper in time and effort and a whole lot easier. 

I installed Hoary via the Wary upgrade. I've also order the pressed Hoary CD and am waiting for them with bated breath. Guess what I'm going to do when they come in? Yep, I'm going to reinstall! Why? Because I'm an idot and I can't help myself! This is what I live for. God, I've got to get a life.

Keep the faith and keep on plugging away.

---

### Post by gil-galad on 2005-04-21
Make sure you install ubuntu-desktop so that you have all the hoary packages.

---

### Post by awaldram on 2005-04-27
ensure you have in your xorg.conf
under 

Section "Module"
Load  "dri"

and at the bottom

Section "DRI"
 Mode 0666
EndSection

*Originally Posted by Jezze* 
*Be sure you have the xorg-driver-fglrx package. You can install it with synaptic. Try to reboot. If it still doesnt work check to see if the /etc/X11/xorg.conf file has the line: Driver "fglrx" and not something else... if it does, change it.*   :---)  [-X 

**DONT THINK SO!!!!!!!!!!!!!!!!!!!!!!!!!!**
Your driver should be the intel 810 not an ATI driver cause you dont have an ATI card !!!!!!

ensure you remove all ati  gobledy cook you have been pursuaded to install (fglxr)

When you run glxinfo your should get
Output of glxinfo:
-----------------

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

then glxgears should show a massive frame rate hike..

---

