---
title: "Nintendo 64 emulator?"
date: 2008-02-05
forum: Gaming &amp; Leisure
---

### Post by _Phineas_ on 2008-02-05
On windows I used to use Project 64 emulator, it doesnt work on Ubuntu. any suggestions? :popcorn:

---

### Post by GiantRobot on 2008-02-05
My favorite N64 emulator is Mupen64.

It doesn't have as many options as Project 64 and (to my knowledge) doesn't support cheats and that sort of thing.  Most games play near perfect so it's fine with me.  The only trouble I have is with Ocarina of Time.

Definitely give Mupen64 a try though.  It should be in the repositories.

---

### Post by frenchn00b on 2008-02-05
you dont have much choices: mupen64
it is not that bad, but could be better. 

Good luck with it, it is still not perfect. Let us know what u think about this mupen64 [http://mupen64.emulation64.com/](http://mupen64.emulation64.com/)

look zophar website.

---

### Post by acoustibop on 2008-02-05
> **GiantRobot said:**
> ... Definitely give Mupen64 a try though.  It should be in the repositories.

Afraid it isn't in the repositories, GiantRobot. :(

---

### Post by frenchn00b on 2008-02-05
> **acoustibop said:**
> Afraid it isn't in the repositories, GiantRobot. :(

It is too crashy/buggy for Debian repos. for the moment. It takes some time before it is stable.

---

### Post by FrozenFox on 2008-02-07
Attached to my post is a script that I found that will install mupen64 & plugins for it. it's been stable enough for me. Use it at your own risk though, blah blah, as usual.

For those who don't know how to use a script that may also be reading this, download the file to the desktop, open the terminal/console/konsole, cd to the directory (ie cd ~/Desktop if its on the desktop), make it executable (chmod a+x ./emulation_mupen64install.sh), and run it via ./emulation_mupen64install.sh. I think the only thing it asks for is your sudo password to install into the system.

If you don't have a start menu link, the emulator will be located at 
/usr/local/games/mupen64-0.5/mupen64

P.S.: Great alias :)

---

### Post by frenchn00b on 2008-02-16
Is there any alternative to MUPEN64 ? thanks

---

### Post by Sockerdrickan on 2008-02-16
The new version

32bit: [http://www.fascinationsoftware.com/repo/Mupen64amd64-RiceVideoLinux-1-2-bin-32.zip](http://www.fascinationsoftware.com/repo/Mupen64amd64-RiceVideoLinux-1-2-bin-32.zip)
64bit: [http://www.fascinationsoftware.com/repo/Mupen64amd64-RiceVideoLinux-1-2-bin-64.zip](http://www.fascinationsoftware.com/repo/Mupen64amd64-RiceVideoLinux-1-2-bin-64.zip)

---

### Post by Zzzach on 2008-02-16
Do you just have to unzip it and copy it to the games directory?

---

### Post by Sockerdrickan on 2008-02-16
Yes, start the gui and play the roms!

---

### Post by frenchn00b on 2008-02-16
> **Tux0r said:**
> Yes, start the gui and play the roms!

I get this error message: 

```
gui and play t  5 code:20B854B239203BAF6C961B850A4A51A2
eeprom type:0
init timer!
memory initialized
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: version 0.0.10 initialized.
[RiceVideo] SSE processing enabled.
[RiceVideo] Found ROM 'SUPER MARIO 64', CRC ff2b5a632623028b-45
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
libGL warning: 3D driver claims to not support visual 0x4b
(EE) Error setting video mode 640x480: Couldn't find matching GLX visual
Signal number 11 caught:
        errno = 0 (Success)

```

---

### Post by Zzzach on 2008-02-16
hmmm it starts to load the rom then the window just closes :confused:

---

### Post by Zzzach on 2008-02-16
ok it's working now, I just messed around with the plugins

---

### Post by frenchn00b on 2008-02-16
can I get rice and glx with my video card ?

I get glxinfo yes but this error messga :
> 
libGL warning: 3D driver claims to not support visual 0x4b ...



```
 clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:44000000-47ffffff iomemory:40300000-4037ffff irq:193
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info
```

> 
screen: 0
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
OpenGL vendor string: Keith Whitwell
OpenGL renderer string: Mesa DRI i815 20050821
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_co

---

### Post by Zzzach on 2008-02-16
nothing happens when I click configure input though so I can't use my gamepad

---

### Post by frenchn00b on 2008-02-16
> **Zzzach said:**
> nothing happens when I click configure input though so I can't use my gamepad

type $glxinfo
do you get yes or no .?

---

### Post by Sockerdrickan on 2008-02-16
He is using another graphics plugin than you are

---

### Post by Zzzach on 2008-02-16
type it where, in terminal? Blight input plugin doesn't show up on the list, only mupen's input plugin, but that is doing nothing when I click config or test.

---

### Post by frenchn00b on 2008-02-16
I am lost, I dont understand anything wiht those glx, dri, ... bla bla
I guess I'll never make it to understand linux. It is soo complicated.

So it looks that It will be a no N64 on a 1000Mhz machien, that's sad. I go to bed 
thanks & Cheers !

---

### Post by Zzzach on 2008-02-16
Blight input is not showing up on the list of plugins. Any ideas?? The mupen input plugin is doing nothing.

---

### Post by frenchn00b on 2008-02-16
> **Zzzach said:**
> Blight input is not showing up on the list of plugins. Any ideas?? The mupen input plugin is doing nothing.

In general , you like that mupen64 program ?

I am thinking to go back to windows, with linux, nothing never works

---

### Post by RemmyLee on 2008-02-16
@frenchn00b:
 You need to understand that Linux is NOT Windows. Linux is far more robust, dynamic and customizable. Instead of worrying so much about playing games, go read up on how things are done in Linux and you'll be able to solve most of your problems. This community loves to help people, but you have to be willing to take some initiative and experiment or you'll never "get" Linux. Remember that Mupen64 was stagnant for nearly 2 years and Richard was kind enough to continue its work. Bugs are a fact of life and instead of complaining about it, learn to do traces and let Richard know so he can improve it. Nothing is perfect.

@Zzzach:
Are you running the 32 or 64 bot version? Try deleting everything and extracting it again. Instead of moving it to your ROM directory, simply open it up and choose a ROM directory in the configuration menu.

---

### Post by Zzzach on 2008-02-16
I'm using the 64-bit version. I will try deleting it and starting from scratch. I personally like linux even with all its hassles. I find it fun figuring things out, even though things at times can be frustrating or your options are more limited. Part of the fun of linux is working out the rough spots I think.

---

### Post by RemmyLee on 2008-02-16
I'm in total agreement there and that was in no way focused towards you.

I've been using Unix based systems since 1996, so I tend to make assumptions about the ease of use Linux offers as well.

Using Linux teaches you problem solving frenchn00b and believe me, it pays off. Eventually, you get to the point to where you see your desktop less as a tool and more as cluttered mess bordering your terminal window. lol

---

### Post by V0X on 2008-02-22
> **RemmyLee said:**
> I'm in total agreement there and that was in no way focused towards you.

I've been using Unix based systems since 1996, so I tend to make assumptions about the ease of use Linux offers as well.

Using Linux teaches you problem solving frenchn00b and believe me, it pays off. Eventually, you get to the point to where you see your desktop less as a tool and more as cluttered mess bordering your terminal window. lol

That's completely true. I used to be a die hard-windows guy, but I got tired of the heavy RAM usage, the viruses, and the hated BSOD. So three weeks ago I decided to migrate to linux. I tried like seven versions, among them some of the most popular: Gentoo, Sabayon, Mandriva, Slackware, Redhat. I finally settled on Ubuntu.

Ubuntu is definitely one of the more Windows-like versions of Linux out there. I suggest you just do some surfing and read up on Linux commands or whatever.

If you're considering going "back to windows", I suggest you try WINE first. Wine is a program that allows you to run windows applications on your Linux machine. True, it's not perfect, and it, like everything else in Linux, has bugs and problems that need to be worked out. But if you're looking to play games, maybe do a bit of Photoshop work, get WINE at [http://www.winehq.org/]("http://www.winehq.org/").

Hope it helps.

-V0X

---

### Post by acoustibop on 2008-02-22
Me, too, I only made the final switch to Linux about a year ago; there's no way I'd want to go back now.  I still keep a Windows installation going, but the only thing I use it for is running ripping applications: there there are formats needed for some games that there is no Linux application for - neither will they run in Wine.

But I think that frenchn00b's basic problem is that he's trying to run this stuff on a very low spec machine and expects perfect results.  I've asked him several times in several threads to describe his system, but he won't.  I've managed to find out that it may be a Compaq Evo, that it has a Pentium III and a rubbish (and possibly problematic) soundcard - that's it.

---

### Post by Megatog615 on 2008-03-07
```
(EE) Error setting video mode 1280x1024: Couldn't find matching GLX visual
```
Mupen64 dies with signal 11. Other games can find a GLX visual without problems.

---

### Post by forrestcupp on 2008-03-08
> **GiantRobot said:**
>  Most games play near perfect so it's fine with me.  The only trouble I have is with Ocarina of Time.

I'm playing Ocarina of Time right now without any trouble, other than the occasional polygon glitch.  I ended up having to switch to the glN64 glx plugin, though.  But I set it to 1024x768 and enabled fog, 2xSAI texture scaling, and anisotropic filtering.  It looks better than the original.

> **Megatog615 said:**
> ```
(EE) Error setting video mode 1280x1024: Couldn't find matching GLX visual
```
Mupen64 dies with signal 11. Other games can find a GLX visual without problems.
Does it crash when you start a game, or can you not even get to the menu window?  If it crashes when you start a game, you need to configure the settings.  For some reason, it doesn't come with plugins configured.  Go to Options->Configure and click the Plugins tab.  For the GLX plugin, I am using the glN64 plugin and it's working great.  See above for my settings.

---

