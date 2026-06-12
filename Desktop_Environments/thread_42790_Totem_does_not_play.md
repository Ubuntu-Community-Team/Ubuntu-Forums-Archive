---
title: "Totem does not play"
date: 2005-06-19
forum: Desktop Environments
---

### Post by Ubuntu_learner on 2005-06-19
Hi
Just installed Ubuntu 5.04, tried playing VCD and DVD movies using Totem but it didn't work (it prompts me for some codecs/decoders?). Please advise. Thanks. :)

---

### Post by thagame on 2005-06-19
i had the same prob. so i went in synaptic and installed totem-xine (it removes totem-gstreamer) but everything plays now.

---

### Post by Ninwa on 2005-06-19
I also had similar problems and instead I installed mplayer which has run excellent for me. Either way, good luck!

---

### Post by gil-galad on 2005-06-19
You probably need libdvdcss2.

---

### Post by afonic on 2005-06-19
More posts like this in these forums could have been avoided if there was a big banner:

READ THIS BEFORE POSTING: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by kxs on 2005-06-25
I`ve followed instructions in ubuntuguide and installed libdvdcss2 but Totem still doesn`t play DVDs. It freezes on first second and after a while it gives such error:
"Internal GStreamer error: negotiation problem.  File a bug."

---

### Post by John Jason Jordan on 2005-06-25
[QUOTE=thagame]i had the same prob. so i went in synaptic and installed totem-xine (it removes totem-gstreamer) but everything plays now.[/QUOTE]

OK, I just did the same thing. After it was done I put a movie DVD that I bought at a video store into the DVD drive. Totem popped up and immediately disappeared. 

Before Totem would pop up and then display a message that it could not play the media. Now it just goes away. :(

---

### Post by Dave_is_sexy on 2005-06-25
agreed. can't play anything in totem except mpegs

---

### Post by afonic on 2005-06-26
[QUOTE=Dave_is_sexy]agreed. can't play anything in totem except mpegs[/QUOTE]
 My Totem plays *everything*, including DVDs, XviD, MPEG, VCDs, WMV and more.

What I did was to remove totem-gstreamer and install totem-xine and then installed all the codecs they say to get from ubuntuguide.org.

Do other players (ex. VLC) work?

---

### Post by venkman on 2005-06-26
i've got the same problem with totem - it doesn't work and I just get the message that it can't play the file. VLC works fine :)

---

### Post by kxs on 2005-06-26
[QUOTE=kxs]I`ve followed instructions in ubuntuguide and installed libdvdcss2 but Totem still doesn`t play DVDs. It freezes on first second and after a while it gives such error:
"Internal GStreamer error: negotiation problem.  File a bug."[/QUOTE]

it`s all OK now after moving to totem-xine

---

### Post by ekravche on 2005-10-17
[QUOTE=afonic]My Totem plays *everything*, including DVDs, XviD, MPEG, VCDs, WMV and more.

What I did was to remove totem-gstreamer and install totem-xine and then installed all the codecs they say to get from ubuntuguide.org.

Do other players (ex. VLC) work?[/QUOTE]

With all the codecs this seems like the best solution. Works great for me!

Thanx!

---

