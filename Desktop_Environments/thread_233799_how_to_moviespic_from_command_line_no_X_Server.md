---
title: "how to movies/pic from command line no X Server??"
date: 2006-08-10
forum: Desktop Environments
---

### Post by wakady on 2006-08-10
i want to play movies from command line ( no X server only command line )
i tried mplayer but it always says that error X11 & bla..bla..bla..
i can play audio files but i want to know how to run movies & videos 
Also i want to know how to display pictures/images from command line..
Also how to browse sites from command line..

i know its alot to ask but i want to know how to work all stuff from command line..

if u have any additional info. about games, etc please tell.

AGAIN------> NO X SERVER, NO GDM/KDM, NO GNOME/KDE
                     **JUST COMMAND LINE**

---

### Post by etank on 2006-08-10
I don't know about the others but lynx and links2 are good web browsers that will work from the command line. Although if you hit a site with images then you wont be able to see them. I like links2 more than lynx.

lynx - Text-mode WWW Browser
links2 - Web browser running in both graphics and text mode

```
sudo aptitude install links2
```or```
sudo aptitude install lynx
```

---

### Post by jetblack on 2006-08-10
For the videos, you'll have to use the framebuffer. [This HOWTO](http://devel.reinikainen.net/docs/linux/atitvout.php) talks about setting up the framebuffer and getting mplayer to use it. It also has some tv-out info, but you can ignore that.

---

### Post by wakady on 2006-08-10
ok i'll try both,
but
1- why can't i view images when browse from command line..is there any way around it.
2- i'll try the framebuffer option but is there is any other option?? framebuffer eats a lot of CPU...
3- how can i open pictures from command line

---

### Post by wakady on 2006-08-11
*bump*

---

### Post by llamakc on 2006-08-11
You can view them in ascii if you would like.

---

### Post by Benedolt on 2007-05-24
You can view images on your harddisk from command line using zgv.
```
sudo apt-get install zgv
```
Works pretty well.

Oh, and the mplayer framebuffer howto is [here]("http://devel.reinikainen.net/content/view/38/40/").

---

### Post by Indras on 2007-05-24
You can play videos from command line using mplayer with aalib.  Once you have it properly installed, do something like this:

mplayer -vo aa /path/to/video/file

To add color, change "aa" to "caca."  You may also want to add "-quiet" to get rid of the text and make it look right.

---

