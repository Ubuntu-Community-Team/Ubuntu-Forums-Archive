---
title: "Help needed on using ImageMagick for watermarking an image using a Desktop Launcher"
date: 2009-01-27
forum: Desktop Environments
---

### Post by anyusername on 2009-01-27
I posted this question [HERE]("http://ubuntuforums.org/showthread.php?t=1050801") but on retrospect it may be more applicable in the Desktop Environment forum category as it's a Desktop Launcher question.

I found a post in the archive on how to make a Desktop Launcher for ImageMagick which allows an image to be dragged onto it to apply a watermark. The post is [HERE]("http://ubuntuforums.org/showthread.php?t=303962") and the command for the launcher is ```
mogrify -font /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf pointsize 22 -verbose -draw "gravity south fill black text 0,33 'www.ianmurphyphotography.com' fill white text 1,32 'www.ianmurphyphotography.com' " *.jpg
```

I'd like to use a Desktop Launcher to add a watermark image (stamp.png) rather than text. The code example I have is from [ImageMagick v6 Examples -- Annotating Images]("http://www.imagemagick.org/Usage/annotating/") page but it is not formatted for a Launcher. Is there a way to convert the code below so that it works in a similar way to the Desktop Launcher example above, e.g. upon dragging an image onto the Launcher, the stamp.png image is applied and the composition re-saved to the location of the original image? In addition, can it also append something to the filename so not to overwrite the original file?
```
  composite -gravity south -geometry +0+10 stamp.png  logo.jpg \
            wmark_text_stamped.jpg


```

Thanks in advance.

---

