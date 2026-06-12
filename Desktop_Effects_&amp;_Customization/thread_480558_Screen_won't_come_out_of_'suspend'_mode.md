---
title: "Screen won't come out of 'suspend' mode"
date: 2007-06-21
forum: Desktop Effects &amp; Customization
---

### Post by ba5e on 2007-06-21
Hi I have a ATI X1950 Pro linked by DVI to a 1680x1050@75 monitor with no screensaver active and the fglrx drivers installed from this howto:

[http://wiki.cchtml.com/index.php/Ubu...lation_Guide#C](http://wiki.cchtml.com/index.php/Ubu...lation_Guide#C)

and Beryl installed by this howto:

[http://wiki.beryl-project.org/wiki/I...eisty_with_XGL](http://wiki.beryl-project.org/wiki/I...eisty_with_XGL)

Yes, all standard fare and it works like a dream however if I leave the pc alone and the monitor goes to suspend, then I wake it with a key press or mouse shake - I see the green light come on, then the monitor just goes straight back to standby again.

The only way to bring the screen back (CTRL ALT F1 etc does not work) is to do a CTRL ALT BACKSPACE. This reloads X and the screen reinitialises.

Is there any log anywhere that will help me troubleshoot this issue or does anyone have any good ideas as to what could be causing this?

---

### Post by il-luzhin on 2007-06-21
Got same prob when beryl is running.

---

### Post by ba5e on 2007-06-21
This happens to me when beryl or metacity are enabled.....however that is just from switching the actual window manager.....I will test with a fresh install of Ubuntu I think

---

### Post by ba5e on 2007-06-26
does anyone have an idea how to diagnose this issue?

---

### Post by linux4me on 2007-07-12
The debugging procedure for suspend is here:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

However, it sounds like your problem is more straightforward and related to your video. If Ctrl-Alt-Backspace is working, you are resuming, just not getting video output, I think.

Have you tried playing with the settings in  /etc/default/acpi-support?

It sounds like all you may need to do is change the following:
```

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

```

to:
```

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

```

Then restart X and see if you can suspend and resume with video. If not, there are a few more settings in there you can try to change and see if they do the trick.

Let us know what you find out.

---

### Post by il-luzhin on 2007-07-14
that seems to have got it.  
Thanks linux4me

---

### Post by linux4me on 2007-07-14
You're welcome. I'm glad you got it working.

---

### Post by ba5e on 2007-07-21
Hi Linux4me,

Thanks for the input....I just saw your reply and was so happy someone replied! I have stopped using Ubuntu because of this problem.....so annoying!

I tried what you suggested, and also messed around with some other settings in that file, namely the ATI method of suspending the screen, but none worked.

This is so annoying! are there any other config files you could reccommend I look at? In the mean time Im going to try Gutsy to see if I have any luck there.....

Look forward to your reply

---

### Post by linux4me on 2007-07-21
I am no expert, and don't know of any other file that would affect your video resuming from suspend unless perhaps it could be the video driver you have loaded.

There are, however, a couple of other settings you can try in the acpi-support file.

I would try setting:

> USE_DPMS=false

and if that doesn't work, you could try uncommenting:

> DOUBLE_CONSOLE_SWITCH=true

Those are both settings I have read about in the forums that work for some...

---

