---
title: "Xbox"
date: 2009-01-29
forum: General Help
---

### Post by nealien on 2009-01-29
not sure if this question has been asked yet, but if it hasn't id be surprised.  is there a way to get ubuntu to communicate with my xbox (i.e. stream music and video), or do i have to boot into windows every time??

---

### Post by rwstoner on 2009-01-29
This depends if your talking about an Xbox 360 or an original Xbox.  It also depends on if the Xbox has been setup to load homebrew software.  

I currently have my original Xbox (loaded with Xbox Media Center) connecting to my linux server at home.  Your Xbox and Ubuntu server would have to be on the same network in order for this to work.  Using samba you can create a shared drive on your Ubuntu server which allows the Xbox to see it.  The Xbox would read this share just like a Windows drive and allow you to stream your music, photos, and videos.

If your using an Xbox 360 you need to stream via Windows Media Player, Media Center, or a third party solution such as TVversity through Windows.  I have not seen any Linux to 360 implementations yet.

---

### Post by mozetti on 2009-01-29
There are multiple Linux->360 solutions: fuppes, ushare, and the one I use is Twonkymedia. Twonky costs money (about $30), but it's worth it because it offered the easiest solution with good organization.

---

### Post by mb_webguy on 2009-01-30
For an XBox 360, any UPnP server will work, and there are several available for Linux.  In addition to those mentioned by mozetti, I would suggest looking at MediaTomb.  It's extremely easy to set up and use.  I use MediaTomb to stream media to my PS3.

---

