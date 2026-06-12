---
title: "Camorama, error when uploading image on FTP"
date: 2006-10-05
forum: Desktop Environments
---

### Post by wty on 2006-10-05
Ok, so heres the problem. I recently received a webcam from a norwegian computer paper. And I installed it and it works well. But it seems to be a problem uploading the images on to my FTP, and this bugs me quite a bit. I should mention that I can save the images on to my disk without any problems. And I can also upload the images on the FTP unless I tag on the "append time to filename". You might think thats not a problem, but if I don't have it on, the images will just get replaced. 

So heres the error I get in terminal:
"(camorama:8452): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()"

And heres the error I get in GUI:
"An error has occured opening ftp://ip/folder/webcam/filename-and-many-odd-characters.png."

I have searched for hours and hours, finding nothing. I have also tried to install Camorama by source, the latest edition 0.18 (Ubuntu only got 0.17). But then I get this error:
Requested 'gtk+-2.0 >= 2.10' but version of GTK+ is 2.8.20

Thank you for time, and I hope we can find a solution to this problem. 

-wty

---

