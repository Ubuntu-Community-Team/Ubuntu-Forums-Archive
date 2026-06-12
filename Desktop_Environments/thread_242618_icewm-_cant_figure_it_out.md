---
title: "icewm- cant figure it out"
date: 2006-08-23
forum: Desktop Environments
---

### Post by leb3000 on 2006-08-23
hey guys,

im trying to install the [acqua]("http://www.kde-look.org/content/show.php?content=153") theme in kubuntu.

OK so i install it right by running script. i then have to "Select Window Decoration and then IceWM in the list" in the kde-control centre.

I couldnt find IceWM in the list so i apt-get it. It downloaded and installed... then tried again but it still aint in the list...

Am I doing something wrong???

---

### Post by silverback011 on 2006-09-23
I know this is a late reply.  I hope not too late.

IceWM is a window manager like KDE or Gnome, but much more light weight.  I think you installed the IceWM window manager instead of the theme you wanted.

I am not familiar with the theme aqua.  I use IceWM as my window manager.

I hope I have not misunderstood your post.  Also I hope I have been of some help.

---

### Post by aysiu on 2006-09-23
That's an IceWM theme, for sure. I don't know why it's at [http://www.kde-look.org](http://www.kde-look.org)

If you want an Aqua-looking theme in Kubuntu, you're far better off with Baghira.

**Step 1**: Enable extra repositories by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Paste these commands in the Konsole terminal: ```
sudo aptitude update
sudo aptitude install kwin-baghira
kcontrol
``` You should see Baghira listed in the Window Decoration and Style sections of Appearances and Themes.

---

