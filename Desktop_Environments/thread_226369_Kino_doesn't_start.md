---
title: "Kino doesn't start"
date: 2006-07-31
forum: Desktop Environments
---

### Post by salvo1 on 2006-07-31
I have used Kino until 2 month ago...
...today i run it and...

```
salvo@toshiba:~$ kino
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating Preferences
Loading preferences from "/home/salvo/.kinorc"
Saving preferences.
[...]
>>> Image Filter: Sovraimpressione

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:25807): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:25807): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

Kino experienced a segmentation fault.
Dumping stack from the offending thread

Obtained 9 stack frames.
kino(__gxx_personality_v0+0x322) [0x80729c2]
[0xffffe420]
kino(_ZN27PluginImageCreateRepository14InstallPluginsEP6Plugin+0x65) [0x80d0895]
kino(_ZN10PageMagickC1EP10KinoCommon+0x1d1) [0x80d49a9]
kino(_ZN10KinoCommonC1EP10_GtkWidget+0x321) [0x80a8c2b]
kino(kinoInitialise+0x26) [0x80da8b6]
kino(main+0x150) [0x8072b6c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7398ea2]
kino(__gxx_personality_v0+0x221) [0x80728c1]

Done dumping - exiting.

```

What's the matter?

---

### Post by reclusivemonkey on 2006-07-31
My Kino just broke today too. It was fine this morning, I went to work, came back, no updates and all of a sudden I get

```

luke@mother:~$ kino
kino: error while loading shared libraries: libraw1394.so.8: cannot open shared object file: No such file or directory
luke@mother:~$ whereis libraw
libraw: /usr/local/lib/libraw1394.a /usr/local/lib/libraw1394.la /usr/local/lib/libraw1394.so

```

???

---

### Post by greenstar on 2006-08-06
Kino is broken here too. See my thread [here]("http://www.ubuntuforums.org/showthread.php?p=1347744#post1347744") for details.

DV is the only reason I still have an NTFS partition on my box. WinXP hammers Ubuntu in this area. I hate booting into Windows for anything, but I can actually get a video/DVD project done, so I keep it. I can't wait for Linux to get some practically functional NLE's. I can't even help speed things up, as I'm broke & can't code software.:(

Greenstar

---

### Post by reclusivemonkey on 2006-08-07
> **greenstar said:**
> Kino is broken here too. See my thread [here]("http://www.ubuntuforums.org/showthread.php?p=1347744#post1347744") for details.

DV is the only reason I still have an NTFS partition on my box. WinXP hammers Ubuntu in this area. I hate booting into Windows for anything, but I can actually get a video/DVD project done, so I keep it. I can't wait for Linux to get some practically functional NLE's. I can't even help speed things up, as I'm broke & can't code software.:(


I reinstalled my Ubuntu a few days ago. I have been hammering it installing all sorts just to test it out (I use Slackware on most of my machines). On a clean(ish) install, Kino is working great. I have been trying to make a CS video and XP completely fails to do this. Check it out!

[http://www.youtube.com/watch?v=TDRK94MNu2g](http://www.youtube.com/watch?v=TDRK94MNu2g)

---

### Post by greenstar on 2006-08-07
This question is completely unrelated, but how do you get sites like youtube & myspace video to work on Ubuntu or Slack? I assume they work for you since you mention your youtube videos. I can't get around the Flash 9 issue.

Greenstar

---

### Post by reclusivemonkey on 2006-08-07
> **greenstar said:**
> This question is completely unrelated, but how do you get sites like youtube & myspace video to work on Ubuntu or Slack? I assume they work for you since you mention your youtube videos. I can't get around the Flash 9 issue.


I had a problem with YouTube for a couple of days, but now it seems to work fine with Flash 7 in Firefox. For anything else, I just use IEs4Linux, which has Flash 9 installed with it.

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

HTH

---

### Post by greenstar on 2006-08-07
reclusivemonkey, thanks for the info.

Greenstar

---

### Post by rafalr on 2006-08-14
Hi, 

I encountered something very similar, plus:
- when starting Kino as user, it can not see the camera (if started in terminal as gksudo kino it can see the camera)
- when trying some tests of exporting, there are no tools available in DV Pipe sub-menus
- when captuting, the actual image is garbled as in the screenshot (is that matter of codecs ?).

If it matters, I recently played with installinmg XGL and compriz, however was launching Kino in plain gnome-session.

Pls let me know if you figured it out.
Rafal

---

### Post by rafalr on 2006-11-28
Just for anyone following the thread here is the solution that worked for me:

1. The effect I encounter is:
- fuzzy (=striped and fragmented) picture
- no reaction to mouse clicks on timebar, shuttlebar, 
stop/pause buttons (after a mouse click I need to 
change the workpanel to make Kino react/stop playing)
- export problems via DV Pipe / Dual pass DVD / ffmpeg 
(the process breaks after couple of minutes (othough 
this possibly not related to XGL).

I suspected it could have been about XGL/Compiz which 
I recently configured, and apparently it was right assumption.
I am running Kino 0.8.0 on Ubuntu Dapper kernel 
2.6.15, AMD 64 and Nvidia 5500. All libraries 
installed.

To have all three problems eliminated and get Kino 
back into a perfect and clear cut working I only 
needed to reedit my /etc/gdm/gdm.conf-custom file and 
to hash anything that has been added while configuring 
XGL. 
This part of file should look as below:
code
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
#Browser=true

[chooser]

[debug]

[servers]
#0=Xgl 
#
#[server-Xgl]
#name=Xgl server 
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel 
glx:pbuffer -accel xv:fbo 
#flexible=true
end code

Another important note is that I do not launch compiz 
as default from session manager/gdm, but start it on 
demand from script (that is I do not need to toggle 
with metacity/compiz to get Kino working).

Sadly, whenever I want to play with XGL/compiz I need 
to reedit this gdm-conf file, and when I want to use 
Kino I need to hash it back. Actually I have two versions 
of /etc/gdm/gdm.conf-custom file (hashed = Kino and unhashed = XGL), and depending on need I rename the one that needs to be inactive.

Hope this helps,
Rafal

---

