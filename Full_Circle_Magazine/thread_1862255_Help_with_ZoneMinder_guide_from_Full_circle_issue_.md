---
title: "Help with ZoneMinder guide from Full circle issue 52"
date: 2011-10-16
forum: Full Circle Magazine
---

### Post by tenroot on 2011-10-16
Hi all,

I've been following the Zone Minder guide from Full circle issue 52, when its come to the part you command this line: mjpg_streamer -i “input_uvc.so -r 320x240 -f 6” -o “output_http.so -p 8080” I have this error : mjpg_streamer: unrecognized option '-r' The only thing I've done different to this guide is my is a server install I copied and installed the .deb file.

Many Thanks Rich

---

### Post by ronniet on 2011-10-18
> **tenroot said:**
> Hi all,

I've been following the Zone Minder guide from Full circle issue 52, when its come to the part you command this line: mjpg_streamer -i “input_uvc.so -r 320x240 -f 6” -o “output_http.so -p 8080” I have this error : mjpg_streamer: unrecognized option '-r' The only thing I've done different to this guide is my is a server install I copied and installed the .deb file.

Many Thanks Rich

Hmm, very odd. I've no idea why you would get that error message. My article is a mish-mash of several articles and videos. The mjpg-streamer command I used is also mentioned on the ZoneMinder wiki page: [http://www.zoneminder.com/wiki/index.php/Uvc](http://www.zoneminder.com/wiki/index.php/Uvc)

The -r option is (I think) for resolution, to tell mjpg-streamer what resolution to use.

Sorry I can't be of more help. :(

---

