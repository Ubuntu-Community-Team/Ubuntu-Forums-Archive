---
title: "Gnome-Shell Issue installing certain extensions..help please."
date: 2011-10-16
forum: Desktop Environments
---

### Post by Phaze08 on 2011-10-16
So, I've scoured the net for this issue with the gnome shell, and havent found anything. I've found tons of guides for them and done exactly the way they say. For some reason, I get an error saying 'error loading extension' in Gnome Tweak. I also get this same error with the activities button extension. At first, I changed some of the config file to make a distro logo and not the word activities, so I deleted and reinstalled thinking that was the problem, and it still has the error. I also went into each of their metadata files and changed the gnome shell version to 3.2 which is my version. Anyone know anything else that might fix it? Here is what it looks like:
[http://s1211.photobucket.com/albums/cc433/ThePhaze08/?action=view&current=AdvancedSettings_001.png](http://s1211.photobucket.com/albums/cc433/ThePhaze08/?action=view&current=AdvancedSettings_001.png)

---

### Post by BigCityCat on 2011-10-16
I would try to help you but this post is pretty incoherent. Please explain a little better what problem you are having. The screen shot tells me nothing. I see a couple of yellow triangles. Thats about all I can gather from it.

---

### Post by 23dornot23d on 2011-10-16
Some of the extensions need modifying ..... it was always stated before people started writing the extensions that things would change ....... give it time and they will be made available ....

web8upd is a good place to look for new things coming out too .....

[http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

[http://www.webupd8.org/](http://www.webupd8.org/)

The weather extensions were on there earlier ..... about 7 down ...... but it is constantly changing , hope this helps ....

---

### Post by Phaze08 on 2011-10-16
As I said, at first, the extension didnt even show up, then when I went in and edited the file to reflect the correct version of gnome shell, what you see is what happened. When you hover over the yellow triangle, it just says 'error loading extension' just as I said lol. Actually, I did get the media one from that site you listed, but its not working. Are you saying theres not much I can do but wait?

---

### Post by 23dornot23d on 2011-10-16
If you had old ones installed then you can try removing them first ....

~/.local/share/gnome-shell/extensions/

Check which you have in there ..... first .....

I believe I removed mine and then it started to work ok .....

(what theme are you using - ?)

---

### Post by Phaze08 on 2011-10-16
Since I only installed them yesterday, I wouldnt think they would be old, but I'll give it a shot. Also, my themes are as follows:
Window- Humanoid
Icon- DarkRed Faenza
GTK+- Plastiq
Shell- GSmall

Would that matter?

---

### Post by BazookaAce on 2011-10-16
Add the webupd8 repo and install the extensions that way. They updated the extensions a couple of days ago, so don't use the ones from month old blogs etc.

After installs close gnome tweak tools if it's open, refresh gnome-shell (ALT + F2 type in R + Enter), reopen gnome tweak tools, and voila. Worked for me.

---

### Post by 23dornot23d on 2011-10-16
Nope I just liked what I saw and would like them myself ..... you just helped me .... 

Thank you .....

> 
Add the webupd8 repo and install the extensions that way. They updated  the extensions a couple of days ago, so don't use the ones from month  old blogs etc.

After installs close gnome tweak tools if it's open, refresh gnome-shell  (ALT + F2 type in R + Enter), reopen gnome tweak tools, and voila.  Worked for me.
thanks for helping out there too BazookaAce ....

---

### Post by Phaze08 on 2011-10-16
Oh, sweeet. Thanks! And its ok IMO, but i wish it wasnt blueish lol. Cant find many good gtk+ themes. -_-

---

### Post by 23dornot23d on 2011-10-16
[IMG]http://img811.imageshack.us/img811/7186/screenshotat20111012123.jpg[/IMG]

Mine looks like this I use the Tron theme .... and Awoken Elegant icons ..... but maybe that s not what you want ......

I fancy a change though and no doubt some more new themes and extensions will be written now
this is stable ....

or another like this

[IMG]http://img836.imageshack.us/img836/6213/screenshot1kn.jpg[/IMG]

---

### Post by Phaze08 on 2011-10-16
It just bothers me that all my windows are blueish inside like the screen I showed but I cant find any that are black or grey like I would like. For now this works. Also, even though I've seen both of the extensions I'm having problems with on that site you mentioned, both of them are not in the PPA. -_- I guess I'll have to wait until someone makes one that works for me lol.

---

### Post by 23dornot23d on 2011-10-16
I keep checking for things for Gnome-Shell .... check my page out as I often post new things on it that I find ....

[B][23dornot23d]("http://ubuntuforums.org/member.php?u=953253").


[IMG]http://img847.imageshack.us/img847/739/screenshot5jx.jpg[/IMG]
[/B]

---

### Post by Phaze08 on 2011-10-16
I did find some themes in those ppas and some good things i was needing like Jupiter. Thanks alot. :D

---

### Post by 23dornot23d on 2011-10-16
Glad you are sorted and thanks to [BazookaAce]("http://ubuntuforums.org/member.php?u=724195") for saying about the updates to the PPA

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

---

