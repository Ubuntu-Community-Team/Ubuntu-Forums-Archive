---
title: "HOW can i add the video clip in xscreen saver"
date: 2011-10-27
forum: Desktop Environments
---

### Post by jsg0363 on 2011-10-27
**HOW can i add the video clip in xscreen saver**


MFauzilkamil Zainuddin proposed the following answer:
To play MP4, MPEG, QuickTime, FLV and AVI videos:
      Install MPlayer 1.0 or newer, and add something like the following  to the `programs' preference in your .xscreensaver file:

           "My Movie"  mplayer -really-quiet -nosound -nolirc          \
                         -nostop-xscreensaver                          \
                         -wid $XSCREENSAVER_WINDOW                     \
                         -fs -loop 0                                   \
                         $HOME/movies/my_movie.mp4                   \n\

i don`t understand where i paste the line i cann`t find the  [COLOR=Red][U]`programs' preference in your 

.xscreensaver file:
 
[/U][/COLOR]

---

