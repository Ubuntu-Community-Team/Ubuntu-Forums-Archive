---
title: "No Sound"
date: 2009-02-10
forum: General Help
---

### Post by triplemaya on 2009-02-10
I have read the posts, and gone through some how tos without success.
I installed ubuntu 8.10 in a new computer, and it did not recognise the onboard sound, no biggie. I put in the old Creative SB Live I know it will recognise. But No, Too Late! This is not windows ( sob, for once ) and nothing new happens. I commence the process of getting it to work, as suggested on this thread
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and 
lspci -v
shows up the Creative sound card "showing that Ubuntu is detecting the presence of your soundcard, but the drivers are not installed/running."

I went to the website as suggested on this thread
namely
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)
and all I get is a big bare page with
Index of /alsa-doc
at the top and a directory of stuff I do not begin to comprehend.

Can someone please tell me an easy way.
I know this all works with an install ( bang head, sob, why could I not have put in the card originally ) but I did so much other setting up before I checked the sound, so although all I have to do is reinstall, it is time expensive already. It all works fine on the live cd.

Surely if it works with the live cd there is something simple I can do to make it work with the install.

five minutes later:
It just works!? Turned off the live cd and rebooted an all ok.

---

### Post by gettinoriginal on 2009-02-10
Not sure which "How To" you used, so just passing these on, hope they help:
Sound Issues
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by triplemaya on 2009-02-10
Many thanks for your post.

It solved itself. On the first reboot after installing the card the drivers did not install although the card was recognised. On the next reboot the drivers were installed ok and everything worked.

---

