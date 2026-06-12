---
title: "Play RealMedia files in xine without installing RealPlayer!"
date: 2005-10-19
forum: Desktop Environments
---

### Post by blastus on 2005-10-19
I followed the [HOWTO: Win32 Video Codecs](http://ubuntuforums.org/showthread.php?t=70227) guide and downloaded the "essential codecs package." It works great for playing Windows Media files but xine cannot play real media files. I even made sure that my ~/.xine/config file contained these settings...

decoder.external.real_codecs_path:/usr/lib/win32
decoder.external.win32_codecs_path:/usr/lib/win32

...so I decided to install RealPlayer 10...

1. sudo apt-get install libstdc++5
2. chmod +x RealPlayer10GOLD.bin
3. sudo ./RealPlayer10GOLD.bin

...then I could play real media files in RealPlayer but still not in xine. :( xine complains about not being able to load cook.so.6.0 and drv4.so.6.0, which are not part of the essential codecs package or RealPlayer 10!!! :???: 

So based on my experience with SimplyMepis 3.3.1-1, I decided to look inside /usr/lib/win32. Sure enough, it contains cook.so.6.0 and drv4.so.6.0 files. So what I did was copy all the files in my /usr/lib/win32 directory in SimplyMepis over to /usr/lib/win32 in Ubuntu and presto...I can play real media files in xine in Ubuntu! :) 

I've looked around on these forums and can't seem to find any answers. So, one way you can play real media files in xine is to use the SimplyMepis 3.3-1.1 Live CD, grab all the files in the /usr/lib/win32 directory, copy them over to /usr/lib/win32 in Ubuntu, and edit your ~/.xine/config file so that the path to the real codecs is /usr/lib/win32, and it should work without installing RealPlayer 10. :cool:

---

