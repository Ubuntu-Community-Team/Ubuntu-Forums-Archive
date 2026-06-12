---
title: "Metacity doesn't start ?!?!"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by pacut on 2007-05-08
Hello there...
i am not very expert with Linux and Ubuntu, so I couldn't find any solution to my issue thrugh all the posts here.

The fact is: when I start my Ubuntu (7.04) there is no window manager at all (windows don't have title bar, buttons, etc) and I found that "there is no window manager" running. The temporary solution I found is to open a root terminal an launch "metacity".

Question for you:
1 - what the hell can be ?
2 - is it there any final solution to have metacity running each time I log on ?

Thanks !
Paolo

---

### Post by Sunflower1970 on 2007-05-08
I had this happen in both Ubuntu & Xubuntu. What I did was add, in Ubuntu, to the start up menu metacity. Then all worked out fine. (In Xubuntu, I added xfwm4 to the start up menu.)

I've read some other posts and some have said to delete a hidden file in your home folder. .gnome2/sessions. Read this post: [http://ubuntuforums.org/showthread.php?t=432732&highlight=.gnome2%2Fsessions](http://ubuntuforums.org/showthread.php?t=432732&highlight=.gnome2%2Fsessions). Heree's another post on it: [http://ubuntuforums.org/showthread.php?t=436144&highlight=.gnome2%2Fsessions](http://ubuntuforums.org/showthread.php?t=436144&highlight=.gnome2%2Fsessions)

hope that helps :)

---

