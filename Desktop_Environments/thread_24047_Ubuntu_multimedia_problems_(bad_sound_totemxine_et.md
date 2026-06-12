---
title: "Ubuntu multimedia problems (bad sound totem/xine etc..)"
date: 2005-04-05
forum: Desktop Environments
---

### Post by ubuntulnx on 2005-04-05
i have been unsuccesful with the integration of multimedia in ubuntu. reading through the forums and howto's led me to:

*install the w32codecs
*install the mplayer codec package (moved the codecs to the .gnome2.../totem add on directory)
*installed totem-xine

i can now watch video (avi,mpg etc), but some of them have an awfull choppy sound, video is ok. 

i am using warty. i know the files and my system are ok as I can see/listen to them perfectly when i start my system with a knoppix cd (and using xine).

are there some problems with the codecs that cause this? are there any sollutions for this? how do i know what codecs are being used?

thanks a lot for your help.

i've seen many problems with this. i'll try to mold the answers in a wiki entry.

---

### Post by ubuntulnx on 2005-04-07
reply to myself.. 8-)

i have found the problem to be the codecs. i have copied the codecs from an old knoppix 3.3 cd over /usr/lib/win32 and the problem was solved. 

i had followed the exact instructions from the unofficial ubuntu guide to install the win32 codecs.

both totem-xine and gxine work now. what i see is ico big files totem-xine and gxine read/index the complete file before beginning. this gives the impression that the app. is hanging. the xine in knoppix does not seem to do this, and reads on while you start playing the file.

in general, it seems that multimedia (also) is pretty well implemented in knoppix. should be even better now in 3.7.

well. struggling on untill hoary, we'll see what new it brings in the multimedia arena. if it remains the same, we'll look at a better/more prepared debian desktop implementation. fortunately open source means options. and in the process we always learn something!

---

### Post by ubuntulnx on 2005-04-24
another update to my question.

upgraded to hoary this weekend. looks great. nothing changed in the sound department though. 

thing is, if i play a mp3 in totem-xine.. the sound is very choppy, if i play it in Rhythmbox 0.8.8 the sound is good. sound in totem-xine for videos continues to be choppy in some cases for me.

i really have not figured this out completely.

also, totem-xine continues to refuse to play some files. it starts and exits. i can see all of them with knoppix 3.3. ubuntu does show a snippet of the file in the file explorer.

anyone had the same problem and came up with a sollution?

---

### Post by ubuntulnx on 2005-04-24
just saw this thread.. seems i'm not the only one.. hope we can get this solved..

[http://ubuntuforums.org/showthread.php?t=24012&page=2&pp=10&highlight=choppy+sound+xine](http://ubuntuforums.org/showthread.php?t=24012&page=2&pp=10&highlight=choppy+sound+xine)

---

### Post by ubuntulnx on 2005-05-06
to make sound work in warty i found a suggestion on the ubuntu forums that worked for me in warty. it now seems that the choppy sound in hoary was due to this file. 

i tried other suggestions, (ubuntu unofficial ubuntu guide, [http://ubuntuforums.org/showthread.php?t=26567&highlight=choppy+sound](http://ubuntuforums.org/showthread.php?t=26567&highlight=choppy+sound) ), but unfortunately, none worked for me.

after deleting .asoundrc from my home directory, the choppy sound in totem disappeared. i have not made any other changes than that. the contents of the file was:
pcm.asymed {
        type asym
        playback.pcm "dmix"
        capture.pcm "dsnoop"
}
pcm.!default {
        type plug
        slave.pcm "asymed"
}

if anyone knows why this resulted in a success, please explain and let us know. 

by now, im happy...  \\:D/

---

### Post by ashokmani on 2005-05-06
can anyone give me the link to download win32codecs pls ? 

i am having troucle finding them.



Thanks.

---

### Post by Bob D. on 2005-05-06
You need to add the Backports repositories to your sources.list.

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

See the UbuntuGuide for more detailed instructions on adding repositories:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

Bob

---

