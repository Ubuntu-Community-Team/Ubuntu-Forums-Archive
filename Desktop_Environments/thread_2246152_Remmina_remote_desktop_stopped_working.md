---
title: "Remmina remote desktop stopped working"
date: 2014-09-28
forum: Desktop Environments
---

### Post by derekcentrico on 2014-09-28
It worked great for ages on my 12.04 server.  It abruptly stopped a month ago and I've yet to find a cure.

I disabled the requirement for encryption on both my server and laptop (which connects to it).  The laptop runs 14.04.

Using the Reminna remote desktop application, I sign into the server with no errors of incorrect credentials.  Then, it's a blank gray screen on the desktop side.  Nothing occurs on the server side.

Any help is greatly appreciated.

Here's .xsession-errors in case anyone has ideas:
28/09/2014 06:05:05 PM [IPv4] Got connection from client DerekLaptopU.hsd1.fl.comcast.net
28/09/2014 06:05:05 PM   other clients:
28/09/2014 06:05:06 PM Client Protocol Version 3.7
28/09/2014 06:05:06 PM Advertising security type 18
28/09/2014 06:05:06 PM Advertising security type 2
28/09/2014 06:05:06 PM Client returned security type 18
28/09/2014 06:05:07 PM Advertising authentication type 2
28/09/2014 06:05:08 PM Client returned authentication type 2
28/09/2014 06:05:08 PM Pixel format for client DerekLaptopU.hsd1.fl.comcast.net:
28/09/2014 06:05:08 PM   32 bpp, depth 24, little endian
28/09/2014 06:05:08 PM   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
28/09/2014 06:05:08 PM no translation needed
28/09/2014 06:05:08 PM rfbProcessClientNormalMessage: ignoring unknown encoding type -131072
28/09/2014 06:05:08 PM Enabling NewFBSize protocol extension for client DerekLaptopU.hsd1.fl.comcast.net
28/09/2014 06:05:08 PM rfbProcessClientNormalMessage: ignoring unknown encoding type -131071
28/09/2014 06:05:08 PM rfbProcessClientNormalMessage: ignoring unknown encoding type -131070
28/09/2014 06:05:08 PM rfbProcessClientNormalMessage: ignoring unknown encoding type -131069
28/09/2014 06:05:08 PM rfbProcessClientNormalMessage: ignoring unknown encoding type -309
28/09/2014 06:05:08 PM Enabling cursor position and shape (rich encoding) updates for client DerekLaptopU.hsd1.fl.comcast.net
28/09/2014 06:05:14 PM rfbProcessClientNormalMessage: read: Resource temporarily unavailable
28/09/2014 06:05:14 PM Client DerekLaptopU.hsd1.fl.comcast.net gone
28/09/2014 06:05:14 PM Statistics:
28/09/2014 06:05:14 PM   framebuffer updates 14, rectangles 14, bytes 10220108
28/09/2014 06:05:14 PM     hextile rectangles 14, bytes 10220108
28/09/2014 06:05:14 PM   raw bytes equivalent 21532216, compression ratio 2.106848

---

