---
title: "Write access to sound device?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by tribaal on 2006-06-02
Hi all!

I have installed quake3 on my fresh Ubuntu 6.06, and I cannot think or find a way to permanently grant a non root user Read and Write acces to /dev/dsp. By default this isn't the case, and so by default quake3 won't play any sound.

I used chmod a+rwx /dev/dsp , and it works, but it disappears after every reboot...

Is there a more elegant way? and perhaps some way to make it so that only me can write to it, not everyone... :)

Thanks a lot!

- trib'

---

### Post by asimon on 2006-06-02
The /dev/dsp has by default read and write permissions for the audio group. Thus adding your user to the audio group should solve the issue. The user you create during installation is automatically member of the audio group.

An other way is to define other permissions for /dev/dsp by creating some new rule in /etc/udev/rules.d/, for example something like
```

KERNEL=="dsp",  MODE="0640"
```
in /etc/udev/rules.d/01-dsp-permission.rules. But having hw devices world writable is usually no good idea. Go for the solution with the audio group.

---

### Post by tribaal on 2006-06-02
Thanks, adding my user to the audio group solved the problem completely.
And on top of that, I learned about udev rules, which I never heard about before. Although this does not have an immediate use for me now I'll just read some info about it... you know... just in case :)

Cheers

- trib'

---

