---
title: "ffmpeg installation!"
date: 2009-03-18
forum: General Help
---

### Post by a.driaan on 2009-03-18
Hi there,

am trying to install ffmpeg on my ubuntu 8.10, everything went ok and I've test it after the installation and it works perfectly, BUT, after that whenever I type ffmpeg I got this error:

ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context

I don't know what the problem is, ffmpeg worked fine in the first time and I didn't change anything after that!!

I've tried to search the forums but I didn't find any solution, I hope you can help me guys, my graduation project based on multimedia conversion :s

Thanks a lot in advance :)

---

### Post by kryptikos on 2009-03-18
This thread might help you:

[http://ubuntuforums.org/showthread.php?t=1082698]("http://ubuntuforums.org/showthread.php?t=1082698")

---

### Post by a.driaan on 2009-03-18
kryptikos

Thanks for your replay.

I've seen that thread before but they advised to remove --enable-shared, but I need it to use ffmpeg-php!

any other suggestions?

---

### Post by mb_webguy on 2009-03-18
You shouldn't have any problem installing ffmpeg from the official repositories, but if you want to enable support for AAC and are feeling a bit brave, you can try compiling ffmpeg from source.  Check the link in my signature for details.

---

### Post by a.driaan on 2009-03-18
mb_webguy

at first .. thanks,

am learning here on my localhost how to compile ffmpeg from source to support all the formats and to be able to install ffmpeg on any server ..

I believe that I've passed by the thread in your signature and it didn't work for me! I'll try it again.

I've installed ffmpeg many times on different machines and nothing worked completely "except on Mac OS X" :s

I've followed this tutorial:
[http://www.youtube.com/watch?v=u0QTR-Iljm0&feature=related](http://www.youtube.com/watch?v=u0QTR-Iljm0&feature=related)

and as I wrote in my post .. it worked but whenever I install anything after it .. am getting the same error:

ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context

---

### Post by a.driaan on 2009-03-19
It didn't work :(

am getting the same problem :s

---

### Post by FakeOutdoorsman on 2009-03-19
Everything is in the repository if you don't want to compile it yourself:
```
sudo apt-get install php5-ffmpeg libavcodec-unstripped-51
```
The libavcodec-unstripped-51 package allows restricted encoders and I believe php5-ffmpeg package is ffmpeg-php.

---

### Post by FakeOutdoorsman on 2009-03-19
> **a.driaan said:**
> ...
after that whenever I type ffmpeg I got this error:

ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context

I am unable to duplicate your error.  I installed SVN FFmpeg following this tutorial on a vanilla Ubuntu installation:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

When I reached step 5 (Install FFmpeg) I added --enable-shared to the FFmpeg configuration line.  After I installed FFmpeg with checkinstall I updated the links to the new shared libraries with:
```
sudo ldconfig
```
FFmpeg worked fine for me after these steps and I was able to decode and encode with no errors.

---

