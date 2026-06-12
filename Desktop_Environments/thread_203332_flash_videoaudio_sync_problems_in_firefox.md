---
title: "flash video/audio sync problems in firefox"
date: 2006-06-25
forum: Desktop Environments
---

### Post by usr on 2006-06-25
anytime i try to play a flash video (like you'd find on youtube or google videos) in firefox, the audio and video are out of sync with the video being ahead of the audio.

downloading and playing videos of a variety of other formats work fine through various video players.  its just the flash videos from websites.

any help or suggestions appreciated.

---

### Post by hippy4life on 2006-06-25
you could have found this on the wiki

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by usr on 2006-06-25
thanks for the quick reply...

i have looked through that doc, however i do not see it address problems with audio and video being out of sync.  even so, before posting here i ran through the troubleshooting steps listed (installing alsa-oss, in /etc/firefox/firefoxrc - edit/add FIREFOX_DSP="aoss", in ~/.mozilla/firefox/rc - edit/add FIREFOX_DSP="none", and creating a symlink by issuing command: sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1).  these steps are listed as possible fixes for:

Flash videos stop playing after 1 second.
Firefox freezes when going to another page ater having tried to view a flash video.
The firefox process not correctly ending after having tried to view a flash video.

none of them had any effect - video and audio still work as before, but are out of sync.  

a little more info :
i get the same effect in konqueror - flash audio and video work but are out of sync

---

### Post by joelito on 2006-06-25
My simple explanation...

Lack of ALSA support in Macromedia's flash 7.

It will hopefully be fixed by the time flash 9 for linux is released.

---

