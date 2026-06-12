---
title: "ape monkey audio codec"
date: 2006-01-05
forum: General Help
---

### Post by cacharreo on 2006-01-05
Somebody knows how to play and/or convert ape monkey audio file format?
Could it be Totem?
Thanks!!!

---

### Post by sept00 on 2006-01-05
Try the instructions in this post: [http://ubuntuforums.org/showthread.php?t=18319#8](http://ubuntuforums.org/showthread.php?t=18319#8)

In more detail:
[LIST=1]
[*]Open a terminal window
[*]Type "wget http://rarewares.org/debian/packages/unstable/gstreamer0.8-monkeysaudio_0.8.0-1_i386.deb" (without the quotes, as always) and hit enter to get the needed package
[*]Type "sudo dpkg -i gstreamer0.8-monkeysaudio_0.8.0-1_i386.deb" and press enter to install it (you will be asked for the admin's password
[*]Type "gst-register-0.8" or "gst-register" and hit enter to register the new codec
[*]Type "rm gstreamer0.8-monkeysaudio_0.8.0-1_i386.deb" to get rid of the deb package (which you really don't need anymore)
[*]You're all set. Start your favorite GStreaming multimedia app and let 'er rip.
[/LIST]

Of course this all depends on an application that uses GStreamer to output audio (like amaroK, RhythmBox, or whatever). YMMV and I have no clue on what the legal status of that plugin is...

---

### Post by GabrielWolff on 2006-02-09
After doing all this I'm still unable to listen to .ape files. Not to talk about burning them.
Why?
G

---

### Post by ploosqva on 2006-05-18
Go to [http://sourceforge.net/projects/mac-portt]("http://sourceforge.net/projects/mac-port"). This is what I did. k3b won't burn the files anyway though but I can convert and play apes...

EDIT: and have you tried this: [http://ubuntuforums.org/showthread.php?t=160550&highlight=monkey+audio+codec]("http://ubuntuforums.org/showthread.php?t=160550&highlight=monkey+audio+codec")?

---

