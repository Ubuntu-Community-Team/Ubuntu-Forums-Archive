---
title: "XFCE Thumbnails not appearing in Thunar."
date: 2010-08-26
forum: Desktop Environments
---

### Post by chris_andrew on 2010-08-26
Hi, everybody.

When I open Thunar, I can see thumbnails of jpegs, but not for video, pdf or document files. I've got the Thumbnailers package installed as part of XFCE Goodies, and also ffmpegthumbnailers (? I think, I'm at work so can't check). I've looked for a setting to change, but can't see anything relevant. Previous installations have allowed me to have beautiful thumnail icons, can anyone help me get them back?

Many thanks,

Chris.

---

### Post by x1a4 on 2010-08-26
Open Thunar and press Ctrl+1 and see if that gives you thumbnails.  Also, make sure 'Show thumbnails' is checked in Properties. 

Alternatively, you may want to try resetting Thunar settings and see if that helps.
```
mv ~/.config/Thunar ~/.config/Thunar.bak
```

---

### Post by chris_andrew on 2010-08-27
Tanks for your reply and sorry for the delay in mine. Unfortunately none of the suggestions helped.  I'm otherwise leased with my Squeeze install, so I think I'll just have to accept that this is a small downside.

Cheers,

Chris.

---

### Post by bobcollard on 2010-08-27
> **chris_andrew said:**
> Tanks for your reply and sorry for the delay in mine. Unfortunately none of the suggestions helped.  I'm otherwise leased with my Squeeze install, so I think I'll just have to accept that this is a small downside.

Cheers,

Chris.
Open Thunar>View>View as Icons

---

### Post by x1a4 on 2010-08-27
Don't give up just yet.  Look in /usr/share/thumbnailers/ and see if you have .desktop files for each of the file formats you don't have thumbnails for.  There might be missing files in which case they can be recreated.  

Look in /usr/lib/thunar-thumbnailers and see if you have thumbnailers for videos, pdfs, etc. 

Also try clearing your thumbnail cache by deleting ~/.thumbnails/
```
rm -rf ~/.thumbnails/
```
This will force all thumbnails to be recreated which might also recreate the ones that weren't done before.

---

### Post by chris_andrew on 2010-08-27
> **bobcollard said:**
> Open Thunar>View>View as Icons

Tried that. I can get jpeg thumbnails, going to have a look at the solution in the post that followed yours.

Thanks,

Chris.

---

### Post by chris_andrew on 2010-08-27
more /usr/share/thumbnailers/thunar-vfs-font-thumbnailer-1.desktop:

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=X-Thumbnailer
Name=Thunar Font Thumbnailer
Comment=Creates thumbnails for font files
TryExec=/usr/lib/thunar/thunar-vfs-font-thumbnailer-1
MimeType=application/x-font-otf;application/x-font-pcf;application/x-font-ttf;ap
plication/x-font-type1;
X-Thumbnailer-Exec=/usr/lib/thunar/thunar-vfs-font-thumbnailer-1 -i %i -o %o -s 
%s

# vi:set encoding=UTF-8:
```


Unfortunately, 
```

rm -rf ~/.thumbnails/
```

didn't help.

Does the first bit help? Does anyone that is getting good thumbnails other than jpeg's have a different entry in this file?

Thanks,

Chris.

---

### Post by bobcollard on 2010-08-27
Not sure what you are after?  My Documents Folder looks like this:

---

### Post by demosthenese on 2010-08-28
Does /usr/share/thumbnailers have a desktop file for ffmpeg?

My Ffmpeg Thumbnailer.desktop contains:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=X-Thumbnailer
Name=FFmpeg Thumbnailer
TryExec=ffmpegthumbnailer
MimeType=video/jpeg;video/mp4;video/mpeg;video/quicktime;video/x-ms-asf;video/x-ms-wm;video/x-ms-wmv;video/x-msvideo;video/x-flv;application/x-flash-video;video/3gpp;video/x-matroska;
X-Thumbnailer-Exec=/usr/lib/thunar-thumbnailers/ffmpeg-thumbnailer %i %o %s

```

Also check in synaptic that you have installed ffmpegthumbnailer.

---

### Post by chris_andrew on 2011-05-24
> **x1a4 said:**
> Don't give up just yet.  Look in /usr/share/thumbnailers/ and see if you have .desktop files for each of the file formats you don't have thumbnails for.  There might be missing files in which case they can be recreated. 

Bingo! The avi extension is missing. Can I just create any empty file that looks like the other extensions, or is there a special way?

Cheers,

Chris.

---

### Post by chris_andrew on 2011-05-24
I su'd to root, then cd'd to /usr/share/thumbnailers. I then did 

```
cp dvi-thumbnailer.desktop avi-thumbnailer.desktop
```

This created the entry I needed. I closed and re-opened Thunar, and I can now see avi thumbnails.

Perfect.

Cheers,

Chris.

---

