---
title: "Recording sound from videos"
date: 2009-04-18
forum: General Help
---

### Post by cchase88 on 2009-04-18
Is it possible to record sound from videos somehow? I'm guessing it's possible other than putting a mic up to my speakers and recording that way.

---

### Post by mb_webguy on 2009-04-19
If it is a video you have on your computer or a DVD, or is it a video on a website like YouTube?

If it's the former, then you can do it fairly easily with the VLC media player.  (You can do it even more easily with command-line tools like mencoder and ffmpeg, but from the level of experience indicated by your question I think it would probably be best to stick with GUI applications.)

You can install VLC from the official repositories (using Add/Remove or Synaptic).  You can get the latest version by adding [this PPA]("https://launchpad.net/~c-korn/+archive/vlc") to your Software Sources first.

Open VLC and go to Media->Convert/Save.  Select your video, and click the Convert/Save button.  On the Encapsulation tab, click WAV.  On the Audio Codec tab, click the checkbox next to Audio, and select WAV.  In the Outputs section, click the checkbox next to File, and select a name and location for the output file.  Now click the Save button so save the audio as a wav file.  Now you can use something like Audacity to edit the audio and convert it to some format with better compression, like mp3 or Ogg Vorbis.

If the video you're talking about is on a website like YouTube, you'll first have to copy the video to your computer using something like the [Video DownloadHelper extension]("https://addons.mozilla.org/en-US/firefox/addon/3006") for Firefox before follow the instructions above.

---

### Post by cchase88 on 2009-04-20
Thanks for your reply. I'm trying to record sound from a video on the web. It seems unnecessary to first download the video before you're able to record the audio from it. I would think there's a way to just record the line out. But maybe not.

Any other suggestions?

---

