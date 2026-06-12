---
title: "Suddenly getting errors running skype"
date: 2009-03-12
forum: General Help
---

### Post by dflock on 2009-03-12
I'm using Ubuntu 8.10 AMD64 and have had Skype setup and running fine for ages; I'm using the latest mediabuntu version of skype. However, I start skype yesterday and the window opens, it logs in and then - just before it would play the login sound - it vanishes.

Running Skype from the terminal does the same and generates this output:

```
/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference
```

I'm guessing that this is a library version conflict somewhere, between skype and the installed version of libasound?

This is part of the output of doing 'aptitude show skype':

```
Depends: ia32-libs (>= 1.6), lib32asound2 (> 1.0.17), lib32gcc1 (>= 1:4.1.1), lib32stdc++6 (>= 4.1.1), libc6-i386 (>= 2.3.2), skype-common (= 2.0.0.72-0medibuntu4), dbus-x11 (>= 1.0.0), lib32nss-mdns, lib32v4l-0
```

The version of libasound that comes with ubuntu is 1.0.17a and the one that I've currently got is 1.0.19 - this version came with something from a PPA, according to synaptic.

Can anyone shed any light on this, or how to fix it? How do I find out which package installed the updated version of libasound, if that's the problem. If that's not the problem, any idea what is?

Thanks,
Dunc

---

### Post by rebegin on 2009-03-19
i get the same error.
found some info here:
[http://ubuntuforums.org/showpost.php?p=6642423&postcount=522](http://ubuntuforums.org/showpost.php?p=6642423&postcount=522)
in the previous post it mentions the same error but i didn't find the solution yet. i don't know what the alsa-lib package should be, as i don't that one...

---

### Post by pottedmeat123 on 2009-04-13
I'm having the same exact error described after upgrading to Jaunty. Any luck finding an answer?

---

### Post by dflock on 2009-04-13
Unfortunately not, no.

---

