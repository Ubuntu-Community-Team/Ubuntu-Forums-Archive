---
title: "Visual Effects settings resets at computer restart."
date: 2008-12-03
forum: Desktop Environments
---

### Post by rosj04 on 2008-12-03
Hi, 

I'm having some problems with visual effects in ubuntu. Everytime I start the computer the visual effects under Preferences > appearance have changed back to "none". This leaves me without a window decorator, and having to manually put it on at every boot. Quite annoying. 

Tried searching this forum for a solution but couldn't find anything. Found this however: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/269292]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/269292")

So I know I'm not alone with this problem.

Using Intrepid release. Any input would be highly appreciated.

---

### Post by rosj04 on 2008-12-03
also noticed that for example all my network settings get resetted at each reboot as well.. might that be part of the same problem? *shrug*

---

### Post by splatterhorn on 2008-12-04
Not sure about my network settings, but I am having the exact same problem with compiz not starting on login (that is, the 'custom' selection in the GNOME *preferences/appearance/visual effects* tab keeps resetting to the 'none' selection at each login).

---

### Post by Vantrax on 2008-12-04
Try running compiz from a terminal and give the output of the error

ie compiz --replace

---

### Post by rosj04 on 2008-12-04
This is the output I get when running that command: 

[I]Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[/I]

---

### Post by rosj04 on 2008-12-04
splatterhorn, I came up with a simple  workaround. Install Compiz Fusion-Icon and put it into sessions so it starts at login. That did the trick for me. 

The command to run it is simply fusion-icon.

Still curious what the original problem is though :-/

---

### Post by ab636 on 2009-04-07
the same problem here in ubuntu 8.04. Used it since July 2008. the problem appeared only these days.

tried "Fusion-Icon" but the problem is still there.

---

### Post by Ratscallion on 2009-04-07
With your fusion-icon, add it to system->Preferences->Sessions, then compiz should start. However, you may need to add compiz& or compiz --replace to your sessions startup also. Just add either of those into the program thing where you browse, just type.

---

### Post by johnathanamber on 2009-10-25
Wow, I am also having this issue...

I get this when I do the:
$ compiz --replace
> $ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x00000000014c2380 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f368640ecb8]
/lib/libc.so.6(cfree+0x76)[0x7f3686411276]
/usr/lib/libGL.so.1[0x7f3688215038]
======= Memory map: ========
00400000-0043c000 r-xp 00000000 08:06 431357                             /usr/bin/compiz.real
0063b000-0063c000 r--p 0003b000 08:06 431357                             /usr/bin/compiz.real
0063c000-0063d000 rw-p 0003c000 08:06 431357                             /usr/bin/compiz.real
010ea000-0265a000 rw-p 010ea000 00:00 0                                  [heap]
7f368082a000-7f3680836000 r-xp 00000000 08:06 351233                     /lib/libnss_files-2.9.so
7f3680836000-7f3680a35000 ---p 0000c000 08:06 351233                     /lib/libnss_files-2.9.so
7f3680a35000-7f3680a36000 r--p 0000b000 08:06 351233                     /lib/libnss_files-2.9.so
7f3680a36000-7f3680a37000 rw-p 0000c000 08:06 351233                     /lib/libnss_files-2.9.so
7f3680a37000-7f3680a41000 r-xp 00000000 08:06 351236                     /lib/libnss_nis-2.9.so
7f3680a41000-7f3680c40000 ---p 0000a000 08:06 351236                     /lib/libnss_nis-2.9.so
7f3680c40000-7f3680c41000 r--p 00009000 08:06 351236                     /lib/libnss_nis-2.9.so
7f3680c41000-7f3680c42000 rw-p 0000a000 08:06 351236                     /lib/libnss_nis-2.9.so
7f3680c42000-7f3680c58000 r-xp 00000000 08:06 350700                     /lib/libnsl-2.9.so
7f3680c58000-7f3680e58000 ---p 00016000 08:06 350700                     /lib/libnsl-2.9.so
7f3680e58000-7f3680e59000 r--p 00016000 08:06 350700                     /lib/libnsl-2.9.so
7f3680e59000-7f3680e5a000 rw-p 00017000 08:06 350700                     /lib/libnsl-2.9.so
7f3680e5a000-7f3680e5c000 rw-p 7f3680e5a000 00:00 0 
7f3680e5c000-7f3680e64000 r-xp 00000000 08:06 350701                     /lib/libnss_compat-2.9.so
7f3680e64000-7f3681063000 ---p 00008000 08:06 350701                     /lib/libnss_compat-2.9.so
7f3681063000-7f3681064000 r--p 00007000 08:06 350701                     /lib/libnss_compat-2.9.so
7f3681064000-7f3681065000 rw-p 00008000 08:06 350701                     /lib/libnss_compat-2.9.so
7f3681065000-7f3681094000 r-xp 00000000 08:06 349619                     /lib/libpcre.so.3.12.1
7f3681094000-7f3681293000 ---p 0002f000 08:06 349619                     /lib/libpcre.so.3.12.1
7f3681293000-7f3681294000 r--p 0002e000 08:06 349619                     /lib/libpcre.so.3.12.1
7f3681294000-7f3681295000 rw-p 0002f000 08:06 349619                     /lib/libpcre.so.3.12.1
7f3681295000-7f36812d9000 r-xp 00000000 08:06 431137                     /usr/lib/libgobject-2.0.so.0.2000.1
7f36812d9000-7f36814d8000 ---p 00044000 08:06 431137                     /usr/lib/libgobject-2.0.so.0.2000.1
7f36814d8000-7f36814d9000 r--p 00043000 08:06 431137                     /usr/lib/libgobject-2.0.so.0.2000.1
7f36814d9000-7f36814da000 rw-p 00044000 08:06 431137                     /usr/lib/libgobject-2.0.so.0.2000.1
7f36814da000-7f36814db000 rw-p 7f36814da000 00:00 0 
7f36814db000-7f3681517000 r-xp 00000000 08:06 350834                     /lib/libdbus-1.so.3.4.0
7f3681517000-7f3681716000 ---p 0003c000 08:06 350834                     /lib/libdbus-1.so.3.4.0
7f3681716000-7f3681717000 r--p 0003b000 08:06 350834                     /lib/libdbus-1.so.3.4.0
7f3681717000-7f3681718000 rw-p 0003c000 08:06 350834                     /lib/libdbus-1.so.3.4.0
7f3681718000-7f3681738000 r-xp 00000000 08:06 432631                     /usr/lib/libdbus-glib-1.so.2.1.0
7f3681738000-7f3681938000 ---p 00020000 08:06 432631                     /usr/lib/libdbus-glib-1.so.2.1.0
7f3681938000-7f3681939000 r--p 00020000 08:06 432631                     /usr/lib/libdbus-glib-1.so.2.1.0
7f3681939000-7f368193a000 rw-p 00021000 08:06 432631                     /usr/lib/libdbus-glib-1.so.2.1.0
7f368193a000-7f3681941000 r-xp 00000000 08:06 351241                     /lib/librt-2.9.so
7f3681941000-7f3681b40000 ---p 00007000 08:06 35Aborted


God bless,
Johnathan

---

### Post by johnathanamber on 2009-10-25
Oh, and I get this after running:
fuse-icon:
> $ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Decorator "/usr/bin/compiz-decorator" is invalid.
 * Setting decorator to KDE4 Window Decorator ("kde4-window-decorator --replace")
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
trying to create local folder /home/johnathan/.kde/share/apps: File exists
Bus error
kde-window-decorator(689) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"

God bless,
Johnathan

---

### Post by stinkeye on 2009-10-25
This solution may be helpful to some peoples problems.
I'm using compiz 0.8.2 and fusion-icon in startup applications.
nVidia driver 185.18


My problem:
Every time I restarted my computer it would revert to metacity even though compiz was still ticked in the fusion-icon.
If I did compiz --replace 
in the terminal it would fail and I would still be running metacity.

My solution:
_[COLOR="DarkRed"]Edit:[/COLOR]_Try the solution in the next post first.
In startup applications I changed the command to start fusion-icon to
```
fusion-icon -n
```
which will run fusion-icon but not start a window manager.

Also check that you don't have the command "compiz --replace" anywhere in your startup applications
because it appears to me that the compiz --replace command is stuffed up in some way. 
I used this page to set compiz as the default window manager.
[_[COLOR="DarkRed"]http://www.jejik.com/articles/2008/10/how_to_properly_start_compiz_in_gnome/[/COLOR]_]("http://www.jejik.com/articles/2008/10/how_to_properly_start_compiz_in_gnome/")
It says to create a ~/.gnomerc  file but a later poster said to now use ~/.xprofile
I created both files so I don't know which one works.
In Gconf-editor under /desktop/gnome/applications/window_manager/ it now looks like this:
[ATTACH]133043[/ATTACH]
There must be some reason why they don't say to just paste "/usr/bin/compiz"
into the default value so I probably wouldn't do that.



Before I changed the fusion-icon command to use the -n option everything would
be loading fine until fusion tried to load compiz.
There would be a flicker of the panel and I would be left with metacity.
So for me, once I've got compiz up and running there is no need to have fusion try and load compiz at startup, it boots into compiz anyway.

---

### Post by stinkeye on 2009-10-27
Something else I just noticed was that if I had metacity compositing manager enabled 
it would cause the compiz --replace command not to function corectly.See this post:
[_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8171997&postcount=26[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8171997&postcount=26")

---

### Post by quequotion on 2010-02-26
There are about a half dozen related bugs for this in launchpad. I'm going to try the setting WINDOW_MANAGER as soon as I get home, but I'll do it a slightly different way. One of the scripts called by gdm (postlogin/default) may be a good place to set this. I'll post some files and a better explanation later. at the moment I'm in Vista at work *shudder...*

---

### Post by quequotion on 2010-02-26
> **quequotion said:**
>  I'll post some files and a better explanation later.

And here it is. I haven't tested this yet.  I had the wrong file in mind, although that one might work also.

in /etc/gdm/PreSession/Default

there is a line:```
initctl -q emit desktop-session-start DISPLAY_MANAGER=gdm
``` to which I've appended```
 WINDOW_MANAGER=compiz
```

After this post, I'll try it out....


file:```
#!/bin/sh
#
# Note that any setup should come before the sessreg command as
# that must be 'exec'ed for the pid to be correct (sessreg uses the parent
# pid)
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH:/bin:/usr/bin"

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --daemon
fi

initctl -q emit desktop-session-start DISPLAY_MANAGER=gdm WINDOW_MANAGER=compiz
```

---

### Post by Igorpan on 2010-02-26
Hi,i tried all solutions placed from this thread and none didn't work for me.

The thing is: when i login,first few seconds i have visual effects,woobly windows etc,and than screen reloads and they are disabled. For some reason compiz shuts down and changes visual effects to "None". :???:

Sorry for my english,i hope you understood me

Igor

---

### Post by quequotion on 2010-03-04
> **Igorpan said:**
> Hi,i tried all solutions placed from this thread and none didn't work for me.
The thing is: when i login,first few seconds i have visual effects,woobly windows etc,and than screen reloads and they are disabled. For some reason compiz shuts down and changes visual effects to "None". :???:
Igor

Yeah, my idea doesn't work either... the symptoms still persist, even with updated packages from xorg-edgers, dnjl, compiz-packagers and other bleeding-edge ppas.. no good.

What's happening to compiz?

I've specified compiz as the window manager everywhere I can possibly imagine and more. Actually, I don't know how gnome is even able to *find* a startup script for metacity because I certainly can't.

I actually began to suspect that the file permissions of something may be messed up, which would make sense of compiz starting *after* login when called by a user rather than the startup script which may be running as root or a system user...

---

### Post by Igorpan on 2010-03-04
I fixed effects. It turned out the problem were ATI graphics card drivers I downloaded from ATI site. They work fine,but somehow compiz doesn't know how to use them or something like that. I reinstalled old drivers from System->Administration->Hardware Drivers and it works fine.

Only problem is,blender menu is bugged with this driver version

---

### Post by quequotion on 2010-04-12
I'm not entirely sure what fixed this, as I tried dozens of "solutions" and upgraded to some bleeding-edge repositories at the same time...

I think the suggestion of running "fusion-icon -n" at startup was the most effective for me.

---

### Post by krige on 2010-04-15
Try running:
```
sudo apt-get install compiz
```

---

