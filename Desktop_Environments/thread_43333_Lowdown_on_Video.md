---
title: "Lowdown on Video"
date: 2005-06-21
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-21
I'm struggling to get my head around linux video, so I thought I'd post what I know about video and see how this compares with my new environment.

Normally, I'd play back video using directshow. This was good because libacodec (in ffdshow) could play almost anything in directshow without luttering the system.

Encoding would use exclusively VFW stuff. So to transcode a format, I would make sure the full appropriate codec was installed and we'd be away. 

Above the codecs were filters to be able to see inside containers and decode the component streams. 

Some video players would refer to the VFW and/or directshow codecs. But some would have their own internal codecs and run independantly of the system-wide installs. 

So how does linux do things?  :smile:

---

