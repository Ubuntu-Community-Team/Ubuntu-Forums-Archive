---
title: "Ubuntu Fonts - Turning off smoothing?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by jpdoane on 2006-06-06
I'm trying to improve the look of the fonts in Ubuntu - Particularly in firefox, where I have a direct comparison to my windows machine, and windows looks so much better.  The problem is that if I have smoothing on, the fonts loose their sharpness and become too soft and blurry (to my eyes).  However if I turn off smoothing, Ubuntu can't seem to render them cleanly.  They end up looking ragged and pixelated.  Here are 3 screenshots - all using Arial (but the effect is similar regardless of the font):

Windows:
[http://i78.photobucket.com/albums/j118/jpdoane/windowsFonts.jpg](http://i78.photobucket.com/albums/j118/jpdoane/windowsFonts.jpg)

Ubuntu with smoothing:
[http://i78.photobucket.com/albums/j118/jpdoane/SmoothedFonts.jpg](http://i78.photobucket.com/albums/j118/jpdoane/SmoothedFonts.jpg)

Ubuntu w/o smoothing:
[http://i78.photobucket.com/albums/j118/jpdoane/crappyFonts.jpg](http://i78.photobucket.com/albums/j118/jpdoane/crappyFonts.jpg)

Please help - what am I missing here?  I tried a bunch of various font patchs I found, but none seemed to help.  Perhaps I messed something up in the process.  Any suggestions?

---

### Post by jazzmuzik on 2006-06-07
See if one of the options at the bottom of System, Preferences, Font, Font Rendering look any better.

---

### Post by jpdoane on 2006-06-07
[QUOTE=jazzmuzik]See if one of the options at the bottom of System, Preferences, Font, Font Rendering look any better.[/QUOTE]


No, none of them are any better.

---

### Post by johnc4510 on 2006-06-07
I just posted this earlier today:
[http://www.ubuntuforums.org/showthread.php?t=190862](http://www.ubuntuforums.org/showthread.php?t=190862)
Here is a screenshot

---

### Post by Rondonjin on 2006-06-07
[QUOTE=jpdoane]I'm trying to improve the look of the fonts in Ubuntu - Particularly in firefox, where I have a direct comparison to my windows machine, and windows looks so much better.  The problem is that if I have smoothing on, the fonts loose their sharpness and become too soft and blurry (to my eyes).  However if I turn off smoothing, Ubuntu can't seem to render them cleanly.  They end up looking ragged and pixelated.  Here are 3 screenshots - all using Arial (but the effect is similar regardless of the font):

Windows:
[http://i78.photobucket.com/albums/j118/jpdoane/windowsFonts.jpg](http://i78.photobucket.com/albums/j118/jpdoane/windowsFonts.jpg)

Ubuntu with smoothing:
[http://i78.photobucket.com/albums/j118/jpdoane/SmoothedFonts.jpg](http://i78.photobucket.com/albums/j118/jpdoane/SmoothedFonts.jpg)

Ubuntu w/o smoothing:
[http://i78.photobucket.com/albums/j118/jpdoane/crappyFonts.jpg](http://i78.photobucket.com/albums/j118/jpdoane/crappyFonts.jpg)

Please help - what am I missing here?  I tried a bunch of various font patchs I found, but none seemed to help.  Perhaps I messed something up in the process.  Any suggestions?[/QUOTE]

Have you followed the HOWTO on improving font rendering? I'd read the whole thread before doing it.

[http://www.ubuntuforums.org/showthread.php?t=180647](http://www.ubuntuforums.org/showthread.php?t=180647)

Wayne

---

### Post by jpdoane on 2006-06-07
Yeah, I went through all that.  Actually, when I got rid of the patches that the HOWTO suggested and reverted to the default dapper font engine, things were a lot better.  I can display unsmoothed fonts that look decent (still not as good as windows), however bigger fonts look pretty bad, so I had to turn smoothing back on.  I suppose its the best I can do.

Thanks for helping!!
-Jon

---

### Post by donar73 on 2006-06-07
Try [this](http://www.ubuntuforums.org/showthread.php?t=20976) guide, it will make your fonts look like the fonts in Windows without Cleartype (non-antialiased). It was written for Hoary originally, but it still works for Dapper.

---

### Post by Half-Left on 2006-06-07
I think you should be using a font like Bitstream Vera Sans or DejaVu Sans, maybe it's because I use 1280x1024.

---

