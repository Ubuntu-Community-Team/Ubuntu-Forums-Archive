---
title: "Thunar... enable thumbnails?"
date: 2012-06-15
forum: Desktop Environments
---

### Post by valmorel on 2012-06-15
How can I enable thumbnails in Thunar please? Xubuntu 12.04

---

### Post by Toz on 2012-06-15
Do you have tumbler installed? It is used to generate thumbnails in thunar. You might also want to install ffmpegthumbnailer for video thumbnails.

---

### Post by Rodney9 on 2012-06-15
In Thunar preferences set 'Show Thumbnail', see screenshot

Rodney

---

### Post by black veils on 2012-06-15
in case you mean desktop thumbnails:

*right-click the desktop  >>  **Desktop Settings**  >>  **Icons** tab  >>  **Show thumbnails***

---

### Post by valmorel on 2012-06-17
> **Toz said:**
> Do you have tumbler installed? It is used to generate thumbnails in thunar. You might also want to install ffmpegthumbnailer for video thumbnails.

Yes, tumbler is installed.

---

### Post by valmorel on 2012-06-17
> **Rodney9 said:**
> In Thunar preferences set 'Show Thumbnail', see screenshot

Rodney

Had done that during setup thanks. No thumbnails though.

---

### Post by valmorel on 2012-06-17
> **black veils said:**
> in case you mean desktop thumbnails:

*right-click the desktop  >>  **Desktop Settings**  >>  **Icons** tab  >>  **Show thumbnails***


Had also done that during setup. No thumbnails though.

---

### Post by Toz on 2012-06-17
Try resetting your thumbnails cache by deleting the folder ~/.thumbnails and logging out and back in again?

---

### Post by valmorel on 2012-06-17
> **Toz said:**
> Try resetting your thumbnails cache by deleting the folder ~/.thumbnails and logging out and back in again?

That was the charm thanks. Now fixed, but, wierd, right?

---

### Post by Toz on 2012-06-17
It is interesting. Something must have been corrupt there. Can you please mark this thread as Solved from the Thread Tools link above so that someone else might benefit from the fix?

---

### Post by valmorel on 2012-06-21
> **Toz said:**
> It is interesting. Something must have been corrupt there. Can you please mark this thread as Solved from the Thread Tools link above so that someone else might benefit from the fix?

Done. Appologies for delay.

---

### Post by silentcreek on 2012-08-11
Hi,

I have the same problem, but the steps in this thread didn't solve the issue for me.
I'm running Xubuntu 12.04 and I can't get the thumbnails workin.

Here's a list of thumbnail related packages that are installed on my system:
tumbler
libtumbler-1-0
tumbler-common
tumbler-plugins-extra
ffmpegthumbnailer
libffmpegthumbnailer4

I also deleted the .thumbnails folder in my homes/USER folder several times to recreate the thumbnails, but it didn't help. The thumbnails in thunar preferences are enabled, of course. Thumbnails for images are shown, but not for videos.

Any suggestions on how to solve this?

Thanks!

---

### Post by Toz on 2012-08-11
> **silentcreek said:**
> Hi,

I have the same problem, but the steps in this thread didn't solve the issue for me.
I'm running Xubuntu 12.04 and I can't get the thumbnails workin.

Here's a list of thumbnail related packages that are installed on my system:
tumbler
libtumbler-1-0
tumbler-common
tumbler-plugins-extra
ffmpegthumbnailer
libffmpegthumbnailer4

I also deleted the .thumbnails folder in my homes/USER folder several times to recreate the thumbnails, but it didn't help. The thumbnails in thunar preferences are enabled, of course. Thumbnails for images are shown, but not for videos.

Any suggestions on how to solve this?

Thanks!

Do you also have the following packages installed?
- gstreamer0.10-ffmpeg
- gstreamer0.10-plugins-good

---

### Post by silentcreek on 2012-08-13
> **Toz said:**
> Do you also have the following packages installed?
- gstreamer0.10-ffmpeg
- gstreamer0.10-plugins-good

Thanks, this was the right hint! The second package was installed, but the first wasn't. I just don't understand why the packages that you have to install to get video thumbnails change with every release... But anyway, it works, now :)

---

