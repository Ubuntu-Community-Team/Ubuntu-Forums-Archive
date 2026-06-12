---
title: "amarok m4b problem"
date: 2006-06-09
forum: Desktop Environments
---

### Post by prash@linuxitarian on 2006-06-09
Hi,

I have been using kubuntu for about 5 months now, and it is great!

I have one question regarding podcasts on amarok. They are great as long as they are mp3, but the station I have been listening to recently decided to switch to "enhanced podcasts" which I think is in "m4b" format. Now, I know there is a patch @ [http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg07635.html](http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg07635.html).  The amarok site says that the pictures and links (enhanced part of podcast) displays on the "context bar".  However, amarok downloads the podcasts but refuses to play....Could someone please help me as to how to fix this problem? 

Thanks in advance.

---

### Post by FredB on 2006-06-10
[QUOTE=prash@linuxitarian]Hi,

I have been using kubuntu for about 5 months now, and it is great!

I have one question regarding podcasts on amarok. They are great as long as they are mp3, but the station I have been listening to recently decided to switch to "enhanced podcasts" which I think is in "m4b" format. Now, I know there is a patch @ [http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg07635.html](http://www.mail-archive.com/kubuntu-bugs@lists.ubuntu.com/msg07635.html).  The amarok site says that the pictures and links (enhanced part of podcast) displays on the "context bar".  However, amarok downloads the podcasts but refuses to play....Could someone please help me as to how to fix this problem? 

Thanks in advance.[/QUOTE]

m4b ? Never heard of them. Try adding from multiverse gstreamer bad plugins.

Hope it could help ;)

---

### Post by prash@linuxitarian on 2006-06-10
Hey,
  Thanks for the reply. Did you check the link. I tried the following and it still didn't work:

apt-get install gstreamer*
apt-get install xine*

A little extreme but it still refused to play the files. Thanks for the help.

---

### Post by hopstah on 2006-06-15
m4b is encoded with the same codec as m4a files (aac) but for some reason amarok doesn't recognize them as such.  i would love help with this as well, so i don't have to rename all of my m4b files to m4a and lose the audiobook functionality.

---

### Post by TheDeivix on 2008-03-21
I was having trouble playing m4a files too, i googled for a while and found this solution:

```
$ sudo apt-get install faad
```

It worked for me, now i just have to find a way to make amarok display the pictures and links included with the enhanced podcast.

---

