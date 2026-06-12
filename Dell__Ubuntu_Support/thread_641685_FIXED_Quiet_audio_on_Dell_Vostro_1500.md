---
title: "FIXED Quiet audio on Dell Vostro 1500"
date: 2007-12-15
forum: Dell  Ubuntu Support
---

### Post by dyssident on 2007-12-15
First off, if your sound isn't working, use the fix described [[COLOR="Blue"]in this thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3872487&postcount=3"). Worked perfectly for me although others have had problems. If this fix doesn't work for you, there is a threads for people with problems [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=569082") and [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=627945").

To fix your quiet audio:

1. Install the alsamixergui package with Synaptic or `sudo apt-get install alsamixergui`
2. Open Applications > Sound and Video > Alsamixergui
3. Jack the PCM levels all the way up. This apparently resets the maximum volume.
4. Close Alsamixergui and turn sound back down to a reasonable level with the hardware buttons or the task bar volume control widget

---

