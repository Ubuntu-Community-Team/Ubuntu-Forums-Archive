---
title: "Can I play WMA files on Listen?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Txukie on 2006-09-14
Hi,

I'm currently using Xubuntu Dapper and have installed Listen unstable (5beta). The program works fine, a lot better than previous versions. However i can't play any WMA files although i have every gstreamer codec (version 0.10) i can find in the repos. Has anyone succeeded at this?

---

### Post by dannystaple on 2006-09-14
First, can you play them in Totem or MPlayer? AFAIK WMA codecs are in the restricted section of the repos, so you may not have them installed yet.

Check those in your package manager, by searching for "windows media". You may need to add new repo sources.

---

### Post by Txukie on 2006-09-14
I can play them in xfmedia, but that uses xine and listen uses gstreamer.I can play them well using totem-gstreamer too.

---

### Post by Txukie on 2006-09-14
*bumP*

---

### Post by Txukie on 2006-09-15
*bump*

---

### Post by Txukie on 2006-09-21
*bump*

---

### Post by skymt on 2006-09-21
Try the directions [here](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5), then make sure gstreamer0.10-pitfdll is installed.

---

