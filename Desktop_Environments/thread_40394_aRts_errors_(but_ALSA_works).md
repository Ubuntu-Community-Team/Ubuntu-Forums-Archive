---
title: "aRts errors (but ALSA works)"
date: 2005-06-08
forum: Desktop Environments
---

### Post by msoulchild on 2005-06-08
Hi there. I recently installed Kubuntu on my new AMD Athlon64 and I seem to be having issues with aRts.

After installing the 2.6.11-1-amd64-generic kernel I have managed to get my Tascam US-122 usb audio interface working fine with ALSA. In KDE, the startup sound and system sounds all work fine. The "Test Sound" button in the Control Center works. I am also able to use XMMS to output directly to ALSA.

Unfortunately, I run into problems when trying to play music in amaroK or JuK. artsd either segfaults or displays the following message:
```
Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = -1, can_write = 4096, errno = 77 (File descriptor in bad state)
This might be a sound hardware/driver specific problem (see aRts FAQ)
```

The only aRts FAQ I've found has been this one: [http://www.arts-project.org/doc/mcop-doc/artsd-faq.html](http://www.arts-project.org/doc/mcop-doc/artsd-faq.html) and it does not address my issues. Does anyone have any suggestions how to proceed? I'd much prefer to use JuK or amaroK over XMMS.

---

### Post by Ironi on 2005-06-09
I'm not sure how you'd fix artsd. As an alternative, you could use other output methods. amarok supports xine and gstreamer; apt-get install amarok-engines and select one in the Engines configuration. Juk (as shipped with KDE 3.4.1) can output to gstreamer and akode; Settings -> Output to...

---

