---
title: "MPEG/MP3 Illegal?"
date: 2005-03-15
forum: Desktop Environments
---

### Post by dsginter on 2005-03-15
Why don't most media types play out of the box?

I am led to believe that there is a licensing issue, no?  Am I in violation of this licensing issue if I enable this sort of playback?  How do I go about doing this legally?

---

### Post by iomicifikko on 2005-03-15
if u are talking about errors playing mp3 with totem, that is a know "bug". i solved it according to the imput by someone i dont remember where in the forum telling me to uninstall the totem version based on gstreamer and install the totem version based on xine (just select to install the "totem-xine" pack and synaptic will do everything). for the video codecs with copyright just install them always using synaptic, i dont remember exactly the packs anyway "w32codecs" for sure and maybe others

byez

---

### Post by gylf on 2005-03-15
The short answer is no, its not illegal to use.
Please do some research before posting a question as this has been answered in many other posts.  Here are 3 popular ones.  With a bit of searching you can find even more:

[here](http://ubuntuforums.org/showthread.php?t=7585&highlight=mp3+license) 
and
[here](http://ubuntuforums.org/showthread.php?t=8266&highlight=mp3+license) 
and
[wiki](http://www.ubuntulinux.org/wiki/RestrictedFormats)

---

### Post by dsginter on 2005-03-15
[QUOTE=gylf]The short answer is no, its not illegal to use.
Please do some research before posting a question as this has been answered in many other posts.[/QUOTE]

I did and found jack.

OK - after reading about the licensing issues, my suggestion is to have the default web browser open to a page where these packages can be installed immediately upon finalizing installation.  At first, I thought that the Synaptic package manager would make it easy but I've installed many of the cryptic packages in there to no avail.  So then I tried to install different media players at the recommendation of what came from a google search.  Now I've got .rpm, .tar.gz, .bin and .deb files scattered all over (Firefox tells me that they are downloading to 'desktop' but they don't appear there).

Finally, the totoem player could have a better error message as "you might need to install the default plugins" put me on the wrong course.  A google search for totem plugins yeilds nothing.

Quite the frustrating experience that could be avoided by simply sticking a HOWTO on the desktop of the default install.

---

### Post by dsginter on 2005-03-15
As a matter of fact, after reading about all these licensing issues, I'd like to suggest that the error message on totem point to one of these available FAQs on the matter.

---

### Post by mike998 on 2005-03-15
Try going to [http://ubuntuguide.org](http://ubuntuguide.org)
There is a fabulous how-to on how to get mp3 and mpeg up and running.  There is no need to download .tgz .rpm .deb files - just follow the how-to.
Also, your desktop not showing files - you may want to try navigating to your desktop (go Home > Desktop) and clicking refresh in Nautilus.

I too am frustrated by the inability of Ubuntu to play these files out of the box, but with the guide mentioned above, it's a trivial issue.  XMMS is a great program for .mp3 and Xine-ui is great for all video.  (If you installed the win32codecs file.)

Good Luck!

---

### Post by dsginter on 2005-03-15
[QUOTE=mike998]Try going to [http://ubuntuguide.org](http://ubuntuguide.org)
There is a fabulous how-to on how to get mp3 and mpeg up and running.[/QUOTE]
 
Thanks for that link.  This should be a standard fixture on the desktop of new Ubuntu installs.

My problem was that a friend passed me a CD and asked me to give it a shot.  When I got the error message from Totem, I made the mistake of trying to locate info on resolving the error specific to Totem rather than some fundamental licensing issue with free software - I had no idea.

If I had just substituted 'ubuntu' for 'totem' on my google search, this post would not be here.

---

### Post by mike998 on 2005-03-15
[QUOTE=dsginter]Thanks for that link.  This should be a standard fixture on the desktop of new Ubuntu installs.
[/QUOTE]
Download a copy of that page and keep it handy just in case you do a re-install.  I have a copy backed up on a file server so I can get everything up and running without even having to go to the site.

---

