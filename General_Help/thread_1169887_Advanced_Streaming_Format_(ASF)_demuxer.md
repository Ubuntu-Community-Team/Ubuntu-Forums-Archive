---
title: "Advanced Streaming Format (ASF) demuxer"
date: 2009-05-25
forum: General Help
---

### Post by CLoss on 2009-05-25
i am a complete noob can any1 give complete clear instructions on how to get the required plug-in.
i know nothing so plese fdont presume i know stuff
and i am using the latest ubuntu.
thanks.

---

### Post by egyfalcon on 2009-11-15
thanks

---

### Post by 3rdalbum on 2009-11-15
Go to this page and run the big command there (under "Adding the Repository") to add the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

(you run commands in the terminal - Applications > Accessories > Terminal)

Now, in your Synaptic Package Manager, you will find a package called "non-free-codecs" (do a search for it). Right-click this and mark it for installation. It will tell you that it's pulling in some other packages as dependencies - click Ok. Now click the Apply button and OK. Now you'll have support for almost all audio and video formats that can be played on Ubuntu.

---

### Post by 6205 on 2009-11-15
You should install all necessary GStreamer plugins through Synaptic >

gstreamer-plugins-bad
-bad-multivers
-ugly
-ugly-multiverse
-ffmpeg
-pitfdll
-w32codec (available in medibuntu repository)

With these codecs is default Totem movie player able to play almost everything..

---

