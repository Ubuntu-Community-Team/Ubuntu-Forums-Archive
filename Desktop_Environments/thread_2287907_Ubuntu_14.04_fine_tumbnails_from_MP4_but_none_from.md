---
title: "Ubuntu 14.04: fine tumbnails from MP4 but none from MPG. Help, please!"
date: 2015-07-23
forum: Desktop Environments
---

### Post by siggi2 on 2015-07-23
Hi,

before anyone suggests I should search the forums or google... I did extensively, e.g., [http://askubuntu.com/questions/313489/how-to-make-videos-show-thumbnail-in-ubuntu-13-04]("http://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus"), [http://askubuntu.com/questions/507411/nautilus-thumbnails-dont-appear-in-14-04]("http://askubuntu.com/questions/507411/nautilus-thumbnails-dont-appear-in-14-04"), [http://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus]("http://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus"), etc. To no avail :-(

_Problem_: I have hundreds of videoclips in MPG-format and I keep getting new ones from my digital camera. 

They play beautifully with VLC or Totem or WinFF (Ubuntu 14.04.2 Unity), but, try as I might, I don't get any thumbnails!

I do get thumbnails with MP4 from my mobile, or with MP4 converted with WinFF from the "bad" MPGs. So, I have two questions:

* 1 * How can I see which "strange" format my MPG-files have?

* 2 * And then, how could I have thumbnails from these "bad" files?

Thank you,

siggi2

---

### Post by Skaperen on 2015-07-23
it would be nice if a standard for a sibling filename would be used as a thumbnail or other features.  then at least issues like this could be worked around on-the-fly as needed.  for example for file **mymovie.mpg** *.mymovie.mpg.jpeg* for a tumbnail and *.mymovie.mpg.opt* for special usage options to "play" this file.

---

### Post by siggi2 on 2015-07-23
It would be also nice if Ubuntu 14.04.2 could do the same as Lubuntu 14.04.2 does, which shows thumbnails of my MPG files easily! Why has Ubuntu been "downgraded" in this respect :mad:

---

### Post by siggi2 on 2015-07-23
Is there any trusted ppa with a potent thumbnailerprogram I could use?

---

### Post by siggi2 on 2015-07-23
Does anybody know of a trusted ppa that offers a potent thumbnailerprogram?

---

### Post by papibe on 2015-07-23
Hi siggi2.

Please don't bump your thread so often. Please allow 24hrs before bumping it again.

You could try ffmpegthumbnailer. Here's a couple of guides: [this]("http://askubuntu.com/questions/2608/nautilus-video-thumbnails-without-totem") and [that]("http://askubuntu.com/questions/150492/way-to-make-video-thumbnails-generate-from-vlc-instead-of-totem").

Regards.

---

### Post by siggi2 on 2015-07-24
Thanks, papibe, but it won't work:

```
~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ffmpeg' has no installation candidate
```
To my knowledge, ffmpeg has been replaced with avcon/WinFF in Ubuntu 14.04 And > is referred to by another package means it is referred to by avcon. I have both programs. WinFF is very good to convert Videoformats, but MPG still does not thumbnail.

Lubuntu does, but there is a difference: Lubuntu stores thumbnails in **.thumbnails**, Ubuntu does it in **.cache/thumbnails**. Could this make the difference?

N.B. In my Ubuntu, MP4 shows in Nautilus as thumbnails, and the "old" MPG does show after having it converted with option "MPEG-2" to MPG. But, as I mentioned, I would have hundreds of videodfiles to convert! 

Sadly :-(

siggi

---

### Post by siggi2 on 2015-07-24
After having read this:

[B]Latest news
WEB UPD8: FFmpeg Returns To The Official Ubuntu Repositories With Ubuntu 15.04 Vivid Vervet[/B]
(from:[http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04]("http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04"))
and not being willing to leave my 14.04 LTS, I did the "leap of faith", removed libav-tools, and followed this:

[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-mediahttp://")

Now I have ffmpeg ad ffmpefthumbnailer, finally.

But, nothing changed, no thumbnails for my MPG files :mad:

I hope I can trust this launchpad.net site?

Why can't Ubuntu do so simple things Lubuntu can?

---

### Post by siggi2 on 2015-07-24
Compliments of Lubuntu, solved:

_Lubuntu 14.04.2_
*/usr/share/thumbnailers*
evince.thumbnailer
ffmpegthumbnailer.thumbnailer

_Ubuntu 14.04.2_
*/usr/share/thumbnailers*
evince.thumbnailer
ffmpeg.thumbnailer
ffmpegthumbnailer.thumbnailer
gnome-font-viewer.thumbnailer
totem.thumbnailer

So, I renamed ffmpeg.thumbnailer and totem.thumbnailer to backup names so that they could not do any harm anymore, and...   voila... excellent thumbnails for my MPGs :popcorn:

---

### Post by siggi2 on 2015-07-25
Even after having ffmpeg removed the tumbnails keep in full swing. So, no use anay more for this ppa mentioned above.

---

### Post by siggi2 on 2015-07-26
After a new installation of Ubuntu 14.04.2 only the following steps were necessary to thumbnail MPG:

* install ffmpegthumbnailer

* klick on the file and install what totem wanted to have installed

---

