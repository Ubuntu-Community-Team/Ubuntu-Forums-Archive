---
title: "temporary flash videos"
date: 2009-05-14
forum: General Help
---

### Post by alberto ferreira on 2009-05-14
Hi, I use Ubuntu 8.04 and I used to save youtube videos by going to /tmp and copying the Flash* file.

Now, however that file is always corrupt and when I open it -- although the file size is still in the 10-20MB range totem gives this error: > Internal data stream errorWhy does this happen? I don't remember changing anything and I would really like to be able to save videos again.

---

### Post by mb_webguy on 2009-05-14
I don't know why you're getting that error, but I also don't save flash videos that way.  I use the Video DownloadHelper extension in Firefox, and it's never given me any problems.  It also allows you to transcode the videos using ffmpeg or mencoder.

---

### Post by x33a on 2009-05-14
another downloadhelper user here.

it is a really useful addon, and it keeps getting better and better.

it even gives you the choice to download HD youtube videos.

---

### Post by FakeOutdoorsman on 2009-05-15
I still go by the /tmp method.  Recently, some YouTube videos now appear to be H.264 video and AAC audio in a FLV container, which is not a recommended format, although some players work fine with it.  Looks like Totem may not like that combination.  You could copy the streams to a more appropriate format:
```
ffmpeg -i /tmp/FlashJGcIBd -acodec copy -vcodec copy output.mp4

```
No quality reduction because there is no re-encoding.  The repository FFmpeg (pre-Jaunty Jackalope) may choke on these files, but a recent revision works fine:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

Alternatively, you could try a different media player.  My favorite is MPlayer (with SMPlayer frontend).  For those who want the full potential of this excellent player andrew.46 has written some great guides:
[url=http://ubuntuforums.org/showthread.php?t=1081070]
HowTo: Install the very latest MPlayer under Jaunty Jackalope[/url]
[url=http://ubuntuforums.org/showthread.php?t=1154431]
Top 10 Tricks and Tips for the svn MPlayer[/url]

---

### Post by alberto ferreira on 2009-05-17
I also prefer using the /tmp file because I don't have much bandwith so ...


Tried to use the ffmpeg command and got this errors:

> 
....
....
[flv @ 0xb7f0e110]Unsupported video codec (7)
[flv @ 0xb7f0e110]Unsupported video codec (7)
[flv @ 0xb7f0e110]Unsupported video codec (7)
Input #0, flv, from './Flashq3D1l2':
  Duration: 00:07:13.6, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: 0x0007, 1000.00 fps(r)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
File '/home/a/out.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/home/a/out.mp4':
  Stream #0.0: Video: 0x0007, q=2-31, 1000.00 fps(c)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0xb7f0e110]dimensions not set
Could not write header for output file #0 (incorrect codec parameters ?)


---

### Post by alberto ferreira on 2009-05-17
Now I followed your ffmpeg and x264 installation guide and it works !

Thanks a LLLLLLLLLLLLOOOOOOOOOOOOOOOOTTTTTTTTTTTT for your great guide!!!!!!!!! :D

---

### Post by lucifer1 on 2010-10-31
i used to find my streamed flash video in my system file/tem now after that shockwave has been installed and i cannot remove it to install the flash player 10.1 i dont find any video in the system file/temp 
any one can help

---

### Post by chetancrasta on 2011-02-25
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by belastd on 2011-02-25
for downloading videos from youtube i use ClipGrab,it work

---

### Post by chetancrasta on 2011-02-25
@belastd: Haven't tried out the specific plugin you mentioned, though.
But I have tried a few of the flash downloader plugins, and they all had a major problem. They do not allow one to save flash video that has already been buffered. Instead, the plugin starts the download from the beginning. Therefore, when using one of these plugins, one often downloads the same video twice.

---

