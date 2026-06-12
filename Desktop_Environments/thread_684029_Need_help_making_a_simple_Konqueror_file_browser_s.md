---
title: "Need help making a simple Konqueror file browser script"
date: 2008-01-31
forum: Desktop Environments
---

### Post by tj.milligan on 2008-01-31
What I'd like to do in Kubuntu is be able to right-click a wav file and have a custom "Convert to mp3" menu option.

I can do this w/ a bash script, convert.sh:

```

#!/bin/sh
ffmpeg -b 128k -i $1 $2.mp3
rm -R $1

```

Then making it executable and running it:

```

./convert.sh in.wav out

```

However, I'm making this for a friend (who uses krecord to "tape" class lectures); and I don't want him to have to use the terminal if it's possible to make it so he can simply right click on the wav files he'd like to convert. Thanks in advance!

---

### Post by tj.milligan on 2008-02-01
Bump.

---

### Post by monte48lowes on 2008-02-01
What you are trying to build is known as a service menu. Information can be found here:

[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html")

Mike

---

### Post by tj.milligan on 2008-02-01
> **monte48lowes said:**
> What you are trying to build is known as a service menu. Information can be found here:

[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html")

Mike

Thanks for the tip! I wrote a quick service menu file, but I'm not on a KDE machine right now (rather Gnome-based Ubuntu), so I'll post back later to report if I was successful. In the meantime, here's my convert.desktop file:

```

[Desktop Entry]
ServiceTypes=audio/*
Actions=convertToMP3

[Desktop Action convertToMP3]
Name=Convert to MP3
Exec=/bin/sh -c "ffmpeg -b 128k -i %u %u.mp3"

```

Using the wildcard for MIME type (audio/* instead of audio/mpeg) should allow me to convert any ffmpeg supported file to mp3, rather than just wav! The only thing I'm unsure of is the line

```

Exec=/bin/sh -c "ffmpeg -b 128k -i %u %u.mp3"

```

This looks like it would take an input file, say my.wav, and convert it to my.wav.mp3. I'd like it to convert from my.wav (or my.aiff, etc) to my.mp3. **Any ideas?** Also, the iso I'm downloading w/ KDE on it won't be finished until tomorrow. **Can anyone test this in the meantime?** I'll be following up on this ASAP.

---

### Post by monte48lowes on 2008-02-01
Well I was working with what you had. I started with writing the script to a file and pointing to it. You shortcutted that... and it works. Nice job.

I noticed you removed the -R from that was in the script. That's the safe way I suppose.
Mike

---

### Post by tj.milligan on 2008-02-04
Finally was able to test this on a kde machine today and indeed, it does work! Thanks for the help, monte48lowes.

---

