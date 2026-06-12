---
title: "soundconverter 0.9.4 Oubuntu1 stalls"
date: 2007-07-07
forum: Desktop Environments
---

### Post by johnbl on 2007-07-07
Have installed soundconverter plus gstream {lots of variations mostly .10 but LAME 0.8 }

soundconverter  opens ok, transfer to mp3 is available. But when I select tracks - wma - they are apparently read ok but conversion stalls. zero length files are written but that's it.

I'm stumped. Has anyone solved a similar problem or have any suggestions to get me out of this hole!

John

---

### Post by badman3k on 2007-10-02
Hey, I don't know whether you're still having the same problem, but I was suffering from the same problem. In the end I managed to find a solution to the problem and it was as follows:

```
sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

Then obviously have the soundconverter installed and things seemed to work a lot better. I have only tested this converting .wma to .mp3 and haven't tried other file formats, but I hope this is of use to someone.

Richard

---

### Post by johnbl on 2007-10-02
Thanks Richard, that was one of the problems I'd sort of given up on. Nice one.

My latest ' curious ' effect is the workspaces blanking. If I select a new workspace I get a screen minus the system controls both top and bottom of the screen.

Have you come across that ' effect ' by any chance and solved it?

John

---

### Post by Huss on 2008-01-02
Thanks badfella, that worked for me.

---

