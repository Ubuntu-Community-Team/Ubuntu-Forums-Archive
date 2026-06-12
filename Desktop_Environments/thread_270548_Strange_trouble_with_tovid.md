---
title: "Strange trouble with tovid:"
date: 2006-10-03
forum: Desktop Environments
---

### Post by dyous87 on 2006-10-03
I'm having some trouble with tovid and it's really wierd. I want to convert a video I have from .avi format to dvd format so that I could burn it onto a dvd. I't takes a while to encode and when it does tovid tells me that it was succesful and that my encoded movie should be located in such and such directory. The problem is that it isn't there and I've tried it with two different files. Here is my output from tovid:
```
tovid
DVD and (S)VCD video conversion script
Version 0.28
with: core magick dvd vcd transcode
http://www.tovid.org
--------------------------------
tovid command-line used:
-dvd -in swmovie.avi -out swmovie_encoded
Using config file /home/david/.tovid/tovid.config, containing the following options:
(none)
Changing to working directory: /home/david/Movies

=========================================================

Converting /home/david/Movies/swmovie.avi to compliant NTSC DVD format
Saving to /home/david/Movies/swmovie.mpg
Storing log and temporary files in /home/david/Movies/swmovie_encoded.oLnTii

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 5239 MB of disk space.
You currently have 86914 MB available in this directory.
Analysis of file /home/david/Movies/swmovie.avi:
  720 x 304 pixels, 23.000 fps
  Duration (best guess): 02:04:45 (HH:MM:SS)
  RV40 video with ffcook audio
Target format:
  720 x 480 pixels, 29.970 fps
  m2v video with ac3 audio
  7840 kbits/sec video, 224 kbits/sec audio
Using auto-detected aspect ratio of 236:100 (override with -aspect)
Letterboxing vertically
Input is not 29.970 fps. Framerate will be adjusted.
Scaling picture to 720 x 368
Centering picture against a 720 x 480 black background

=========================================================

Encoding audio stream to ac3 with the following command:
nice -n 0 ffmpeg -i "/home/david/Movies/swmovie.avi" -vn -ab 224 -ar 48000 -ac 2 -acodec ac3 -y "/home/david/Movies/swmovie_encoded.oLnTii/audio.ac3"

Processing started. Please wait... 


Audio encoding finished successfully.

=========================================================

Encoding video stream with the following commands:
nice -n 0 mplayer -benchmark -nosound -noframedrop -noautosub -vo yuv4mpeg:file="/home/david/Movies/swmovie_encoded.oLnTii/video.yuv" -vf-add scale=720:368 -vf-add expand=720:480 "/home/david/Movies/swmovie.avi"
cat "/home/david/Movies/swmovie_encoded.oLnTii/video.yuv" | yuvfps -r 30000:1001 -v 0 | nice -n 0 mpeg2enc --sequence-length 4300 --nonvideo-bitrate 304 --aspect 3 -f 8 -b 7840 -g 4 -G 11 -D 10 -K hi-res --frame-rate 4 -v 0 --video-norm n --reduction-4x4 2 --reduction-2x2 1 -q 5 -o "/home/david/Movies/swmovie_encoded.oLnTii/video.m2v"

Processing started. Please wait... 



Processing started. Please wait... 
    |||  Encoding video stream: 2086 MB written to video.m2v


=========================================================

Multiplexing audio and video together with the following command:
mplex -V -f 8 -o "/home/david/Movies/swmovie_encoded.mpg" "/home/david/Movies/swmovie_encoded.oLnTii/video.m2v" "/home/david/Movies/swmovie_encoded.oLnTii/audio.ac3"
Multiplexing finished successfully
du: cannot access `/home/david/Movies/swmovie_encoded*.mpg': No such file or directory
Output files:
expr: syntax error
expr: syntax error

=========================================================

    ----------------------------------------
    Final statistics
    ----------------
    tovid 0.28
    File: /home/david/Movies/swmovie_encoded.mpg, 7485 secs DVD NTSC
    Final size:      0 kilobytes
    Target bitrate:  7840 kbits/sec
    Average bitrate:  kbits/sec
    Peak bitrate:     kbits/sec
    Took 03:00:23 to encode on  Genuine Intel(R) CPU           T2300  @ 1.66GHz 999.894 mhz
    -----------------------------------------
    EOF
Statistics written to /home/david/.tovid/stats.tovid
Cleaning up...
removed `/home/david/Movies/swmovie_encoded.oLnTii/video.yuv'
Removing temporary files...
removed `/home/david/Movies/swmovie_encoded.oLnTii/video.m2v'
removed `/home/david/Movies/swmovie_encoded.oLnTii/audio.ac3'
removed `/home/david/Movies/swmovie_encoded.oLnTii/tovid.log'
removed `/home/david/Movies/swmovie_encoded.oLnTii/tovid.scratch'
removed directory: `/home/david/Movies/swmovie_encoded.oLnTii'

=========================================================

Done!

=========================================================

Your encoded video should be in the file(s) /home/david/Movies/swmovie_encoded.mpg.
Thanks for using tovid!

=========================================================

david@david-laptop:~/Movies$

```

There were some errors in there. Does anyone have any idea what the problem with this is? :-k 

Thank,
-Dave

---

### Post by n_hendrick on 2006-10-03
have you tried to run tovid without the  "_" character in the file name....I had a similar problem with tovid with the filename try it with just letters and see if it appears.

---

### Post by dyous87 on 2006-10-03
You mean over here?:
```
-dvd -in swmovie.avi -out swmovie_encoded
```
I didn't use any " ?

---

### Post by n_hendrick on 2006-10-03
I think the _ character is causing a write error in tovid, If I remeber correctly (I haven't used tovid since last year) the filename of the movie should not be variable. Whats command line paramaters are you using? If I'm remmebering correctly you only need to mention the output file once.

---

### Post by dyous87 on 2006-10-03
so are you saying i should put in the command as:
```
-dvd -in swmovie.avi -out swmoviempg
```

---

### Post by n_hendrick on 2006-10-03
yeah...its either the _ or the fact that your not specifing the .mpg in the ouput file name.

---

### Post by n_hendrick on 2006-10-03
make sure you put a . in the output file name

---

### Post by dyous87 on 2006-10-03
aright thanks, I'll try that as soon as I get home from work and tell you how it goes 8)

---

### Post by dyous87 on 2006-10-04
> **n_hendrick said:**
> yeah...its either the _ or the fact that your not specifing the .mpg in the ouput file name.

no it didn't work. i typed it in as: 
```
-dvd -in swmovie.avi -out swmovie.mpg
```

It all went through but after it was completed and said succcesful still no mpg...

---

### Post by n_hendrick on 2006-10-05
I'm not sure whats wrong with it. Like I said I had a problem with tovid running through the process and not spitting out a mpg but I can't exactly remember how I resolved it....sorry I couldn't help you further.

---

### Post by dyous87 on 2006-10-05
hmm I duno, well thanks anyway, I'm sure I'll figure it out eventually.

---

### Post by digbysellers on 2007-04-18
i'm having this problem all of a sudden. 

I have been downloading some youtube videos via vixy.net - four of them have worked fine. Tovid converts them to mpg no problems. 

But out of nowhere I am having the same problem as the OP. I've tried two different videos three times each and they're nowhere to be found, despite the successful output message. 

Are there any alternatives to tovid for a simple command line encoder?

---

