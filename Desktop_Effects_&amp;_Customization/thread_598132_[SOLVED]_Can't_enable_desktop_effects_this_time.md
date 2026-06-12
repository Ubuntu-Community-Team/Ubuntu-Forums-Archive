---
title: "[SOLVED] Can't enable desktop effects this time"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by forestpixie on 2007-10-31
I originally was trying to get the menu buttons to speed up - which appears to be aproblem - I found this in a post

> #!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

which I used as a script to start with ubuntu - didn't work.

Then I found a thread which suggested changing the last line of /usr/bin/compiz to this

> ${COMPIZ_BIN_PATH}${COMPIZ_NAME} --only-current-screen $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

that didn't work either.

I deleted the script and changed the /usr/bin/compiz back - then desktop effects wouldn't enable.

Another thread suggested installing xserver-xgl, that meant I didn't have nvidia-settings so I removed that.

As it stands I have the restr drivers installed, got both screens working - but trying to change visual effects in appearance to anything other than none gets me 
> 
desktop effects cannot be enabled.

Anyone have any idea what I've done?

TIA

---

### Post by d'isperatu on 2007-10-31
Well, I don't know why, I couldn't enable the desktop effects in my Gutsy (upgraded from Faisty Fawn) and I couldn't enable any tipe of desktop effect (just the default - no effects). And the sistem gives a small error dat says something like the video card might not support the effects. But I think is IMPOSSIBLE! In Faisty Fawn the effects war enabled (easy, whit no errors)- the cube, window effects etc.,but here?!? I don't know what to say... If u buys can help me, please do it.
THX allot! ;)

---

### Post by forestpixie on 2007-10-31
was that an answer - or another thread stuck on the end :(

Edit

ok fixed it 

whether I needed to or not I'm not sure 

removed EVERYTHING nvidia related and compiz related, made sure it booted with no rest driver.

reinstalled compiz stuff then redid nvidia and all is well

---

