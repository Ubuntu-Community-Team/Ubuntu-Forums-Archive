---
title: "Flash causes firefox to terminate!"
date: 2006-08-24
forum: Desktop Environments
---

### Post by StayPuft on 2006-08-24
When I view any page with Flash on it, Firefox immediately terminates without warning, errors, or log messages. I am running the newest versions of everything, this is a fresh install of Dapper Drake, flash, and mozilla FF. I am running AIGLX but I experience the problem whether I am in Metacity or AIGLX. I have installed flash from synaptic (flashplugin-nonfree), I have downloaded the zipped package directly from adobe's website and installed it that way, and I have tried isnstalling it using Automatix, none of which have changed anything for me. Please help! Thanks in advance.

---

### Post by Greycloak on 2006-08-24
I've had the same problem with a few flash sites.  My forum has a java based IRC chat, and I have no way to access it from Ubuntu/firefox.

---

### Post by StayPuft on 2006-08-25
Bump...

Please help! I can't get to any websites with flash! It's making it very hard for me to get my work done. Any suggestions would be greatly appreciated!

---

### Post by _profox on 2006-08-25
Yes. This is caused by AIGLX.
The solutions is to add 2 lines to the firefox script, like this:

**sudo gedit /usr/bin/firefox**

A text editor will open.

after the lines that read:
```
#
# Contributor(s):
#
```

insert these 2 lines:

```
XLIB_SKIP_ARGB_VISUALS=1
export XLIB_SKIP_ARGB_VISUALS
```

If you speak Dutch ;) you can read about the problem on my blog: [http://wesley.debianbox.be/2006/07/08/oplossing-flash-crasht-firefox-in-aiglx/](http://wesley.debianbox.be/2006/07/08/oplossing-flash-crasht-firefox-in-aiglx/)

---

### Post by StayPuft on 2006-08-25
Thank you!!! You are awesome! I am going to post this in the AIGLX thread, I cant believ it isn't in there already. I wonder why nobody else is complaining of this bug?

Anyway, thanks again for your help, it worked beautifully!

---

