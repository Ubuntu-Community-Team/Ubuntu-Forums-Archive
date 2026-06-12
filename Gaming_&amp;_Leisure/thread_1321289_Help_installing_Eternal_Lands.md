---
title: "Help installing Eternal Lands"
date: 2009-11-09
forum: Gaming &amp; Leisure
---

### Post by abrake on 2009-11-09
Hey, I'm on a fresh installation of karmic, brand new to ubuntu.. I installed the game via the script here:[https://help.ubuntu.com/community/EternalLands](https://help.ubuntu.com/community/EternalLands). Anyway the starts up fine, but when I try to create a character I get this error log:

[23:56:56] Error: Can't open file "quest.log"
[23:56:56] * server [www.eternal-lands.com](www.eternal-lands.com) filename [http://www.eternal-lands.com/updates180/files.lst](http://www.eternal-lands.com/updates180/files.lst)
[23:56:56] Downloading [http://www.eternal-lands.com/updates180/files.lst](http://www.eternal-lands.com/updates180/files.lst) from [www.eternal-lands.com](www.eternal-lands.com)
[23:56:56] Error: Can't open file "alias.ini"
[23:56:56] Finished downloading [http://www.eternal-lands.com/updates180/files.lst](http://www.eternal-lands.com/updates180/files.lst)
[23:56:57] * server [www.eternal-lands.com](www.eternal-lands.com) filename [http://www.eternal-lands.com/updates180/files.lst](http://www.eternal-lands.com/updates180/files.lst)
[23:56:57] Downloading [http://www.eternal-lands.com/updates180/files.lst](http://www.eternal-lands.com/updates180/files.lst) from [www.eternal-lands.com](www.eternal-lands.com)
[23:56:57] Finished downloading [http://www.eternal-lands.com/updates180/files.lst](http://www.eternal-lands.com/updates180/files.lst)
[23:56:58] Failed to download (files.lst) 3 times. Giving up.
[23:56:58] * server [www.eternal-lands.com](www.eternal-lands.com) filename [http://www.eternal-lands.com/updates/custom_files.lst](http://www.eternal-lands.com/updates/custom_files.lst)
[23:56:58] Downloading [http://www.eternal-lands.com/updates/custom_files.lst](http://www.eternal-lands.com/updates/custom_files.lst) from [www.eternal-lands.com](www.eternal-lands.com)
[23:56:58] Finished downloading [http://www.eternal-lands.com/updates/custom_files.lst](http://www.eternal-lands.com/updates/custom_files.lst)
[23:57:05] Language changed, was [en] now [en]

This was the program output:  Note it is overwritten each time you run the game.

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
el.x86.linux.bin: brw_vs_emit.c:936: get_src_reg: Assertion `0' failed.

Any idea what I can do to fix this?

---

### Post by claudiam on 2009-11-10
[LEFT]I get a similar output, but it happens when I try to connect to the server. :S
[/LEFT]

[18:57:48] Using the server profile: main
[18:57:48] Window size adjusted to 1014x713
[18:57:49] GL_ARB_multitexture extension found, using it.
[18:57:49] GL_EXT_compiled_vertex_array extension found, using it.
[18:57:49] GL_ARB_point_sprite extension found, using it.
[18:57:49] GL_ARB_texture_compression extension found, using it.
[18:57:49] GL_EXT_texture_compression_s3tc extension found, using it.
[18:57:49] GL_SGIS_generate_mipmap extension found, using it.
[18:57:49] GL_ARB_shadow extension found, using it.
[18:57:49] GL_ARB_vertex_buffer_object extension found, using it.
[18:57:49] GL_EXT_framebuffer_object extension found, using it.
[18:57:49] GL_EXT_draw_range_elements extension found, using it.
[18:57:49] GL_ARB_texture_non_power_of_two extension found, using it.
[18:57:49] GL_ARB_fragment_program extension found, using it.
[18:57:49] GL_ARB_vertex_program extension found, using it.
[18:57:49] GL_ARB_fragment_shader extension found, using it.
[18:57:49] GL_ARB_vertex_shader extension found, using it.
[18:57:49] GL_ARB_shader_objects extension found, using it.
[18:57:49] GL_ARB_shading_language_100 extension found, using it.
[18:57:49] GL_ARB_texture_mirrored_repeat extension found, NOT using it...
[18:57:49] GL_ARB_texture_rectangle extension found, NOT using it...
[18:57:49] GL_EXT_fog_coord extension found, NOT using it...
[18:57:49] Couldn't find the GL_ATI_texture_compression_3dc extension, not using it...
[18:57:49] Couldn't find the GL_EXT_texture_compression_latc extension, not using it...

This was the program output:  Note it is overwritten each time you run the game.

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

---

### Post by gordong11 on 2009-11-18
Same here, someone? anyone? please :) Running 9.10 Karmic with 185 nvidia drivers activated


rob@rob-desktop:~$ eternallands
/usr/games/eternallands: line 149: 12496 Segmentation fault      /usr/games/el.x86.linux.bin $config $* &>~/.elc/terminal_log.txt

Log started at 2009-11-18 22:37:39 localtime (EST)

[22:37:39] Using the server profile: main
[22:37:39] Window size adjusted to 1014x713
[22:37:39] GL_ARB_multitexture extension found, using it.
[22:37:39] GL_EXT_compiled_vertex_array extension found, using it.
[22:37:39] GL_ARB_point_sprite extension found, using it.
[22:37:39] GL_ARB_texture_compression extension found, using it.
[22:37:39] GL_EXT_texture_compression_s3tc extension found, using it.
[22:37:39] GL_SGIS_generate_mipmap extension found, using it.
[22:37:39] GL_ARB_shadow extension found, using it.
[22:37:39] GL_ARB_vertex_buffer_object extension found, using it.
[22:37:39] GL_EXT_framebuffer_object extension found, using it.
[22:37:39] GL_EXT_draw_range_elements extension found, using it.
[22:37:39] GL_ARB_texture_non_power_of_two extension found, using it.
[22:37:39] GL_ARB_fragment_program extension found, using it.
[22:37:39] GL_ARB_vertex_program extension found, using it.
[22:37:39] GL_ARB_fragment_shader extension found, using it.
[22:37:39] GL_ARB_vertex_shader extension found, using it.
[22:37:39] GL_ARB_shader_objects extension found, using it.
[22:37:39] GL_ARB_shading_language_100 extension found, using it.
[22:37:39] GL_ARB_texture_mirrored_repeat extension found, NOT using it...
[22:37:39] GL_ARB_texture_rectangle extension found, NOT using it...
[22:37:39] GL_EXT_fog_coord extension found, NOT using it...
[22:37:39] Couldn't find the GL_ATI_texture_compression_3dc extension, not using it...
[22:37:39] Couldn't find the GL_EXT_texture_compression_latc extension, not using it...

This was the program output:  Note it is overwritten each time you run the game.

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

---

### Post by gordong11 on 2009-11-19
OK OK .....i HAVE GOT THE FIX!! THANKS TO PIPER.

GET RID OF NVIDIA 185 DRIVER. 

GOTO SYSTEM>HARDWARE DRIVERS, AND ACTIVATE 173 VERSION. THEN REBOOT. YOUR ARE AS GOOD AS GOLD.

[B]Or (for Karmic 32-bit users)
[/B]
GET NEW 190.43 DRIVERS INSTALLED, deemed stable. was beta now been certified by nvidia and should show in your hardware drivers menu as recommended, with activated green light, when installed.

Karmic:

1. sudo add-apt-repository ppa:nvidia-vdpau/ppa

2. sudo gedit /etc/apt/sources.list

3. Add and save:

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

4. sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

5. sudo apt-get update

6. sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings-190

I rebooted, but check menu *system>administration>HardwareDrivers* for green light as activated.

THE ABOVE INSTRUCTIONS WAS TAKEN FROM LINK BELOW.

**Older Ubuntu versions: for sources apt lines see**:

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)



Note for 9.10 Karmic users: I manually deleted the words "jaunty main" and changed it to "karmic main" in the apt lines instructions from the ubuntugeek link above. They did not provide apt lines for karmic. It worked flawless for me and shows as activated and recommended in my hardware drivers menu.

Enjoy EL

---

### Post by claudiam on 2009-11-19
Installing the beta drivers worked perfectly. Thanks! :D

---

### Post by gordong11 on 2009-11-19
Those arent beta drivers anymore, the 190.42 has been certified, should show in your hardware drivers menu as recommended/activated. which is cool


I'm glad it worked for you too. :) EL is a great game IMO.

---

### Post by gordong11 on 2009-11-23
I can confirm, for me anyway running 9.10, running realtek sound from my mobo or my Sblaster audigy SE card, upgrading to 1.0.21 drivers help, big time. Night and day difference.

I was getting horrible sound, very scratchy. use this link and your sound will greatly improve.

[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

NOTE: in step four u must include the period at the end of the terminal command:

"sudo cp ~/alsa* ."

---

### Post by LutraMan on 2009-12-08
I have a similar problem, just with UT3. I tried installing 173 or 19 nvidia drivers, and I still don't have it working.
Did you had to reinstall the game or Wine after reinstalling the nvidia drivers?

---

### Post by gordong11 on 2009-12-08
I'm not sure of UT3, but for eternal lands just follow the ubuntu instructions for gui, after u install drivers. Eternal lands is a linux game, so wine isnt needed. different animal for ut3

---

### Post by pjbroad on 2010-01-04
> **abrake said:**
> ....
el.x86.linux.bin: brw_vs_emit.c:936: get_src_reg: Assertion `0' failed.

Are you still having this problem?

---

### Post by retro89 on 2010-01-04
Try playdeb [http://www.playdeb.net/software/Eternal%20Lands](http://www.playdeb.net/software/Eternal%20Lands)

---

### Post by pjbroad on 2010-01-04
> **retro89 said:**
> Try playdeb [http://www.playdeb.net/software/Eternal%20Lands]("http://www.playdeb.net/software/Eternal%20Lands")
That's just a rebuild of the original packages.  The original thread problem is with a particular graphic card/driver not the packages.

---

