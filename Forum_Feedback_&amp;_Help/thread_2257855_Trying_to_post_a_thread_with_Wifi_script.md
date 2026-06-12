---
title: "Trying to post a thread with Wifi script"
date: 2014-12-23
forum: Forum Feedback &amp; Help
---

### Post by ghormax on 2014-12-23
After pasting the script into the message, I get the following error:
> 
Errors
The following errors occurred with your submission

    You have included a total of 17 images in your message. The maximum number that you may include is 8. Please correct the problem and then continue again.

    Images include use of smilies, the BB code [img] tag, and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.


Can you please fix this so I can post the message?

---

### Post by lisati on 2014-12-23
*Thread moved to **Forum Feedback & Help**.*

17 images? It might be a bit much for people to digest all in one go.

---

### Post by ghormax on 2014-12-23
not a single image included, just the text of the script

---

### Post by ghormax on 2014-12-23
I think it's because the script gives many like these: 

> [/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

[/etc/modprobe.d/rtl8723ae.conf]
options rtl8723ae swenc=1 ips=0

---

### Post by lisati on 2014-12-23
Your thread has been moved to a section for asking for help using the forums. In that context, my advice is to start a support request in an appropriate section, but without so many images.

---

### Post by ghormax on 2014-12-23
I think your script for detecting images is broken. There were no images included at all. I think I will have to split the printout of the WLAN script to multiple messages if you will not change this!

---

### Post by lisati on 2014-12-23
Have you tried using the "manage attachments" button below the area where you type?

---

### Post by ghormax on 2014-12-23
Oh I did not see that part. It could be made clearer. Also, I think auto-smileys could be disabled.

---

### Post by varunendra on 2014-12-23
Simple case of not using 'Code' tags, which causes the code parts to turn into smileys.

Smileys=images.

---

### Post by lisati on 2014-12-23
I have just looked at your [other thread]("http://ubuntuforums.org/showthread.php?t=2257862"). Try using [noparse]```
 and 
``` instead of >  and .[/noparse]. That way the formatting of your messages will be preserved, and you won't get those annoying smileys.

This thread now closed.

---

