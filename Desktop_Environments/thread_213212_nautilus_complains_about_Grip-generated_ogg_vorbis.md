---
title: "nautilus complains about Grip-generated ogg vorbis files"
date: 2006-07-11
forum: Desktop Environments
---

### Post by matthewn on 2006-07-11
Here's a weird one. If I rip a CD with Sound Juicer, Nautilus plays nice with the files produced. If I open such a file's Properties, Nautilus reports "Type: Ogg Vorbis audio" and "MIME type: audio/x-vorbis+ogg".

BUT, if I rip the same CD with Grip (set to use oggenc), Nautilus won't let me double-click the file to play it, complaining that the extension, ogg, doesn't match the file's MIME type. And sure enough, if I open the file's properties, I see "Type: MP3 audio" and "audio/mpeg". But XMMS and Totem both confirm that the file is actually an ogg vorbis file, which is no surprise, since that's all oggenc can make.

I've been using Grip-with-oggenc for years and have never had this problem before. Suddenly, oggenc produces files that Nautilus doesn't understand. What happened? Is oggenc or Nautilus at fault? How do I go about troubleshooting this?

---

