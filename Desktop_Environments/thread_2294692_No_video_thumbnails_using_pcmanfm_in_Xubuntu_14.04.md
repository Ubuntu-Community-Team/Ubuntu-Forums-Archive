---
title: "No video thumbnails using pcmanfm in Xubuntu 14.04"
date: 2015-09-12
forum: Desktop Environments
---

### Post by necbot on 2015-09-12
I have no problems viewing image thumbnails.  My issue is viewing video thumbnails.  On some of my videos I can see thumbnails but on others I cannot.  Strangley there is not file extension pattern.  For example, some .avi files will show thumbnails, some .avi files won't.  I installed ffmegthumbnailer but the problem still persists.  My /usr/share/thumbnailers/ffmpegthumbnailer.thumbnailer file looks like this...

```
[Thumbnailer Entry]
TryExec=ffmpegthumbnailer
Exec=ffmpegthumbnailer -i %i -o %o -s %s -f
MimeType=video/jpeg;video/mp4;video/mpeg;video/quicktime;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-msvideo;video/x-flv;video/x-matroska;video/webm;
```

Any ideas?  Thanks.

---

### Post by mc4man on 2015-09-13
I've no clue if pcmanfm will use ffmegthumbnailer if present or not
(- I use ffmegthumbnailer here with nautilus but that requires replacing totem.thumbnailer.

Anyway your thumbnails should be stored in ~/.thumbnails , try removing either the 'failed' folder inside or just delete the whole folder. Then open your Videos folder/folders with vids with pcmanfm first (before thunar if still installed.
See if it does better..

As far as ffmpegthumbnailer - the Mimetypes is a bit sparse - I use the attached here.

---

