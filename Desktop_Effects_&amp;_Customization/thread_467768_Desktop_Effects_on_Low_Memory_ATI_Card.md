---
title: "Desktop Effects on Low Memory ATI Card"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by ff8jake on 2007-06-08
After hours and hours of searching through numerous posts on how to get this working, I have finally found the answer, and I wanted to post it up in hopes that maybe it'll help someone else.

I just installed Ubuntu and seen the "Desktop Effects" setting. Me, being a graphics whore, had to have this working. When I enabled it on my laptop which has a native res of 1400x1050 it worked, but the right quarter of the screen was really messed up, and if you stretch windows too big the window decorations totally turn white and disappear.

After looking, I discovered that my card only supported a 1024x1024 texture buffer size. It can be increased using the following code in an /etc/drirc XML file (this was for an ATI Radeon driver, not sure what edits need to be made for other users): ```
<driconf>
<device screen="0" driver="r200">
<application name="all">
<option name="allow_large_textures" value="2" />
</application>
</device>
</driconf>
```This works, but any window above the 1024x1024 res will respond EXTREMELY slowly. Most people that tried this solution simply gave up on desktop effects because of the lag.

However, you can increase the texture buffer size (to 2048x2048 in my case) by simply setting the color depth from 24 bit to 16 bit. The quality difference is hardly seen and everything runs extremely fast.

I hope this helps someone, it's been extremely frustrating to have such an awesome feature and not be able to take advantage of it, or at least figure out exactly why it doesn't work.

Cheers

---

