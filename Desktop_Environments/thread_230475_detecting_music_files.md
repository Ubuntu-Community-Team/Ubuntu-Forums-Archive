---
title: "detecting music files?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by JohnJSal on 2006-08-06
Hi everyone. I just tried to import all my music into the Rhythmbox program, but it says that my files aren't valid audio files. They are just mp3s, but it won't import them. It only imported two wavs. Is there something more I need to do for this to work?

Thanks.

---

### Post by Jagot on 2006-08-06
Read this link:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Specifically for MP3's you need the gstreamer0.10-plugins-ugly package which is in the universe repository.

---

### Post by JohnJSal on 2006-08-06
Thanks!

---

### Post by sidlinux on 2006-08-06
I did what Jagot suggested that is download the gstreamer0.10-plugins-ugly using SPM, but this time, I got no sound :(, but was able to import the files.  Is there anything else I have to install?  I use a Dell Inspiron 1100 laptop.  Any help is appreciated.

Sidney

---

### Post by Skia_42 on 2006-08-06
Check out the link that he posted ([https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats"))
and download all the plugins that apply to your system. if it still does not work, import a cd and see if the imported files work.

---

