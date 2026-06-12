---
title: "VoIP, IM experiences."
date: 2006-06-05
forum: Desktop Environments
---

### Post by paulyche on 2006-06-05
I'm running Dapper and at the other end of the country (UK By the way) my parents are now also running Dapper. They're not at all technically literate and love their new fast computer with no popups. 

My mother wants to phone me and my windows siblings over the net. We used the skype client for a bit, but it's frankly awful with oss sound and having to restart after each call and if amarok is playing when it rings.

So I want another solution. This solution has to be _very_ easy at their end. The ekiga client is too complex, I would much rather something like tapioca in terms of user simplicity. We all have gmail addresses after all. Thing is tapioca seems to be missing quite important things like minimizing to the panel and saving passwords.

Is anyone in a similar situation? Net to landline calls aren't necessary and a packaged solution in a repo is much preferred. wengophone doesn't seem to want to work, and I'd really like a simple apt-get kind of answer to this

Of course I'm prob asking a lot... ;-) Anyway, recommendations from experience?

---

### Post by biquillo on 2006-06-05
did you try [http://www.gizmoproject.com/]("http://www.gizmoproject.com/") and [http://www.openwengo.org]("http://www.openwengo.org")? Both are opensource and are SIP compilant :) you can use ekiga from your ubuntu box and your family can use any of those windows/linux clients :)

I hope this work for you, and sorry for my english!! :D

---

### Post by paulyche on 2006-06-05
I tried wengo but the sound setup didn't work at first. Haven't spent a lot of time on it though. 

I'll try gizmo. According to wikipedia gizmo is actually closed-source, but open standards are still good.

---

### Post by paulyche on 2006-06-05
Gizmo seemed to install fine (Gizmo Project v1.0.0.18 ), however after putting in my new gizmo username/password it crashes with this gem

```


(gizmo:5119): GdkPixbuf-CRITICAL **: gdk_pixbuf_animation_iter_advance: assertion `GDK_IS_PIXBUF_ANIMATION_ITER (iter)' failed

(gizmo:5119): GdkPixbuf-CRITICAL **: gdk_pixbuf_animation_iter_get_delay_time: assertion `GDK_IS_PIXBUF_ANIMATION_ITER (iter)' failed
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
gizmo: pcm.c:663: snd_pcm_close: Assertion `pcm' failed.
Aborted

```

Which looks like more linux sound worries. I'm going to bed I'll try to deal with this in the morning...

Thanks for the advice biquillo,

---

### Post by biquillo on 2006-06-05
the best thing for those VoIP apps is that both works with SIP, thats mean you can call from any application that supports SIP to Gizmo or Wengo, so lets imagine that you use Ekiga in your computer, your parents use OpenWengo in their ubuntu box and your brother/sister use Gizmo on Windows :) 

the key is that the SIP protocol is a standard and you can communicate with anyone who uses any SIP client (skype is not a SIP client). I'm also having troubles with skype, so I'll move all my family to anything that works for me.

---

### Post by rado_london on 2006-06-05
I think linux sucks with video and audio communication programs. Skype is hell for me as I have webcam. Wengo doesnt start. Gizmo doesnt recognise me webcam. Ekiga IMO shouldnt be included by default. I think we should make our all audio/IM/video/everything app that will serve all gaim/ekiga etc. Just a thought.

---

