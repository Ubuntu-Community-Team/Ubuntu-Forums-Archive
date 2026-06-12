---
title: "Colour Balance on Totem."
date: 2006-09-24
forum: Desktop Environments
---

### Post by pyro666 on 2006-09-24
Hello,

I made the changes as per help.ubuntu.com for playing all differnt types of media files. After doing so, the colour balance has completly gone out of wack and all my videos are high in brightness and contrast.

I liked how it was set before, but cannot return it to that previous state.

Can anyone assist?

Grant

---

### Post by wieman01 on 2006-09-25
I cannot help you with your problem but just to confirm that I am facing the same issue. Found out last night when watching a movie on my projector for the first time in months.

So I dropped Totem completely and use **Kaffeine** instead. Great player & excellent contrast & video quality. You may want to try Kaffeine instead (repositories).

---

### Post by Gio2k on 2006-09-25
Xine works fine. Funnily enough, if i start xine and keep it running and then open a video file on totem, color displays normal.

---

### Post by wieman01 on 2006-09-25
> **Gio2k said:**
> Xine works fine. Funnily enough, if i start xine and keep it running and then open a video file on totem, color displays normal.
Lol... Is that so? So I was right in dropping it after all. :-)

Xine is excellent too. True. Kaffeine is the more obvious choice for KDE users.

---

### Post by loko on 2006-11-30
i have the same problems with the colour when i watch a video using totem.

i can confirm that if i start xine, let it play a movie, and also start totem then the colours in totem are ok.

i use kaffeine because the colour-problem with totem is really bad kaffeine worked for a while but now i have the same problems with colour and kaffeine.

this is strange, does somebody know what to do?



EDIT: after opening and closing a video a few times, also xine does have this problem with colours. i think it is a problem with the video-driver, i have i810 and this seems to be causing the problems.

---

### Post by wieman01 on 2006-11-30
Same here... i810 on a Sony Vaio. Kaffeine is fine, however.

---

### Post by Mr Frosti on 2007-02-17
The problem seems to be related to the gstreamer packages. Totem has the ability to change which backend that it uses to render video and sound. I changed Totem from using gstreamer to using totem-xine and the color balance was fixed. 

To do this, in Synaptic install the following packages:

"totem-xine" -> accept when it tells you that "totem-gstreamer" will be removed.

Also, under Add/remove, there is a metapackage called Xine codecs that will install everything that you need for the Xine backend to decode video codecs. 

Hope this helps.

---

