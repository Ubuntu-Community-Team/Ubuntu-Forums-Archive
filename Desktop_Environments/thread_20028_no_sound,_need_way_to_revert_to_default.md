---
title: "no sound, need way to revert to default"
date: 2005-03-14
forum: Desktop Environments
---

### Post by jordanau on 2005-03-14
After trying the how to about multiple sound, I totally lost sound. BTW I think this belongs here because it doesn't have much to do with making the howto better. Anyway, Is there a way to get my sound back to the way it was when I first installed Ubuntu a week ago?? Is there some sort of autodetect? Would upgrading to Hoary let me start fresh??I am using onboard sound with an nForce 2 chip if it matters. I tried deleting the files i added and changing old files to default but it doesn't help. Would getting rid of Alsa do the trick? 
For some reason, "sudo apt-get install fix-my-damn-computer" isn't working right now.

If I am not making sense, let me know, I will be glad to specify anything necessary.

---

### Post by kassetra on 2005-03-14
[QUOTE=jordanau]After trying the how to about multiple sound, I totally lost sound. BTW I think this belongs here because it doesn't have much to do with making the howto better. Anyway, Is there a way to get my sound back to the way it was when I first installed Ubuntu a week ago?? Is there some sort of autodetect? Would upgrading to Hoary let me start fresh??I am using onboard sound with an nForce 2 chip if it matters. I tried deleting the files i added and changing old files to default but it doesn't help. Would getting rid of Alsa do the trick? 
For some reason, "sudo apt-get install fix-my-damn-computer" isn't working right now.

If I am not making sense, let me know, I will be glad to specify anything necessary.[/QUOTE]

Ok, I need to know what you did first of all... Did you install Alsa (you should have had some things already installed) ... 
Deleting files -- you mean uninstalling?
I need a bit more info to help you get it back.  :)

---

### Post by nanaban on 2005-03-14
[QUOTE=jordanau]After trying the how to about multiple sound, I totally lost sound. BTW I think this belongs here because it doesn't have much to do with making the howto better. Anyway, Is there a way to get my sound back to the way it was when I first installed Ubuntu a week ago?? Is there some sort of autodetect? Would upgrading to Hoary let me start fresh??I am using onboard sound with an nForce 2 chip if it matters. I tried deleting the files i added and changing old files to default but it doesn't help. Would getting rid of Alsa do the trick? 
For some reason, "sudo apt-get install fix-my-damn-computer" isn't working right now.

If I am not making sense, let me know, I will be glad to specify anything necessary.[/QUOTE]
 Same here, I used to got sound working when I first installed Hoary. I switched to polydaudio because some said it's better, but I got no sound. Now I just want to switch back to esd, what's the package that I need to install to revert to the default setting?

---

### Post by jordanau on 2005-03-15
Thank you for your quick reply, 
I installed the files that were in the howto. This included libesd-alsa0.
Possibly installed libsdl1.2debian-alsa and vlc-pluging-alsa. I will have to boot into linux to check. I have not uninstalled any of the files. 


When I say I deleted files I was refering to asound.conf. I removed it because it did not exist before I began the howto. I also deleted the manual changes I made to esd.conf. (I am very careful to add comments that say what I did to the file and why).
This entailed deleting "-d dmixer" from the end of one of the lines. 

anything else I am missing? If I just need to reinstall Ubuntu, I don't mind as long as someone can tell me how to save my NDISwrapper package to that I don't have to physically move my computer around the house trying to connect to my router manually.

---

### Post by jordanau on 2005-03-15
Excuse the double post but I think I am actually getting somewhere with my sound. I still have no sound but I found the /etc/asound.conf for my specific onboard sound card from the Alsa wiki. I use this asound.conf and add "-d dmixer" to my /etc/esound/esd.conf and I get an error. For some reason I think that this actually might be a bug. I have heard people mention that they also have gstreamer-properties crash when enabling Alsa. I have also heard that hoary does not have this problem. Do you think upgrading to hoary could fix the bug? I will post my different files here:

this is the error that I get when I set sound sink to Alsa and click test:
```

jordan@JordanUbuntu:~ $ gstreamer-properties
gstreamer-properties: pcm.c:2094: snd_pcm_wait: Assertion `err == 1' failed.
Xlib: unexpected async reply (sequence 0x132a)!
```

This is my /etc/esound/esd.conf file:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d dmixer
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
#added "-d default" to the end of line 3 on march 10 2005
```

This is my /etc/asound.conf file:
```

pcm.nforce-hw {
    type hw
    card 0
}
pcm.!default {
    type plug
    slave.pcm "nforce"
}
pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 32768
        rate 48000
    }
}
ctl.nforce-hw {
    type hw
    card 0
}
```

I am new to linux (though I am catching on very fast) so it could be a very obvious thing that I don't understand.

Finally, I get no sound with ESD or OSS either, even though I used to with esd

---

