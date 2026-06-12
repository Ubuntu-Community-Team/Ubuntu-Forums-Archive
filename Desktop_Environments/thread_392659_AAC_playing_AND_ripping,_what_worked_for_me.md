---
title: "AAC playing AND ripping, what worked for me"
date: 2007-03-24
forum: Desktop Environments
---

### Post by maestrobwh1 on 2007-03-24
I had the many issues with ripping and sound juicer. AAC files were a choppy mess. I had to rip to MP3 and then use wine with iTunes 6.05  to convert the files to aac and it was very cumbersome.  Ever run iTunes in wine?   slow slow slow

I had all the necessary items installed but sound-juicer just did not work well natively in Kubuntu with aac even with all of the correct things installed.  

I found this to be the most useful site in the world when it comes to multimedia
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
Do the very first shaded area.  I changed "apt-get" to "aptitude," as I just think it is a better thing to do. Make sure all of your repositories are enabled!  Aptitude does a better job finding and installing dependencies.

If that doesn't make aac play, then go to adept or synaptic and to a search for aac and installl anything that looks relevant that is not installed.  Most importantly make sure faac is installed.

Now for encoding/ripping:

I found this on the web:
[http://wiki.hydrogenaudio.org/index.php?title=Guide_aac_kaudiocreator]("http://wiki.hydrogenaudio.org/index.php?title=Guide_aac_kaudiocreator")
and I changed the 150 to 128 and the 21000 to 44100 to suit my needs.

So you will need kaudiocreator so use "aptitude install" in a shell or use adept or synaptic You can do this in regular ubuntu I assume, even though it is a kde app.  Follow the instructions given in the second url.

It works very well.

Peace,
Brian

---

