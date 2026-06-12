---
title: "Need help to configure compiz"
date: 2006-07-08
forum: Desktop Environments
---

### Post by latebeat on 2006-07-08
Hi all,

I just finished installing XGL and compiz and it works fine on my Radeon 9800 :) I was very surprised!!
Anyway, I've spent hours trying to find how to configure some parts of compiz with no success:

1. I don't like the fade thing of the inactive window, is there any way to change the value to make it more subtle? With the default value the inactive windows become dark and I'd like to reduce that effect as I usually have two windows next to each other.

2. The speed that the inactive/background windows fade. I'd like to make it faster. I tried changing /apps/compiz/plugins/fade/screen/0 > fade_speed to 10 but it didn't make things that much faster :(

3. Is there a way to arrange the open windows? Like vertically, horisontally? Something like a permanent F12? 

I tried to find what I was looking for on google but I couldn't. I also tried the config tool that I found [here]("http://www.ubuntuforums.org/showthread.php?t=140687&highlight=compiz+administration") but I coudn't find the relevant option

Any help is greatly appreciated!

latebeat

---

### Post by Crosbie on 2006-07-08
1 & 2: Use Synaptic to install gset-compiz.  This'll give you a graphical tweaking program to set your preferences.  You might also like Compiz themer too. A search in Synaptic for 'compiz' should turn up these two programs. :)

3: I think there might be a solution to this.  Try a search on the Compiz forums: [http://www.compiz.net/index.php](http://www.compiz.net/index.php)

---

### Post by latebeat on 2006-07-08
Thanks for your reply... it's greatly appreciated!

gset-compiz absolutely rocks! Trying to configure compiz with just gconf guessing what each value does seems like stone age :)

Anyway, I still can't find which setting is responsible is for 1?

---

### Post by latebeat on 2006-07-08
It's funny after playing with gset-compiz for an hour I've only found the setting 2 minutes after posting my last message :)

Anyway, it's under trailfocus plugin, brightness setting. It didn't occur to me, I was looking at the fade tab :)

latebeat

---

