---
title: "Enlightenment and Polypaudio"
date: 2005-07-20
forum: Desktop Environments
---

### Post by pizzach on 2005-07-20
Hello.

I've been toying with Hoary for a while now. I love e16 so much better than gnome ore kde. Though I was trying to solve some audio issues though since esd doesn't work well with my sound card in my Asus Z71V. I had upgraded my Alsa driver which had fixed the problem for gnome but for enlightenment my luck was a little more shacky. Specifically, Rhythbox was causing me the trouble. Whenever I typed "polypaudio" into the terminal after installing it through synaptic, Rhythmbox worked and so did the sound effects of e16. But I was hoping to autimate the loading so it is less ugly than keeping a terminal window open with it and having to load it manually each time.

Unfortunately...6 hours later and unable to log into gnome now, I am still stumped. In what document am I supposed to put polyaudio to have it load like it did in the terminal!? Am I missing something stupid? I tried stuffing it all over the place.....xinitrc.....xsession...all over the etc directory....little bit of gnoming etc etc.
 :mad: 
Life would be so much easier if I would have just stayed happy with gnome I wonder. But it wouldn't have turned out so interesting  :-P

---

### Post by pizzach on 2005-07-20
Figured it out!  The problem was one and the same.  I accidently uncommented the cli option in the default file of polypaudio.  I knew staying up all night would do it.  :smile:

---

### Post by songochain on 2005-07-26
Hi dude, i've a problem with e17 and polyaudio. I cant get fullscreen into e17  using mplayer but in gnome i havent this problem. I know it's polyaudio because before i could get fullscreen but i've installed polyaudio to can hear multiple sounds. 
Any idea?
thanks

---

### Post by charlieg on 2005-07-26
Why don't you guys try dmix (alsa config) to get multiple concurrent sounds for your desktop:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by songochain on 2005-07-26
[QUOTE=charlieg]Why don't you guys try dmix (alsa config) to get multiple concurrent sounds for your desktop:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)[/QUOTE]
I've followed this post to get multiple sounds. In gnome it works perfectly with mplayer but in e17 not... so there's something wrong

---

### Post by pizzach on 2005-07-30
Meh.  I've gone back and forth with success.  I'm back with gnome for now until there is better support for my computer.  (it bugs the heck out of me how synaptic downgrades my alsa driver to one that doesn't work with my system)

---

### Post by pizzach on 2005-07-30
[QUOTE=songochain]Hi dude, i've a problem with e17 and polyaudio. I cant get fullscreen into e17  using mplayer but in gnome i havent this problem. I know it's polyaudio because before i could get fullscreen but i've installed polyaudio to can hear multiple sounds. 
Any idea?
thanks[/QUOTE]


Not much help but it's funny I couldn't get full screen to work with VLC in e17 so I used mplayer.  What are your drivers for mplayer?

---

### Post by songochain on 2005-07-31
I've used all drivers and always i get the same problem. In fullscreen the screen freezes but if i use gnome not... I think the problem is polyaudio because before i could use mplayer in fullscreen without any problem

---

