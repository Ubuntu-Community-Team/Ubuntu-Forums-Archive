---
title: "Unable to Download Streaming Video on Ubuntu"
date: 2011-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-01-02
Hello,


Hope everyone had a Happy New Year!

I've been trying to figure out how to recording streaming video from 

[http://hindi.moneycontrol.com/tv/](http://hindi.moneycontrol.com/tv/)


since a family friend was in a contest that has been broadcast on this station.


Below are the steps taken

1. Download Firefox browser

2. Install Video DownloadHelper at 

[https://addons.mozilla.org/en-US/firefox/addon/3006/](https://addons.mozilla.org/en-US/firefox/addon/3006/)

3. At 7:30 AM go to [http://hindi.moneycontrol.com/tv/](http://hindi.moneycontrol.com/tv/)

4. Start recording the video by saving it to Desktop. However, the Downloads pop-up only says "Starting"

5. At 8:00 AM when the program is finished, shut down the Firefox browser. Now the Download says it will take 9 hours to download something that is 1 GB (around 20 KB per second). However my usual download speed 7 MB per second.

6. While in the middle of download I am able to open the .flv file using VLC media player ([http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)) 

7. When I open the .flv file, it shows broadcast from 8:02 AM, rather than 7:30 AM


What am I doing wrong? I have been attempting to download the streaming media of this show yesterday morning, and today morning. I only have two more chances left, as the show will repeat again next Saturday and Sunday.

Will appreciate any guidance.

Thank you

---

### Post by perspectoff on 2011-01-02
Video Download helper generally will not download if you still have the original browser window open. Close the original window and then the Video DownloadHelper will start to download.

-------------------------------------------------------

For .flv files, there is also another method.

While watching the Flash video in the original browser window (but while keeping the browser Window open) check the /tmp folder.

You should see a file there named something like

 AxRtBwXt.flv

or something similar. It should be increasing in size as you watch the video. This is the buffered Flash video. When it has been downloaded completely (but before you close the browser window), copy it to any folder in your /home directory and rename it to something you like, such as MyVideo.flv.

You can then watch that copy from VLC.

---

### Post by lisati on 2011-01-02
What you do on your computer is your business. Just be aware that some sites that host video clips don't appreciate people downloading clips for later use. Youtube is one example of this - see the link in my sig.

---

### Post by perspectoff on 2011-01-02
> **lisati said:**
> What you do on your computer is your business. Just be aware that some sites that host video clips don't appreciate people downloading clips for later use. Youtube is one example of this - see the link in my sig.

The same goes for images, icons, and text that people routinely download and copy from the Internet, not just video. Some people even copyright their help manuals. 

Trademarks, URLs, and unique form are also legally protected in many countries, but are copied worldwide nevertheless. I'm sure the Ubuntu Forums moderators do not advocate any illegal activity, but neither is it an arm of the DCMA enforcement regime. 

There are plenty of completely legal uses and methods of sharing and content propagation. Ubuntu itself is distributed over Torrent networks, and there are many, many Flash videos that are freely available without copyright restriction. 

Awareness of licensing, the GPL and Creative Commons licenses, and Richard Stallman's visionary efforts starting many years ago are important to everyone interested in this topic.

---

### Post by RSASKA on 2011-01-05
@ perspectoff: I will try this out as soon as possible. I simply want to record this program.

@ lisati, @ perspectof: You bring up a very good point about copyright and the Internet. In this case, this program is on CNBC (for audiences in India), and will be viewed by my close family.

Will keep you updated...

---

