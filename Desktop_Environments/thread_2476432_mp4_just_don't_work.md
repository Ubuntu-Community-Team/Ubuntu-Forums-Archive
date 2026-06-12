---
title: "mp4 just don't work"
date: 2022-06-26
forum: Desktop Environments
---

### Post by UBUminJ on 2022-06-26
I can do whatever explanation is on the net.
mp4 cannot be played on my Ubuntu 20.04
Even VLC is not able to do it.
(I cannot even upload a screenshot here. I click on add, browse, upload and nothing happens.)

---

### Post by iamjiwjr on 2022-06-26
I always fear I'm sounding like talking down to people so I apologize if you already know all this stuff.

If you've not done it install synaptic, so you can get easy access (for those of us not so terminal-savvy) to multimedia codecs missing at install. One terminal entry - Enter in terminal "sudo apt install synaptic." Open synaptic after installation and search the word "restricted." Scroll to the bottom of the list and choose the ubuntu-restricted-addons and ubuntu-restricted-extras. Install them. This will also add the microsoft fonts and other files to give you a full experience. After I do this mp4's play fine for me.

---

### Post by UBUminJ on 2022-06-26
Thanks but unfortunately, doesn't work in my case.

---

### Post by TheFu on 2022-06-26
mp4 is a container, not a video codec or audio codec.

99% of the time, if **mpv** or **mplayer** or **vlc** cannot play the video inside an mp4 container, it is because the video file is corrupted.  Recreate it or download it again is probably the only answer.  For a long time, some phones made non-standard  mp4 files. I haven't seen that in a few years, but I suppose it could still happen.

I'm making all sorts of other assumptions above.  Like the GPU drivers on the system are working for everything else.
Do other video files playback?
What was the source of the video?
Is VLC a snap package?  Snaps run in restricted sandboxes which don't allow access or integrations with other programs.  Using a non-snap version will probably work.  There were a number of issues with the VLC snap package, addons and integrations back in 2020.  I've never used the snap version, so I've never seen these issues.

---

### Post by yancek on 2022-06-26
>  mp4 cannot be played on my Ubuntu 20.04

Where did you get VLC from to download?  Has it ever worked?  If so, did yo make any changes?  What type of mp4 file and where did you get it, download, self-created?  How do you open the mp4 file with VLC?  Do you open VLC from a terminal, click the Media tab and select Open File and navigate to the location?  Do you just double click on the mp4 icon or do you right click the mp4 file and select open with VLC (or other application if VLC is not the default)?  All of these methods work for me on 20.04 and should work on any 20.04 install.

---

### Post by SeijiSensei on 2022-06-27
I use mpv with smplayer as the front-end. Plays everything I throw at it.

```
sudo apt install mpv smplayer
```

---

### Post by mike010 on 2022-06-27
I had a issue playing .mp4 files with 22.04 removing gstreamer1.0-vaapi file fixed it for me might try that.

---

### Post by ActionParsnip on 2022-06-28
```

sudo apt -y install ubuntu-restricted-extras

```
use TAB and ENTER to accept the license.

---

