---
title: "Problem playing Mp3s with Amarok"
date: 2005-12-12
forum: General Help
---

### Post by Serenader on 2005-12-12
Hello,

I have Amarok and I really love the program. It plays some mp3 files fine. But, with some mp3 files, it has hiccups. I have no idea why this is happening. The same files play fine in Juk and XMMS. I have all the gstreamer plugins installed including the gst-mad plugin. Any help would be greatly appreciated.

Thanks.

---

### Post by anil_robo on 2005-12-12
I downloaded some podcasts with iTunes some time back. Those lie in my windows FAT partition, along with some other MP3 files. I load all the files  in the playlist, and begin to play. The regular MP3 files play well. But when Amarok tries to play a podcast downloaded with iTunes, it simply closes! No error message at all! The tray icon also  vanishes instantly! On manually restarting AMarok, I see the playlist hasn't been updated with the last item I played.  I'd like to know why!

---

### Post by Kyroku on 2005-12-12
I dunno if this will help you. But I had some problems playing mp3's with the gstreamer engine installed, so I installed the xine engine and that fixed everything and enabled me to play all my music.

---

### Post by steevc on 2005-12-12
Amarok was working fine for me until recently, but I may have done something to break it and it would not play most MP3 files any more. I saw in antoher thread about using the Xine engine, so installed that last night and it's working fine again.

I also seem to have lost sound in Flash sites. I've seen a thread about that and will investigate when I get home. My kids play a lot of Flash games.

I'm still hoping to get multiple sounds working one day.

---

### Post by Serenader on 2005-12-12
[QUOTE=Kyroku]I dunno if this will help you. But I had some problems playing mp3's with the gstreamer engine installed, so I installed the xine engine and that fixed everything and enabled me to play all my music.[/QUOTE]

Thanks a lot. The xine engine did the trick.

---

### Post by Sarisar on 2006-04-30
Been playing around with music programs all day it seems.  Amarok looks the best, however at first I got _no_ sound.  Turned out I didn't have the correct libraries installed for gstreamer.

So you might want to check that.  Was either gstreamer0.8-lame or gstreamer0.8-mad that let me listen to MP3s.

Now if I could just stop it crashing when I listen to a podcast I'd be sorted!

---

### Post by Harold P on 2006-04-30
[QUOTE=anil_robo]I downloaded some podcasts with iTunes some time back. Those lie in my windows FAT partition, along with some other MP3 files. I load all the files  in the playlist, and begin to play. The regular MP3 files play well. But when Amarok tries to play a podcast downloaded with iTunes, it simply closes! No error message at all! The tray icon also  vanishes instantly! On manually restarting AMarok, I see the playlist hasn't been updated with the last item I played.  I'd like to know why![/QUOTE]

The same exact thing happens to me!

---

### Post by Sarisar on 2006-04-30
OK sounds similar to a problem I've been having.  Basically some slightly iffy MP3s (for some reason) cause amarok to crash - and of course it doesn't save settings except on exit.

Try running amarok from a console (amarok will run it strangely enough) and see what your error is - mine was a glibc problem.

Hope that helps :)

---

