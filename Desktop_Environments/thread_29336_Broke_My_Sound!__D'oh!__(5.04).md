---
title: "Broke My Sound!  D'oh!  (5.04)"
date: 2005-04-23
forum: Desktop Environments
---

### Post by General_Tso on 2005-04-23
Hello, folks.

My sound was working, but occasionally the usual chimes seemed to hesitate so I decided to follow this segment of [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/#configuresoundproperly) and after restart I had no sound.  The red flag during the process was after I ran "sudo apt-get install libesd-alsa0" I got a long string of dependency errors.  X package wasn't going to be installed b/c it depended on Y and so on.  I do not have the actual text, unfortunately.  Do any of you know where I went astray and how I might correct my error?

Thanks!

---

### Post by Nis on 2005-04-24
[QUOTE=General_Tso]Hello, folks.

My sound was working, but occasionally the usual chimes seemed to hesitate so I decided to follow this segment of [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/#configuresoundproperly) and after restart I had no sound.  The red flag during the process was after I ran "sudo apt-get install libesd-alsa0" I got a long string of dependency errors.  X package wasn't going to be installed b/c it depended on Y and so on.  I do not have the actual text, unfortunately.  Do any of you know where I went astray and how I might correct my error?

Thanks![/QUOTE]
 In /etc/asound.conf, replace
```

pcm "hw:1,0"

```
with
```

pcm "hw:0,0"

```
Reboot and see if that works.

---

### Post by General_Tso on 2005-04-24
[QUOTE=Nis]In /etc/asound.conf, replace
```

pcm "hw:1,0"

```
with
```

pcm "hw:0,0"

```
Reboot and see if that works.[/QUOTE]

Thank you for your quick response, Nis.  However, that did not seem to correct the problem.  After the reboot and still no sound, I did try experimenting the Multimedia Systems Selector.  On the default sink, the only option that produced a test chime was OSS.  None of the pipelines produced a test chime for the default source.  I did manage to crash gstreamer-properties once during this process.  I'm unsure what the cause was, but it seemed as though I was running tests too rapidly as that was how I was able to recreate the crash.  That is probably unrelated, but I thought I'd mention it nonetheless.

Thanks again for the input.  I would appreciate any other suggestions you might have.

---

### Post by crazybill on 2005-04-24
Take it in steps:
Make sure your speakers are powered on, and that it has a good and correct connection to your computer.

See if your sound card is working ok:

# **cat /usr/lib/openoffice/share/gallery/sounds/train.wav > /dev/dsp**

If you hear the sound of a train, you have no problem with your sound card or driver. 

Then you go to other steps with software setup.

---

### Post by General_Tso on 2005-04-24
[QUOTE=crazybill]Take it in steps:
Make sure your speakers are powered on, and that it has a good and correct connection to your computer.

See if your sound card is working ok:

# **cat /usr/lib/openoffice/share/gallery/sounds/train.wav > /dev/dsp**

If you hear the sound of a train, you have no problem with your sound card or driver. 

Then you go to other steps with software setup.[/QUOTE]

Crazybill, thank you for your input.  Speakers are receiving power, the connections are good and correct, and the sound card seems to be working.  Executing the following command, I heard a train whistle.  What would be your next suggestion?

I do really appreciate the members input on this site.  I hope to be able to return the favor by contributing to this site as I become more familiar with Ubuntu.  :grin:

---

### Post by General_Tso on 2005-04-26
Update:  Looks like I'm going to call "mulligan" and reinstall Ubuntu.  I can't seem to figure it out.  To those of you reading this, be weary of the sound walk-through linked above.

---

