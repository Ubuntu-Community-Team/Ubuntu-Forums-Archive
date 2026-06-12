---
title: "TV-out: no image while playing video"
date: 2006-02-14
forum: Desktop Environments
---

### Post by choizy on 2006-02-14
I just installed ubuntu on a HP 8320. Everything whent fine except drivers for the graphic card(ati radeon mobility X600). So I installed fglrx and after restarting X i got picutre at my LCD screen and TV. but **when i play movies i only see the movie on my LCD screen**. Its only a black window on the TV. Annyone know howto fix it?

---

### Post by queenorych on 2006-02-15
I've seen the same issue in windows.  PLay with you default video output.  I think its under preferences/mulimedia video tab.  Ideally select x11

or try
mplayer yourfile.mpg -vo x11 

Try to see if there is an ati guide out there to help you.

---

### Post by paulbarbee on 2006-02-15
This happened to me also. It was because of the video overlay I believe. I found  one solution in the forums here [http://ubuntuforums.org/showthread.php?t=75378]("http://ubuntuforums.org/showthread.php?t=75378")was to run this:
*sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver.*

Hope that helps.

---

