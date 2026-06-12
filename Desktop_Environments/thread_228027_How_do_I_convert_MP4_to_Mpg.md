---
title: "How do I convert MP4 to Mpg?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by mister_p_1998 on 2006-08-02
Got some nice Vids in MP4 I want to put on VCD, cant figure how to convert with ffmpeg or tovid.
Can you help guys?

---

### Post by bensexson on 2006-08-02
I find the easiest way is to use the transcoding wizard in VLC.  I convert the opposite way all the time.

---

### Post by mister_p_1998 on 2006-08-02
No tried that, picture distorted in VLC

---

### Post by cvmostert on 2006-11-13
Hi, i also had problems...

i used mencoder and it worked...

> mencoder 13112006031.mp4 -ovc lavc -vf scale=352:288 -oac lavc -o outpotmenc.mpg


hope this helps... play around with it...

---

### Post by andoty_jazz on 2007-08-31
Ciao!

Works like a charm... Thank you so very much.

I just have one question. Is it really normal that the conversion will took some time?

I converted a 100mb + of file size .mp4 and it does took some time. And I am to convert 20 of of them... Whew....

Are there any commands that will speed up the conversion?

Thanks in advance, but the conversion does have an excellent output. Thanks really for the help.

---

