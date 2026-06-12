---
title: "Framebuffer Issue 8.04"
date: 2008-12-19
forum: General Help
---

### Post by chessiv on 2008-12-19
I was running 8.10 and had a number of issues so I switched to 8.04 and no longer have those issue.  The only problem is I need to setup a frame buffer.  In 8.1 I used vga=0x311 (640x480x16) and it worked fine.  8.04 doesn't recognize that mode.  In grub I went to the console and ran vbeprobe and found the mode with the number 0x111.  I tested it with testvbe and it worked great.  When I try to boot with it I don't get a /dev/fb0 (or any framebuffer for that matter.)  Any ideas?

Thanks

---

