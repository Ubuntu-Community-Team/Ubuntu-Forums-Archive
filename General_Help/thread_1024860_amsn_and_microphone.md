---
title: "amsn and microphone"
date: 2008-12-29
forum: General Help
---

### Post by akimorita on 2008-12-29
I've been trying to get the microphone on my eeepc 900 working with msn.  I finally got it working and thought I'd share my steps.

Note:  This is for 8.04 and it should work for other ubuntu versions

The main problem from searching on the internet is that the snack library that amsn uses for audio is not compiled with alsa support enabled.  So, we need to rebuild the snack library.

Download the source for the snack library here (click on "Source release for all platforms", the latest as of this writing was 2.2.10): 

[http://www.speech.kth.se/snack/download.html](http://www.speech.kth.se/snack/download.html)

unpack the file

> tar xzf snack2.2.10.tar.gz

> cd snack2.2.10/unix

Now, there are several other things that need to be installed to make sure we can compile and link snack.

> sudo apt-get install tcl8.5-dev tk8.5-dev alsa-source libasound2-dev libxss-dev

I'm not 100% sure alsa-source is necessary.  You may be able to leave it out.

Now, configure snack:

> ./configure --with-tk=/usr/share/tcltk/tk8.5 --with-tcl=/usr/share/tcltk/tcl8.5 --enable-alsa

Now, build snack:

> make

Install the libraries

> sudo make install

The problem here is that it installs the libraries to the wrong place.  So, we overwrite the old version with the new version

> sudo mv /lib/snack2.2/* /usr/lib/tcltk/snack2.2/

Note that this moving may be unnecessary if you set the correct prefix when doing the configure.  I haven't bothered to see if this could be properly set.

That should do it for rebuilding the snack library.  The other thing to configure is to make sure the microphone is not muted in the volume control and you may need to fiddle with the microphone boost.  Also, if the system detects more than one microphone, you may need to change the "Input Source" in the "Options" tab of the volume control.  You may need to enable these other microphones in the volume control preferences.

Hope this helps save someone some headaches.

---

