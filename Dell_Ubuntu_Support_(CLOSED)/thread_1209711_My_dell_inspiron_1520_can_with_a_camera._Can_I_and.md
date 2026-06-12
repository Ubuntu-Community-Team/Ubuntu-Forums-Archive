---
title: "My dell inspiron 1520 can with a camera. Can I and how do I use it?"
date: 2009-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mrsticky005 on 2009-07-10
Can anyone help me figure out how to use the (built-in) camera that came with my Dell Inspiron 1520?
Also I would like help figuring out how to get my DVD player (also built in) to actually play DVDS
and how do I get my built-in audio recorder to work
Also anyone know how to get Halo CE (Custom Edition) to work on Ubuntu if at all?


contact me at [EMAIL="mrsticky005@yahoo.com"]mrsticky005@yahoo.com[/EMAIL]

---

### Post by ajgreeny on 2009-07-10
> **mrsticky005 said:**
> Can anyone help me figure out how to use the (built-in) camera that came with my Dell Inspiron 1520?
Also I would like help figuring out how to get my DVD player (also built in) to actually play DVDS
and how do I get my built-in audio recorder to work
Also anyone know how to get Halo CE (Custom Edition) to work on Ubuntu if at all?


contact me at [EMAIL="mrsticky005@yahoo.com"]mrsticky005@yahoo.com[/EMAIL]
Can't help with No 1, it will depend on the camera installed in the machine.  Find out what it is from ```
sudo lshw
``` in terminal, if you don't know.

For DVD playback of most commercial DVDs you need to install libdvdcss2 from [medibuntu]("https://help.ubuntu.com/community/Medibuntu").  I also suggest you install VLC, mplayer or smplayer for the playback, all much better than totem in my opinion.

What do you mean by the "built in audio recorder"?  If you are talking about sound-recorder in the sound and video menu, it should work as long as your microphone works, or you have the mixer settings set to capture the source you're trying to record.  Tell us more and we'll try to help.

No idea about Halo CE, or even what it is, so can't help

---

### Post by avacado on 2009-12-29
Finally something I know.
Instal an application called cheese using the package manager.
takes photos and short video.
quickest way to test whether it is working.

---

