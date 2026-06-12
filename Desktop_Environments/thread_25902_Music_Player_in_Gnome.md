---
title: "Music Player in Gnome"
date: 2005-04-11
forum: Desktop Environments
---

### Post by teumima on 2005-04-11
This is the error I get everytime I try to play an mp3 on Music Player

Internal GStreamer error: negotiation problem.  File a bug.

It used to work great.

Any ideas?

Assistance appreciated.

a.t.

---

### Post by lorap on 2005-04-11
hi!
you should add XMMS player.
i had the same troubles.
go to Computer-->System Configuration-->Synaptic Package Manager.
once you have synaptic's window open go to the Settings-->Repositories.
once you have the repositories' window open mark all checkboxes available then press Ok button.once you are back to synaptic's window press Reload button.
once the process completes press the Search button,write in the search window XMMS then press Ok button.once the synaptic picks it up for you mark it for install then press Apply button.now you are done.after the installation process completes close the synaptic window and the next time you open mp3 file choose XMMS.it is great looking player.the same thing for VLC player for mp4,divx and xvid files.
have a nice day!
pavel

---

### Post by teumima on 2005-04-11
[QUOTE=lorap]hi!
you should add XMMS player.
i had the same troubles.
go to Computer-->System Configuration-->Synaptic Package Manager.
once you have synaptic's window open go to the Settings-->Repositories.
once you have the repositories' window open mark all checkboxes available then press Ok button.once you are back to synaptic's window press Reload button.
once the process completes press the Search button,write in the search window XMMS then press Ok button.once the synaptic picks it up for you mark it for install then press Apply button.now you are done.after the installation process completes close the synaptic window and the next time you open mp3 file choose XMMS.it is great looking player.the same thing for VLC player for mp4,divx and xvid files.
have a nice day!
pavel[/QUOTE]
 Hey man.

Thanx for the reply. I have all those players. I just want the Music Player to work too.

---

### Post by doclivingston on 2005-04-11
If Rhythmbox is reporting that it is probably going to be one of the following three

a) GStreamer has a configuration problem. If you can play other mp3s (in Rhythmbox), it shouldn't be this one
b) The mp3 has become, or always was, corrupted; some other programs might be able to play it regardless though.
c) An actual bug in GStreamer (a lot less likely, but still possible)

Could you see what the following command reports?

```
gst-launch-0.8 'filesrc location=/path/to/music.mp3 ! spider ! alsasink'
```

Edit: fixed command

---

### Post by teumima on 2005-04-11
?: \

** (process:28722): WARNING **: error: syntax error, unexpected $undefined
RUNNING pipeline ...
ERROR: from element /pipeline0/filesrc0: No file name specified for reading.
ERROR: pipeline doesn't want to play.
amichai@bzq-179-124-6:~$

---

### Post by doclivingston on 2005-04-11
Oops. You need to remove the quotes from the above command (and make /path/to/music.mp3 actually point to the mp3).

That's what I get for not checking the command on my machine beore posting.

---

### Post by danip on 2005-04-11
sudo apt-get install gstreamer0.8-plugins

That should fix it.

---

### Post by teumima on 2005-04-12
[QUOTE=doclivingston]Oops. You need to remove the quotes from the above command (and make /path/to/music.mp3 actually point to the mp3).

That's what I get for not checking the command on my machine beore posting.[/QUOTE]
 amichai@bzq-179-124-6:~$ gst-launch-0.8 filesrc location=/home/amichai/Shared/BobMarley-IsThisLove.mp3 ! spider ! alsasink
RUNNING pipeline ...
ERROR: from element /pipeline0/spider0/mad0: Internal GStreamer error: pad problem.  File a bug.
Additional debug info:
gstpad.c(2563): gst_pad_set_explicit_caps: /pipeline0/spider0/mad0:
failed to negotiate (try_set_caps with "audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)44100, channels=(int)2" returned REFUSED)
ERROR: from element /pipeline0/spider0/mad0: Internal GStreamer error: negotiation problem.  File a bug.
Additional debug info:
gstmad.c(1199): gst_mad_check_caps_reset: /pipeline0/spider0/mad0:
Failed to negotiate 44100 Hz, 2 channels
Execution ended after 2 iterations (sum 139794000 ns, average 69897000 ns, min 208000 ns, max 139586000 ns).
amichai@bzq-179-124-6:~$

---

### Post by teumima on 2005-04-12
[QUOTE=danip]sudo apt-get install gstreamer0.8-plugins

That should fix it.[/QUOTE]
 i already have the latest version

---

### Post by doclivingston on 2005-04-12
I know what kind of problem it is (mad and the alsa library don't want to talk to each other), but not how to fix it. You can try running ```
sudo gst-register-0.8
``` to see if that helps, but it probably won't.

I'm not an expert as GStreamer stuff, so if no-one else has any ideas, all I could suggest is reporting it in the GStreamer bugzilla.

---

### Post by teumima on 2005-04-12
[QUOTE=doclivingston]I know what kind of problem it is (mad and the alsa library don't want to talk to each other), but not how to fix it. You can try running ```
sudo gst-register-0.8
``` to see if that helps, but it probably won't.

I'm not an expert as GStreamer stuff, so if no-one else has any ideas, all I could suggest is reporting it in the GStreamer bugzilla.[/QUOTE]
 no didnt work

---

### Post by nocturn on 2005-04-12
Do you have the gstreamer*mad package (can't remember the exact name), it is not installed by default.

I installed this and playback works very well.

---

### Post by teumima on 2005-04-12
[QUOTE=nocturn]Do you have the gstreamer*mad package (can't remember the exact name), it is not installed by default.

I installed this and playback works very well.[/QUOTE]
 hey man

can't find it.

---

### Post by steffen on 2005-04-14
I have the same issue in Sound Juicer. I just got it to rip mp3s, and after ripping two mp3s it just turns up with this error.

I did everything by the book (Ubuntu Wiki) and did a gst-register-0.8 before loading. Tried on several CDs as well, and even after a reboot, this error comes up as soon as I try to rip an mp3.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=teumima]hey man

can't find it.[/QUOTE]


Did you try **sudo apt-get install gstreamer-0.8-mad**? Also, do you have Marillat's repository in /etc/apt/sources.list? I think it's in there.

---

### Post by dastin on 2005-09-07
Dont know if you are still having a problem but I ran into this issue also today.
I figured out that it was becuase I had changed Default sink to ALSA and the Default Source to ALSA (in gstreamer-properties)
To fix it I ran as my regular user (not sudo) gstreamer-properties and changed the default sink back to ESD and the default source to OSS
After this Rythmbox started working again.
Hope this helps

---

