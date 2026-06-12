---
title: "XGL/Compiz Video Playback Issues"
date: 2006-06-20
forum: Desktop Environments
---

### Post by n0yd on 2006-06-20
Hi I had XGL/Compiz running great for a few weeks after following the guide in the compiz.net forums for ubuntu/nvidia/gnome. But last night after upgrading some packages from the repos which I used to install XGL/Compiz, video playback is very distorted or just doesn't work at all.  Totem the video is all distorted, mplayer doesnt show the video at all, xine does the same thing as totem also. I tried using mplayer with the vo=gl2 workaround but then where the video should it's just all white and you can only hear the sound.  Not sure if this affects all video extension types as the only ones I have available to try are .wmv's.  It was working fine after these updates though, if any has any ideas/suggestions/fixes, I'd greatly appreciate it. :)

BTW, I already asked over in the compiz.net forums, no one has replied yet so I figured I'd come over here and pick your brains :p .

Thanks,
n0yd

---

### Post by n0yd on 2006-06-20
Oh BTW, I tried VLC and get no video playback at all, just audio. :(


Help!

---

### Post by n0yd on 2006-06-20
Just a harmless bump. :)

Oh BTW, when I use the "-vo gl2" option, the video comes on but randomly blinks constantly, but if I use the enable the cube and start playing with it, while the cube is active the video plays fine, I'm confused! :mad: ](*,)

---

### Post by Anduu on 2006-06-21
I use "xv" output with mplayer in XGL/Compiz and it is slicker than snot.

If I try to use gl/gl2...look out nothing but trouble.

OpenGL anything and XGL don't get along.

---

### Post by n0yd on 2006-06-21
[QUOTE=Anduu]I use "xv" output with mplayer in XGL/Compiz and it is slicker than snot.

If I try to use gl/gl2...look out nothing but trouble.

OpenGL anything and XGL don't get along.[/QUOTE]

You mean use the "xv:pbuffer" for XGL?  I already have that set in my gdm.conf :-/. ](*,)

---

### Post by n0yd on 2006-06-21
Hmm I just tried mpeg and avi formats and they play fine in totem and mplayer, wonder if maybe it's a codec problem and not something to do with XGL/Compiz?

---

### Post by n0yd on 2006-06-21
Ok now this is really weird, AVI and MPEG play in Totem and any other player, but WMV only plays fine in Mplayer.  I'm frickin' confused! ](*,)

---

### Post by Anduu on 2006-06-22
[QUOTE=n0yd]You mean use the "xv:pbuffer" for XGL?  I already have that set in my gdm.conf :-/. ](*,)[/QUOTE]

I am referring to preferences in mplayer.

Right click the mplayer screen and select preferences.Under the video tab select "xv" 

Restart mplayer.

---

### Post by JNik on 2006-06-26
I had the same problem.

In totem wmv videos were distorted and in VLC I could only hear the sound. I installed mplayer and vmw files play as expected out of the box.

---

