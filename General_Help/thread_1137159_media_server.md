---
title: "media server"
date: 2009-04-25
forum: General Help
---

### Post by linux newb on 2009-04-25
hi all just wondering how i can setup a media server on 9.04, previousely i was using ushare, but now i try to get the source to set up ushare [http://netou.co.uk/](http://netou.co.uk/), and it says that its no longer supported and the source link isnt their at all anymore. does anyone no if i can get the source elsewhere? or of some other media server that i can share with xbox, and ps3?

---

### Post by codeseer on 2009-04-25
How about this: [http://en.jinzora.com/]("http://en.jinzora.com/")

Here's a guide to go with it: [http://rubbervir.us/projects/ubuntu_media_server/]("http://rubbervir.us/projects/ubuntu_media_server/")

Edit:

Also see this: [http://en.jinzorahelp.com/documentation]("http://en.jinzorahelp.com/documentation")

---

### Post by linux newb on 2009-04-25
> **codeseer said:**
> How about this: [http://en.jinzora.com/]("http://en.jinzora.com/")

Here's a guide to go with it: [http://rubbervir.us/projects/ubuntu_media_server/]("http://rubbervir.us/projects/ubuntu_media_server/")

Edit:

Also see this: [http://en.jinzorahelp.com/documentation]("http://en.jinzorahelp.com/documentation")thanks for the post, but when i try to unpackage jz280.tar.gz ite says

tar: jz275.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

is the command a little different for 9.04 or just a typo that i am missing?
i downloaded it to he same spot as i do everything else when im dealing with a tar.gz file. CONFUSED

---

### Post by codeseer on 2009-04-25
You should be able to open it right up with the Archive Manager. If not, then it may be corrupt. In that case, you should delete it and redownload it.

Edit:

I checked the download and it worked fine for me.

Here's the link: [http://downloads.sourceforge.net/jinzora/jz280.tar.gz]("http://downloads.sourceforge.net/jinzora/jz280.tar.gz")

---

### Post by Mike'sHardLinux on 2009-04-25
Linux Newb, you're following that tutorial too literally. You downloaded a newer version of Jinzora ( 2.8 ) than what is in the tutorial ( 2.75 ). You need to modify your command to reflect that difference.

---

### Post by mb_webguy on 2009-04-25
You could also try MediaTomb, which is in the repos.

---

### Post by linux newb on 2009-04-26
> **Mike'sHardLinux said:**
> Linux Newb, you're following that tutorial too literally. You downloaded a newer version of Jinzora ( 2.8 ) than what is in the tutorial ( 2.75 ). You need to modify your command to reflect that difference.

ah yes I shouldve mentioned, i tried with modifying the command to 280 but, i realized something fishy. when i downloaded the tar.bz2 package for firefox, i tried sudo tar xvzf firefox-3.0.9.tar.bz2
and came up with the same message. im thinking i might need to somehow alter my command a bit more because im using the new 9.04 kubuntu release. but am not entirely sure this is just theory, therefore i am but, a linux newb i just went sudo apt-get install firefox to install that. but really stumped on this meia server right now over somehting simple.

---

### Post by codeseer on 2009-04-26
> **linux newb said:**
> ah yes I shouldve mentioned, i tried with modifying the command to 280 but, i realized something fishy. when i downloaded the tar.bz2 package for firefox, i tried sudo tar xvzf firefox-3.0.9.tar.bz2
and came up with the same message. im thinking i might need to somehow alter my command a bit more because im using the new 9.04 kubuntu release. but am not entirely sure this is just theory, therefore i am but, a linux newb i just went sudo apt-get install firefox to install that. but really stumped on this meia server right now over somehting simple.

Xubuntu doesn't have the Archive Manager?

```
:~$ whereis file-roller
file-roller: /usr/bin/file-roller /usr/lib/file-roller /usr/lib64/file-roller /usr/share/file-roller /usr/share/man/man1/file-roller.1.gz

```

---

