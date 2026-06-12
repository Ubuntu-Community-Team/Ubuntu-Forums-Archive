---
title: "Can't change JPG association"
date: 2014-06-28
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2014-06-28
I'm having a weird problem, where either in Nautilus when in Unity, or in Caja when in MATE, where I can not change the file association for JPG's..  It brings up the properties window that lets me change it, but hitting a different radio button, just snaps back to the default image viewer.

How can I actually change the association?  Other file types like PNG, can change to anything just fine.

---

### Post by tgalati4 on 2014-06-28
```
apropos mime
man mimeopen
```

There are a lot of places where mime types are stored--system-level, user-level, application-level.  What version of Linux do you want to troubleshoot?

---

### Post by deadflowr on 2014-06-28
> **Brandon_MacEachern said:**
> I'm having a weird problem, where either in Nautilus when in Unity, or in Caja when in MATE, where I can not change the file association for JPG's..  It brings up the properties window that lets me change it, but hitting a different radio button, just snaps back to the default image viewer.

How can I actually change the association?  Other file types like PNG, can change to anything just fine.

I don't know what is happening for you, but I simply right-click a file, open properties, go to open with it will list the default that is set for that file type, and a number of selections I can choose below that. I then highlight the selection I want and click on the button "set as default".

---

### Post by Brandon_MacEachern on 2014-06-28
It's Ubuntu 14.04, using either Mate or Unity.

I right-click the file, properties, go to open with, and for JPG's, I can NOT change them whatsoever.  I can for PNG though.  Setting another for jpg as default just gets ignored, nothing actually changes.

I ended up trying Ubuntu Tweak, that didn't work either, it will not change JPG's.  Tried then in Details in System Preferences, and changing the app for photos there DOES change JPG.  But I am not sure why I can't set it down at the file type level, only by category.

---

### Post by Brandon_MacEachern on 2014-06-28
Here's a video showing exactly what is happening.

[http://youtu.be/3Ej4gIVljxU](http://youtu.be/3Ej4gIVljxU)

I don't want the OS trying to associate "all" photos to one app like it seems to be doing.  I want individual control over the file types.

---

### Post by Brandon_MacEachern on 2014-06-28
I'm taking it the video has stumped some people.  :)

Since it was originally thought I was simply just doing it wrong.

---

### Post by mc4man on 2014-06-29
This is actually part of a bug where if you have used System Settings > Details > Default app... or possibly that tweak tool to set an overall default then when trying to do *some* individual mimes it won't work (gets set back to previous overall default app

If you want to post the contents of ~/.local/share/applications/mimeapps.list maybe I can pick out your issue.

Quicker solution - 
delete that file, then just set your associations from the context menu on a per mime basis, not thru system setting, ect.

---

### Post by Brandon_MacEachern on 2014-06-29
Thanks.  Sorry for the long post but here's the contents.  If deleting the file is easier, I can always just setup things all over again.

```
[Default Applications]text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
x-scheme-handler/mailto=thunderbird.desktop
message/rfc822=thunderbird.desktop
application/x-extension-eml=thunderbird.desktop
x-scheme-handler/news=thunderbird.desktop
x-scheme-handler/feed=thunderbird.desktop
application/rss+xml=thunderbird.desktop
application/x-extension-rss=thunderbird.desktop
audio/x-vorbis+ogg=banshee.desktop
audio/3gpp=banshee.desktop
audio/AMR=banshee.desktop
audio/AMR-WB=banshee.desktop
audio/ac3=banshee.desktop
audio/ape=banshee.desktop
audio/avi=banshee.desktop
audio/basic=banshee.desktop
audio/flac=banshee.desktop
audio/midi=vlc.desktop
audio/mp=banshee.desktop
audio/mp2=banshee.desktop
audio/mp3=banshee.desktop
audio/mp4=vlc.desktop
audio/mp4a-latm=banshee.desktop
audio/mpc=banshee.desktop
audio/mpeg=banshee.desktop
audio/mpeg3=banshee.desktop
audio/mpegurl=banshee.desktop
audio/musepack=banshee.desktop
audio/ogg=banshee.desktop
audio/vorbis=banshee.desktop
audio/wav=banshee.desktop
audio/wave=banshee.desktop
audio/x-amzxml=banshee.desktop
audio/x-ape=banshee.desktop
audio/x-flac=vlc.desktop
audio/x-it=banshee.desktop
audio/x-m4a=vlc.desktop
audio/x-matroska=vlc.desktop
audio/x-mod=banshee.desktop
audio/x-mp=banshee.desktop
audio/x-mp3=vlc.desktop
audio/x-mpc=banshee.desktop
audio/x-mpeg=vlc.desktop
audio/x-mpeg-3=banshee.desktop
audio/x-mpegurl=banshee.desktop
audio/x-ms-asf=vlc.desktop
audio/x-ms-asx=vlc.desktop
audio/x-ms-wax=vlc.desktop
audio/x-ms-wma=banshee.desktop
audio/x-musepack=banshee.desktop
audio/x-ogg=banshee.desktop
audio/x-pn-aiff=vlc.desktop
audio/x-pn-au=vlc.desktop
audio/x-pn-wav=vlc.desktop
audio/x-pn-windows-acm=vlc.desktop
audio/x-s3m=banshee.desktop
audio/x-sbc=banshee.desktop
audio/x-scpls=banshee.desktop
audio/x-speex=banshee.desktop
audio/x-tta=banshee.desktop
audio/x-vorbis=banshee.desktop
audio/x-wav=banshee.desktop
audio/x-wavpack=banshee.desktop
audio/x-xm=banshee.desktop
video/x-ogm+ogg=vlc.desktop
video/dv=vlc.desktop
video/mpeg=vlc.desktop
video/x-mpeg=vlc.desktop
video/msvideo=vlc.desktop
video/quicktime=vlc.desktop
video/x-anim=vlc.desktop
video/x-avi=vlc.desktop
video/x-ms-asf=vlc.desktop
video/x-ms-wmv=vlc.desktop
video/x-msvideo=vlc.desktop
video/x-nsv=vlc.desktop
video/x-flc=vlc.desktop
video/x-fli=vlc.desktop
video/x-flv=vlc.desktop
video/vnd.rn-realvideo=vlc.desktop
video/mp4=vlc.desktop
video/mp4v-es=vlc.desktop
video/mp2t=vlc.desktop
video/x-matroska=vlc.desktop
video/webm=vlc.desktop
application/x-ms-dos-executable=wine.desktop
application/x-compressed-tar=engrampa.desktop
application/x-bzip-compressed-tar=engrampa.desktop
text/plain=pluma.desktop
image/bmp=eom.desktop
image/gif=eom.desktop
image/jpeg=eom.desktop
image/png=eom.desktop
image/tiff=eom.desktop
inode/directory=caja-folder-handler.desktop
video/x-theora+ogg=vlc.desktop
video/3gpp=vlc.desktop
image/jpg=eom.desktop
image/pjpeg=eom.desktop
image/x-bmp=eom.desktop
image/x-gray=eom.desktop
image/x-icb=eom.desktop
image/x-ico=eom.desktop
image/x-png=eom.desktop
image/x-portable-anymap=eom.desktop
image/x-portable-bitmap=eom.desktop
image/x-portable-graymap=eom.desktop
image/x-portable-pixmap=eom.desktop
image/x-xbitmap=eom.desktop
image/x-xpixmap=eom.desktop
image/x-pcx=eom.desktop
image/svg+xml=eom.desktop
image/svg+xml-compressed=eom.desktop
image/vnd.wap.wbmp=eom.desktop
application/x-gnome-saved-search=nautilus.desktop
image/x-kde-raw=shotwell-viewer.desktop
audio/webm=vlc.desktop
audio/x-real-audio=vlc.desktop
audio/x-pn-realaudio=vlc.desktop
audio/vnd.rn-realaudio=vlc.desktop
audio/x-pn-realaudio-plugin=vlc.desktop
audio/amr=vlc.desktop
audio/amr-wb=vlc.desktop
application/zip=engrampa.desktop


[Added Associations]
x-scheme-handler/news=thunderbird.desktop;
x-scheme-handler/feed=thunderbird.desktop;
application/rss+xml=thunderbird.desktop;
application/x-extension-rss=thunderbird.desktop;
audio/3gpp=banshee.desktop;
audio/AMR=banshee.desktop;
audio/AMR-WB=banshee.desktop;
audio/ac3=banshee.desktop;
audio/ape=banshee.desktop;
audio/avi=banshee.desktop;
audio/basic=banshee.desktop;
audio/flac=banshee.desktop;
audio/midi=banshee.desktop;vlc.desktop;
audio/mp=banshee.desktop;
audio/mp2=banshee.desktop;
audio/mp3=banshee.desktop;
audio/mp4=banshee.desktop;vlc.desktop;
audio/mp4a-latm=banshee.desktop;
audio/mpc=banshee.desktop;
audio/mpeg3=banshee.desktop;
audio/mpegurl=banshee.desktop;
audio/musepack=banshee.desktop;
audio/ogg=banshee.desktop;
audio/vorbis=banshee.desktop;
audio/wav=banshee.desktop;
audio/wave=banshee.desktop;
audio/x-amzxml=banshee.desktop;
audio/x-ape=banshee.desktop;
audio/x-flac=banshee.desktop;vlc.desktop;
audio/x-it=banshee.desktop;
audio/x-m4a=banshee.desktop;vlc.desktop;
audio/x-matroska=banshee.desktop;vlc.desktop;
audio/x-mod=banshee.desktop;
audio/x-mp=banshee.desktop;
audio/x-mp3=banshee.desktop;vlc.desktop;
audio/x-mpc=banshee.desktop;
audio/x-mpeg=banshee.desktop;vlc.desktop;
audio/x-mpeg-3=banshee.desktop;
audio/x-ms-asf=banshee.desktop;vlc.desktop;
audio/x-ms-asx=banshee.desktop;vlc.desktop;
audio/x-ms-wax=banshee.desktop;vlc.desktop;
audio/x-ms-wma=banshee.desktop;
audio/x-musepack=banshee.desktop;
audio/x-ogg=banshee.desktop;
audio/x-pn-aiff=banshee.desktop;vlc.desktop;
audio/x-pn-au=banshee.desktop;vlc.desktop;
audio/x-pn-wav=banshee.desktop;vlc.desktop;
audio/x-pn-windows-acm=banshee.desktop;vlc.desktop;
audio/x-s3m=banshee.desktop;
audio/x-sbc=banshee.desktop;
audio/x-speex=banshee.desktop;
audio/x-tta=banshee.desktop;
audio/x-vorbis=banshee.desktop;
audio/x-wavpack=banshee.desktop;
audio/x-xm=banshee.desktop;
video/dv=vlc.desktop;
video/x-anim=vlc.desktop;
video/x-ms-asf=vlc.desktop;
video/x-ms-wmv=vlc.desktop;
video/x-msvideo=vlc.desktop;
video/x-nsv=vlc.desktop;
video/x-flc=vlc.desktop;
video/x-fli=vlc.desktop;
video/vnd.rn-realvideo=vlc.desktop;
video/mp4v-es=vlc.desktop;
application/x-ms-dos-executable=wine.desktop;
application/x-compressed-tar=engrampa.desktop;
application/x-bzip-compressed-tar=engrampa.desktop;
inode/directory=nautilus-folder-handler.desktop;
image/jpeg=wine-extension-sta.desktop;wine-extension-jpe.desktop;wine-extension-jfif.desktop;display.im6.desktop;gimp.desktop;eog.desktop;eom.desktop;
application/octet-stream=vlc.desktop;
image/gif=vlc.desktop;eog.desktop;
video/x-theora+ogg=vlc.desktop;
video/3gpp=vlc.desktop;
audio/x-mpegurl=vlc.desktop;banshee.desktop;
audio/x-scpls=vlc.desktop;banshee.desktop;
audio/x-wav=vlc.desktop;banshee.desktop;
image/bmp=eog.desktop;
image/jpg=eog.desktop;eom.desktop;
image/pjpeg=eog.desktop;eom.desktop;
image/png=eog.desktop;
image/tiff=eog.desktop;
image/x-bmp=eog.desktop;eom.desktop;
image/x-gray=eog.desktop;eom.desktop;
image/x-icb=eog.desktop;eom.desktop;
image/x-ico=eog.desktop;eom.desktop;
image/x-png=eog.desktop;eom.desktop;
image/x-portable-anymap=eog.desktop;eom.desktop;
image/x-portable-bitmap=eog.desktop;eom.desktop;
image/x-portable-graymap=eog.desktop;eom.desktop;
image/x-portable-pixmap=eog.desktop;eom.desktop;
image/x-xbitmap=eog.desktop;eom.desktop;
image/x-xpixmap=eog.desktop;eom.desktop;
image/x-pcx=eog.desktop;eom.desktop;
image/svg+xml=eog.desktop;eom.desktop;
image/svg+xml-compressed=eog.desktop;eom.desktop;
image/vnd.wap.wbmp=eog.desktop;eom.desktop;
image/x-kde-raw=ufraw.desktop;shotwell-viewer.desktop;
audio/webm=vlc.desktop;
audio/mpeg=vlc.desktop;banshee.desktop;
audio/x-real-audio=vlc.desktop;
audio/x-pn-realaudio=vlc.desktop;
audio/vnd.rn-realaudio=vlc.desktop;
audio/x-pn-realaudio-plugin=vlc.desktop;
audio/amr=vlc.desktop;
audio/amr-wb=vlc.desktop;
audio/x-vorbis+ogg=banshee.desktop;
application/zip=engrampa.desktop;
```

---

### Post by mc4man on 2014-06-29
The issue is likely created because there are 2 defaults for basically the same mime - 
image/jpg=eom.desktop
image/pjpeg=eom.desktop
Try deleting the image/pjpeg=eom.desktop line & space, then see if you can change the default for jpg from the context menu > properties, ect.

If that doesn't work then delete both lines & try again

Edit: do this in both the Default & Added sections plus in the added remove the dupe of eom.desktop on the image/jpg= line

---

