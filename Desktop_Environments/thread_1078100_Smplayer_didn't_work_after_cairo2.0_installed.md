---
title: "Smplayer didn't work after cairo2.0 installed"
date: 2009-02-23
forum: Desktop Environments
---

### Post by youxiang95 on 2009-02-23
Smplayer didn't work well after I installed the cairo-dock 2.0 beta. I can open the vedio file encoding in "RMVB" or "AVI" and played well before the cairo 2.0 install(I installed cairo 1.6.3.1 before cairo 2.0). Now I can't see the picture in the smplayer but the audio.If I opened the files with Mplayer, I could see pictrue,and If I used fullscreen ,Mplayer would exit. So anyone can tell me how to deal with it? Please send to my eMail [email]107944616@qq.com[/email]. Thanks a lot!!!!!

---

### Post by fabounet on 2009-02-23
known qt4 bug
it has been discussed on cairo-dock's forum

---

### Post by youxiang95 on 2009-02-23
> **fabounet said:**
> known qt4 bug
it has been discussed on cairo-dock's forum

Where is the forum? And is there any body had resolved the problem?

---

### Post by rvm4000 on 2009-02-23
Maybe this?

[http://www.cairo-dock.org/bg_topic.php?t=2201](http://www.cairo-dock.org/bg_topic.php?t=2201)

They propose this workaround:
```

export XLIB_SKIP_ARGB_VISUALS=1 
smplayer &

```

---

### Post by youxiang95 on 2009-02-24
> **rvm4000 said:**
> Maybe this?

[http://www.cairo-dock.org/bg_topic.php?t=2201](http://www.cairo-dock.org/bg_topic.php?t=2201)

They propose this workaround:
```

export XLIB_SKIP_ARGB_VISUALS=1 
smplayer &

```


Oh yeah!!!!!It works for me !  Thank you very much !!

---

### Post by rldev on 2009-07-31
This works for me, but it is kind of annoying to have to eneter that every time you want to use a program.
I tried editing /usr/share/applications/smplayer.desktop and changing the exec command to something like:

Exec=bash -c "export XLIB_SKIP_ARGB_VISUALS=1 && smplayer %f"

But smplayer will not launch after this.

---

### Post by Zorael on 2009-08-01
One dirty way would be to hijack the smplayer executable. I do this with several apps, mostly just to add the ampersand (**&**) to get them to start as child processes when launched from a terminal. And also to disable fsyncing in some apps that seem particularly trigger-happy about that (Firefox, Quassel).

Rename **/usr/bin/smplayer** to **/usr/bin/smplayer.real** (which requires superuser permissions), and create a new **/usr/bin/smplayer** that looks like the following.
```
#!/bin/bash

export XLIB_SKIP_ARGB_VISUALS=1 
smplayer**.real** $@ &
```
Don't forget to set it to executable. This has drawbacks in that you'd have to redo it at every upgrade of smplayer (as it'll overwrite the **/usr/bin/smplayer** file with the new version), and you'll leave garbage in the form of **/usr/bin/smplayer_.real_** that the package manager doesn't know of, and won't remove if you uninstall the app.


Yet another way would be to hijack it via **/usr/_local_/bin/smplayer**. **/usr/_local_/bin** is per default placed earlier in the PATH variable, so executables there override those in **/usr/bin/**. If the .desktop file (application link) specifically points to **/usr/bin/smplayer**, they would have to be rewritten to point to the new script instead. I *think* that if they simply point to **smplayer**, the file manager/whatever will try to resolve its location via PATH, but incase that particular app is written to look in **/usr/bin/** if no explicit location is supplied, you'd have to rewrite the .desktop link to point to the full location.
```

#!/bin/bash

export XLIB_SKIP_ARGB_VISUALS=1 
**/usr/bin/**smplayer $@ &
```
As rldev said, the .desktop file is at **/usr/share/applications/smplayer.desktop**, so hack away.

---

### Post by mihaicj on 2009-10-01
> Rename **/usr/bin/smplayer** to **/usr/bin/smplayer.real** (which requires superuser permissions), and create a new **/usr/bin/smplayer** that looks like the following.
```
#!/bin/bash

export XLIB_SKIP_ARGB_VISUALS=1 
smplayer**.real** $@ &
```
Don't forget to set it to executable. This has drawbacks in that you'd have to redo it at every upgrade of smplayer (as it'll overwrite the **/usr/bin/smplayer** file with the new version), and you'll leave garbage in the form of **/usr/bin/smplayer_.real_** that the package manager doesn't know of, and won't remove if you uninstall the app.

I did this but the movie doesn't play. SMplayer starts but after a short while it gives me an error saying Mplayer has crashed.

---

### Post by Lockheed on 2009-11-15
This is the proper solution:
```
sudo bash -c "cat > /usr/bin/smplayer.helper" <<EOF
export XLIB_SKIP_ARGB_VISUALS=1
exec smplayer.real "\$@"
EOF

sudo chmod 755 /usr/bin/smplayer.helper
sudo mv /usr/bin/smplayer{,.real}
sudo ln -sf smplayer.helper /usr/bin/smplayer
```

---

### Post by gudrade on 2010-01-01
Have same problem with avidemux. Someone managed to solve it?

---

### Post by harryscode on 2010-10-24
> **Lockheed said:**
> This is the proper solution:
```
sudo bash -c "cat > /usr/bin/smplayer.helper" <<EOF
export XLIB_SKIP_ARGB_VISUALS=1
exec smplayer.real "\$@"
EOF

sudo chmod 755 /usr/bin/smplayer.helper
sudo mv /usr/bin/smplayer{,.real}
sudo ln -sf smplayer.helper /usr/bin/smplayer
```

Thanks dude.. works perfect
:guitar:

---

