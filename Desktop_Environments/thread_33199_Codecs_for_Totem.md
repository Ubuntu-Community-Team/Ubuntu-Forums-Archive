---
title: "Codecs for Totem?"
date: 2005-05-09
forum: Desktop Environments
---

### Post by garnertr on 2005-05-09
ok, so Totem is installed, but how do I get the required codes installed ??  I've got several AVI's and they don't work saying that the required codec wasn't installed, so, what would be a good way to get a fully working Totem?

v/r
Tom

---

### Post by vassalle on 2005-05-09
[QUOTE=garnertr]ok, so Totem is installed, but how do I get the required codes installed ??  I've got several AVI's and they don't work saying that the required codec wasn't installed, so, what would be a good way to get a fully working Totem?

v/r
Tom[/QUOTE]
 cant seem to remember on top of my head.. try to install xine, it plays most of my movie formats out there..

---

### Post by titus1950 on 2005-05-09
Take a look at "Ubuntu Guide"it will guide you trought the multimedia steps.
And Xine had worked better for me regarding DVD,DIVX,XVID,AVI,.. ETC,ETC....

---

### Post by Segovia on 2005-05-10
[QUOTE=garnertr]ok, so Totem is installed, but how do I get the required codes installed ??  I've got several AVI's and they don't work saying that the required codec wasn't installed, so, what would be a good way to get a fully working Totem?

v/r
Tom[/QUOTE]
"gstreamer0.8-plugins" (universe repository) is a metapackage for all the plugins.  You'll probably also want "gstreamer0.8-ffmpeg".

In my case, I find that playing Divx .avi's with gstreamer, the sound is often out of synch with the video.  "totem-xine", or "xine-ui" seems to do a better job, but in this case then I have no sound with .wmv's.

All these freaking proprietary formats are really getting under my skin...

---

