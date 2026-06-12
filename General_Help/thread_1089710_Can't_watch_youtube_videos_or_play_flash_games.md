---
title: "Can't watch youtube videos or play flash games"
date: 2009-03-07
forum: General Help
---

### Post by roxter on 2009-03-07
Hello I am a new ubuntu user and i was wondering if anyone can help me. I seem to have a problem when i try to watch youtube only a few videos work. I start the video and BAM the window freezes and I am forced to force quit firefox, same thing happens when I try to play a game. I ran firefox in terminal and it seems that i am missing a decoder.
Here is what happens in terminal when I play a random video
unhandled event 19
Loading stream: [http://s.ytimg.com/yt/swf/watch-vfl81523.swf](http://s.ytimg.com/yt/swf/watch-vfl81523.swf)
Loading stream: [http://www.youtube.com/crossdomain.xml](http://www.youtube.com/crossdomain.xml)
Loading stream: [http://208.117.251.38/videoplayback?id=3778d6c88abef6cf&itag=34&ip=70.50.192.168&region=0&signature=D67DFA6B7DC1D12D245C1781302B4FB41C06AF80.803598D7A8EAAF0C98C3B60DE305AD9DA094BDDB&sver=2&expire=1236321823&key=yt1&ipbits=0&redirect_counter=1&tt=EC](http://208.117.251.38/videoplayback?id=3778d6c88abef6cf&itag=34&ip=70.50.192.168&region=0&signature=D67DFA6B7DC1D12D245C1781302B4FB41C06AF80.803598D7A8EAAF0C98C3B60DE305AD9DA094BDDB&sver=2&expire=1236321823&key=yt1&ipbits=0&redirect_counter=1&tt=EC)
SWFDEC: ERROR: swfdec_video_decoder.c(375): swfdec_video_decoder_errorv: error decoding video: no suitable decoder for video codec 7
SWFDEC: ERROR: swfdec_audio_decoder.c(201): swfdec_audio_decoder_errorv: error decoding audio: no suitable decoder for audio codec 10
Killed
I will post what happens when i run a flash game below this post but for now someone please help me with youtube.
I also noticed as soon as i go to youtube this appears
!!! [Hook] hook(): title not found
BTW Flash is Installed

---

### Post by Vadi on 2009-03-07
It looks like you've got swfdec installed, which isn't adobe's flash player and doesn't work as great.

So it's best to replace it with adobes. Go to System &#9656; Administration &#9656; Synaptic package manager, search for *swfdec* remove all installed swfdec stuff (right-click, remove package).

Then search for *flashplugin-nonfree*, and install that. Restart firefox and it should work fine

---

### Post by roxter on 2009-03-07
> **Vadi said:**
> It looks like you've got swfdec installed, which isn't adobe's flash player and doesn't work as great.

So it's best to replace it with adobes. Go to System &#9656; Administration &#9656; Synaptic package manager, search for *swfdec* remove all installed swfdec stuff (right-click, remove package).

Then search for *flashplugin-nonfree*, and install that. Restart firefox and it should work fine



ty so much ill try it right now

---

### Post by roxter on 2009-03-07
> **Vadi said:**
> It looks like you've got swfdec installed, which isn't adobe's flash player and doesn't work as great.

So it's best to replace it with adobes. Go to System &#9656; Administration &#9656; Synaptic package manager, search for *swfdec* remove all installed swfdec stuff (right-click, remove package).

Then search for *flashplugin-nonfree*, and install that. Restart firefox and it should work fine

Now when i go to youtube it tells me i don't have flash installed but i installed flashplugin-nonfree

---

### Post by roxter on 2009-03-07
> **Vadi said:**
> It looks like you've got swfdec installed, which isn't adobe's flash player and doesn't work as great.

So it's best to replace it with adobes. Go to System &#9656; Administration &#9656; Synaptic package manager, search for *swfdec* remove all installed swfdec stuff (right-click, remove package).

Then search for *flashplugin-nonfree*, and install that. Restart firefox and it should work fine

oh sorry man im stupid i had the addon disabled thanks everything works fine

---

### Post by Vadi on 2009-03-07
Glad you got it

---

