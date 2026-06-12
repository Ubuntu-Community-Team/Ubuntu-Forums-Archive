---
title: "JRE1.5 or...?"
date: 2005-12-13
forum: General Help
---

### Post by Kelpie on 2005-12-13
since i run on this version of ubuntu none of the -newer- ways to install or -older- ways to install jre to play runescape with on firefox works for me at all, so id really like to know how to do that, using Hoary -now-.

it would be appreciated much! thanks much!

---

### Post by lisje on 2005-12-14
[http://ubuntuforums.org/showthread.php?t=97989](http://ubuntuforums.org/showthread.php?t=97989)

look at this tread ... although I'm using breezy at the moment I used hoary for a very long time and the solution I give in this thread has worked for me in hoary as wel as in breezy.

download the java from sun and do as I've said in the post. It should work.. I never had any problems with it

to get firefox to recognize your java you'll have to do the following:

```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
```

the location of your java plugin might be different .. but I'm not at my ubuntu box so I can't really check right now.

I hope it helps,
greets

---

### Post by Kelpie on 2005-12-16
[QUOTE=lisje][http://ubuntuforums.org/showthread.php?t=97989](http://ubuntuforums.org/showthread.php?t=97989)

look at this tread ... although I'm using breezy at the moment I used hoary for a very long time and the solution I give in this thread has worked for me in hoary as wel as in breezy.

download the java from sun and do as I've said in the post. It should work.. I never had any problems with it

to get firefox to recognize your java you'll have to do the following:

```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
```

the location of your java plugin might be different .. but I'm not at my ubuntu box so I can't really check right now.

I hope it helps,
greets[/QUOTE]

everything worked fine, but i dont know where the plugin is located so im stuck, i got as far as that last bit of commands, since it was **jre-1_5_0_06-linux-i586.bin** not **jre-1_5_0_05** alittle help here would be nice, i wouldnt have a clue where the plugin would be located as there is no folder for JRE in **/usr/local/**

thanks much

Edit: looking in **/usr/lib/mozilla-firefox/plugins** the above exists but when i click it it disappears o_O

---

