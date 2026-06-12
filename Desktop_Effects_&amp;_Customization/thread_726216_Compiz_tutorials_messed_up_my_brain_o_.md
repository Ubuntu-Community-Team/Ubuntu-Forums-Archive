---
title: "Compiz tutorials messed up my brain o_*"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by Kenniej on 2008-03-16
Hello everyone !

I bet some of the regular forum visitor must have seen these kind of post before, well so have i >_<..

I'm just gonna drop tha bomb : 

 1) I installed Ubuntu 7.10(Gutsy)
 2) Followed the un-official wiki guide to install ATI restricted driver(from their un-official wiki    at the ATI driver download site)
 3) Because i wanted to have a Big Desktop with my 2 monitors i also installed the ATI Catalyst control center for easy setting to make it 1 big desktop over 2 monitors, 

   intermezzo : That all worked , JeeeJ  [-o<[-o<=D>=D>:-\":-\"

 4) Followed numerous guides to get Compiz to work (this is where the play get's dark & sinister)
 
So now i'm stuck at this ; When i want to turn on some visual effects i get
            "Desktop effects could not be enabled "

 Some output : 

kenny@kenny:~$ glxinfo 
```

name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
[B]server glx vendor string: SGI
server glx version string: 1.2[/B]
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
**client glx vendor string: SGI**
**client glx version string: 1.4**
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
**GLX version: 1.2**
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
[B]OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.7412 Release[/B]

```

Then i tried to install xserver-xgl, restarted X only to get the same problem [this poor lad has]("http://ubuntuforums.org/showthread.php?t=660413&page=2") (after rebooting the login hangs & returned me to the login screen each time)

My xorg.conf at this moment can be viewed [here]("http://kenniej.madoka.be/xorgBackUpLast.conf")

Hope i gave all the needed information for someone to get a slightest clue to what this can be, if not , ask.

Hope someone can get me out of this, been nagging my brainz for 2 days now :(

Greetings
and thnx in advance!
Kenniej

---

### Post by Kabezon on 2008-03-17
Compiz is installed by default in Gutsy, you did not need to try and install anything else. I'm not a  Linux pro to tell you the truth, but I can get everything thats eyecandy to work in 10 mins :P Why don't you try doing it the easy way? Let [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")[1] do it for you. Then just install compizconfig-settings-manager to easily configure Compiz, and you're ready to go =] My 2 cents, hope it helps.

[1]"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you

Envy features both a GUI (which you can launch only inside a Desktop Environment) and a textual interface which you can use if, for example, you cannot start the Xserver.

---

### Post by Kenniej on 2008-03-17
Unf , after fiddeling around a bit i can get compiz working with CLONE desktop but not with Big desktop, getting this error when running compiz from terminal
```
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
```

Any idea how to set this max size higer ?

---

### Post by mrmiserable on 2008-03-17
you have to set it to 2048x1024 

2056x1024 is exceeding your graphic card limit

open xorg.conf 

sudo gedit /etc/X11/xorg.conf 

scroll down to screen add 2048x1024 like this

SubSection "Display"
		Depth		24
		Modes		"2048x1024" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

then when you reboot under your screen resolution in sytem/preferences use 2048x1024  and compiz will now do big desktop ati cards dont give this option on amdccle i had same problem it was the only way around it

hope this helps

---

### Post by usererror on 2008-03-18
Can you post your entire xorg.conf file?  I added the addional resolution but too cannot get compiz to enable itself still does not work, i am using the option "Ximerama" in my dual monitor setup so i can drag windows between each monitor...

in fact if i try to change my resolution via System > Preference or Administration, it says it can't do it!

EDIT: Never Mind.  It's a hardware restriction on my ATI 9800 =( bummer, time get an NVIDIA card now...

---

### Post by mrmiserable on 2008-03-18
i dont use two screens anymore but this is my old xorg.conf from another thread
not sure if xinerama is problem just dont know maybe someone else knows
anyway here is link to my xorg

[http://ubuntuforums.org/showthread.php?t=581499](http://ubuntuforums.org/showthread.php?t=581499)

also to drag between windows i did not need xinerama it just worked without it

---

### Post by usererror on 2008-03-18
> **mrmiserable said:**
> i dont use two screens anymore but this is my old xorg.conf from another thread
not sure if xinerama is problem just dont know maybe someone else knows
anyway here is link to my xorg

[http://ubuntuforums.org/showthread.php?t=581499](http://ubuntuforums.org/showthread.php?t=581499)

also to drag between windows i did not need xinerama it just worked without it

Thanks for the post, that's odd that you didn't need Ximerama to make dragging windows between monitors work, oh well. Thanks for the post!

---

### Post by mrmiserable on 2008-03-18
maybe because in compiz  it has option for on big cube
also hope you get it to work

---

### Post by Kenniej on 2008-03-18
> **usererror said:**
> 
EDIT: Never Mind.  It's a hardware restriction on my ATI 9800 =( bummer, time get an NVIDIA card now...

Same here,

well i got it to work with my ati 9800 pro card using the suggestion of mrmiserable, but that was such a low resolution & since ati capped that max 3D texture size an 2048 i had no choise... and plugged in my old FX 5500 card, nvidea atleast can go up to 4048 (or in that area).

So ! Works great on ATI 9800 pro, just small resolution imo :p

Thnx very much for everyone's help , it was highly appriciated.


Greetz,
Kenniej

---

