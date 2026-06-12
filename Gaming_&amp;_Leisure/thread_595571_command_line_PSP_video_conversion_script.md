---
title: "command line PSP video conversion script"
date: 2007-10-28
forum: Gaming &amp; Leisure
---

### Post by Kilbasar on 2007-10-28
NOTE: This is not for beginners. Check out PSPVC.

Although there are already plenty of ways to convert videos to a format viewable on the PSP, I wanted something really simple that I could run from the command line and not have to pass a million options to. So I made this very basic perl script that uses ffmpeg to convert a video to PSP format. I made this for personal use, but figured someone else might enjoy it, so here it is. first off, you must have ffmpeg already installed, with the proper codecs. I think the easiest way is to download the source from their website and configure it with every codec under the sun:

./configure --enable-mp3lame --enable-libogg --enable-vorbis --enable-faad --enable-dts --enable-pp --disable-debug --enable-pthreads --enable-dc1394 --enable-gpl --enable-faac --enable-libgsm --enable-xvid --enable-a52

if you're missing any libraries, they're all available in the ubuntu repositories.

now that you've got ffmpeg set up, unpack my script ("pspconv") to somewhere like /usr/local/bin. now run it like so:

pspconv input.avi "Title Of Video" -nXX

where XX is the video's ID number (ie, M4V000XX.MP4). You can leave out the title or the ID number if you want, it'll use default values (title will be filename without extension). Converted video and thumbnail will be created in the current directory.

---

