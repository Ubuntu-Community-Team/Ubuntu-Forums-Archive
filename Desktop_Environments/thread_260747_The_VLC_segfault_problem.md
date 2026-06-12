---
title: "The VLC segfault problem"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Dillius on 2006-09-19
Did anyone ever resolve this issue? I searched around a bit and found a number of people having this problem, with VLC segfaulting typically due to Matroska video files, but it doesn't seem like a solution was every found.

Someone mentioned that VLC wasn't being compiled with matroska support. Is there a line you can add in Synaptic to add that as a compile option? Or would you just have to do it manually?

---

### Post by whizbaby on 2006-09-19
Coz synaptic downloads binary (precompiled) packages for VLC you would have to get the source, read the instructions and compile it by yourself.

---

### Post by Dillius on 2006-09-19
Did that, which is what is annoying me right now. Compiled it specifically with --enable-mkv found in the /debian/rules file, (Which what bothers me is, it was in the source by default). Still segfaulting the same. Also, now, Totem can't play the matroska files even as messed up as it was prior.

---

### Post by distroman on 2006-09-19
This is not much help I guess.
I compiled vlc quit some time ago, so I can't be specific, but I am sure I didn't have matroska in mind. 
Because I really didn't have a clue about matroska format.
Just being curious, I did a google just now.
[http://www.matroska.org/samples/mewmew/index.html](http://www.matroska.org/samples/mewmew/index.html)
It plays fine here, vlc 0.8.4.

---

### Post by Dillius on 2006-09-19
I'm assuming it's matroska as that's the only format file to do this to me. I suppose it could be something else.

---

### Post by distroman on 2006-09-19
I think so,,,but not sure.
Maybe take a look at the codec needed?

---

### Post by Dillius on 2006-09-19
What do you mean by that? I know the files are .mkv's, but are you suggesting checking the files other codecs? I have tried two different files from two different encoders, and both have equally failed.

One thing I've noticed about the issue though, it doesn't seem to occur until I turn on the subtitles.

---

### Post by distroman on 2006-09-19
Well as I said, it was probably not much help. 
The only .mkv file I ever played, is the nutty cartoon I linked to. 
As I did not compile with the .mkv format in mind, I was just thinking, it might not be the issue.
Other then that, I am clueless.

---

### Post by Dillius on 2006-09-19
Anyone else have any problems like this? I can tell now that it's mostly subtitles... but I'm pretty clueless.

VLC will play audio and video, but if i load subtitles it seg faults
Mplayer: I have no idea how to make it do subtitles from a matroska file
Xine: Will not load the subtitles
Totem: Will not play the audio if i switch from the default, and won't do subtitles.

---

### Post by Dillius on 2006-09-19
Another wierd bit of information just from playing around with it a while, it only crashes if both subtitles are on and I try to resize the video at all.

What a specific, yet annoying, problem.

---

