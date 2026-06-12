---
title: "Desktop effects could not be enabled. WHY?"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by MSdefecter on 2008-03-18
Hi,
I have tried several times to get desktop effects working on my system and had no luck. I keep getting told by unhelpful people that I need to get restricted drivers but every time I open up the restricted drivers tab it tells me that my hardware doesn't require any. I have an Nvidia geforce 8800gts 512mb. I have also tried to use nvidia driver from the list of available drivers but when ever I enable it my screen resolution drops to 800x600. So I am sticking for the moment to the default driver that it installs with.

---

### Post by PurposeOfReason on 2008-03-18
In a terminal type
```
compiz --replace
``` and post the results here.

---

### Post by WFGeppetto on 2008-03-18
Hey, I'm not him, but I am having a very similar problem.  I had it all working fine, then like an idiot, I ran Envy.  It screwed it all up.  I got my old flgrx driver back, and I can finally (after lots of crap) log in to the xclient, but my desktop effects are shot.

heres my output for that:

```
wfgeppetto@GPTO:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

```

When I do that, it makes the screen flash, and when I close the terminal, it flashes again.  I was just about to try to reinstall all the compiz stuff I could find in synaptics, but I figured I had better check this out first.

---

### Post by jacob01 on 2008-03-18
are the ati drivers installed properly and is direct render enabled

run    glxinfo              and see if direct render says yes

---

### Post by WFGeppetto on 2008-03-18
alrighty, here's the output:

```
wfgeppetto@GPTO:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
wfgeppetto@GPTO:~$ 

```

But, when I do 'compiz' I get this:

```
wfgeppetto@GPTO:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

```

---

### Post by PurposeOfReason on 2008-03-18
It's saying that compiz isn't present AKA it's not installed. . .

---

### Post by WFGeppetto on 2008-03-18
Yes, I see that.  Yet, everything is installed, there just isn't a compiz in my /bin.  I have reinstalled all the comiz stuff I can find, but I still get the same error.

---

### Post by PurposeOfReason on 2008-03-18
> **WFGeppetto said:**
> Yes, I see that.  Yet, everything is installed, there just isn't a compiz in my /bin.  I have reinstalled all the comiz stuff I can find, but I still get the same error.
Try sudo cp /usr/bin/compiz /usr/local/bin and do it again or vise versa.

---

### Post by PurposeOfReason on 2008-03-18
Also, post your /etc/X11/xorg.conf

---

### Post by WFGeppetto on 2008-03-18
OMG, (I know nooby) I love you, I think.

My terminal is going crazy, and there's lots of nice "present" words showing up.

Yay!  I think that might have done it.  I'm scared to close my terminal until it stops though.

---

### Post by PurposeOfReason on 2008-03-18
Any chance you can get a snippet of that? Nothing should really be flying by unless you mean it is when you typed compiz --replace. Either way, keep us updated. :)

---

### Post by WFGeppetto on 2008-03-18
I'm trying to keep up but my computer is running like crap now.

It locked up, and I had to hard boot it.  The code was something about "enabling ati driver, present", but it never stopped saying it.

Now everything runs very slowly, and sketchy. Also, my desktop looks bad.  The show desktop, and the date are all sketchy looking.  Firefox doesn't even scroll properly.

bah, try compiz --replace again?

---

### Post by WFGeppetto on 2008-03-18
Also, the little buttons in this input window (bold, italic, etc) are all goofy looking.  Something is weird, wrong.

---

### Post by PurposeOfReason on 2008-03-18
First run sudo -rm /usr/local/bin/compiz.

That command will remove the link we just created as that appears to be the problem. After that please post your xorg.conf.

---

### Post by WFGeppetto on 2008-03-18
Ah, I got it to stop with the scroll bar at the right.  It says:

Enabling Xgl with flgrx drivers...
Checking for Xgl:  present
Checking for Nvidia:  not present

over, and over, and over again.

---

### Post by PurposeOfReason on 2008-03-18
> **WFGeppetto said:**
> Ah, I got it to stop with the scroll bar at the right.  It says:

Enabling Xgl with flgrx drivers...
Checking for Xgl:  present
Checking for Nvidia:  not present

over, and over, and over again.

So the choppiness is fixed? I'll still need your xorg.conf. If you want, PM me and I'll be on pidgin.

---

### Post by lduplantie on 2008-03-18
I don't know if this will help, but here is how I made Compiz work on less powerful hardware.

I am running Ubuntu 7.10 and using the Ubuntu supplied nvidia driver for my Quadro2 (32Mb) card with the proprietary driver enabled.

I edited the nvidia configuration file with the following command in a terminal
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

I installed compizconfig-settings-manager from Synaptic.

I installed the compiz-fusion icon. You can get it here: [http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD;sf=tgz](http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD;sf=tgz)

Then install it from a terminal with  these commands:
```
tar -zxvf fusion-icon-HEAD.tar.gz
cd fusion-icon
sudo make install
```

You can find it in the menu from Applications->System Tools->Compiz Fusion Icon.

fusion-icon will start Compiz with the parameters it thinks will work best with your system when it launches. Right click on the Icon in the panel to access options.

---

### Post by WFGeppetto on 2008-03-18
Ok, I am about to give up.  Thanks loads for the IM convo Purpose of Reason.

Now, it's doing that weird loop thing again, when I do compiz --replace.

I can barely use Ubuntu at all in normal session, and failsafe gnome is even sketchy.  To make matters worse, for some inexplicable reason, my network manager took a crap too.  I never even messed with any of that.  Anyway, I can't even get on the internet without hardwiring, and I never touched anything that should have anything to do with the network manager.  It even times out when I try to manually configure the network settings.

I have no idea what happened, or why it's so goofed up.  Everything was fine, until I ran Envy.  I don't really see what any of this has to do with my network manager, but I'm over it.

I suppose I will simply reinstall.  I had to come to windows to post this, and I really want my ubuntu back, it just seems to have too many problems.  It was so nice this morning.  I should never have messed with Envy, the flgrx driver was working fine.

---

### Post by MSdefecter on 2008-03-19
Sorry man, me again the oringinal noob in this post. I entered compiz --replace in the terminal and this is the output.

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

I suppose this means that I do not have compiz but I have installed the application using a different post with the command and it does appear in my preferences tab.

sudo apt-get update && sudo apt-get install compizconfig-settings-manager

---

### Post by WFGeppetto on 2008-03-20
I don't know for sure, but I bet someone one will come, or I may be able to get someone to come...

Anyway, I think, but I don't know, that you forgot to install xserver-xgl.  Go to System->Administration->Synaptics Package Manager.  Search for "xserver-xgl" and install it.  Then after following whatever instructions, log out, and log back in. or ctrl-alt-backspace, and log back in.

Then try again.  Post what happens, or if it doesn't work.  I'm sure, either that will do it, or someone more competent will show up.  I'll watch this thread, and try to make sure you figure it out.

Edit:  Did you already enable your restricted drivers?

---

### Post by daniel-linux on 2008-03-20
> **MSdefecter said:**
> Sorry man, me again the oringinal noob in this post. I entered compiz --replace in the terminal and this is the output.

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

I suppose this means that I do not have compiz but I have installed the application using a different post with the command and it does appear in my preferences tab.

sudo apt-get update && sudo apt-get install compizconfig-settings-manager

are you running ubuntu as a vmachine? the 3d driver is required no matter what the system says

you should also install compiz and compiz plugins, not only ccsm

---

### Post by MSdefecter on 2008-03-20
This is not a Vm. What is the best way to obtain these drivers if the restricted drivers manager won´t do it for me. Also due to my newness to ubuntu what is the command needed to install compiz?

---

### Post by WFGeppetto on 2008-03-21
What version of Ubuntu are you using?  If you have Gutsy Gibbon 7.10, then it's already installed, and it's just a matter of activating it properly.

---

### Post by MSdefecter on 2008-03-21
Hi,
I appologize for not explaining myself properly. I am running version 7.10. The reason I installed this one was because I, as must be quite evident by now need to learn about Ubuntu and Linux in general, but I was intrigued by the demo of bery and later Compizl that I saw on the net. How would I configure Compiz correctly and any drivers that I may require?

---

