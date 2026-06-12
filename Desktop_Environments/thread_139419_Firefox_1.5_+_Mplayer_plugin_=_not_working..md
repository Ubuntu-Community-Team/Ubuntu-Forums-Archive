---
title: "Firefox 1.5 + Mplayer plugin = not working."
date: 2006-03-04
forum: Desktop Environments
---

### Post by nismoskys on 2006-03-04
ive searched.. ive read.. ive tried.. ive failed. lol yeah its not working at all.. im on breezy. I get nothing in "about: plugins" except for 2 entries for shockwave flash. no mplayer or anything or mime stuff. can anyone help? thanks.:-k

---

### Post by akiro.yamamoto on 2006-03-04
Use Synaptic, search for mplayer. You should see one package called:
mozilla-mlpayer
Use that, uninstall 
mozplugger (1.7.1) 
and all should be good. This is my current set-up and it just works. ;)

---

### Post by akiro.yamamoto on 2006-03-04
Here is a screenshot of what my Firefox 1.5 about: plugins page looks like:
[http://ubuntuforums.org/showthread.php?t=135882&page=3](http://ubuntuforums.org/showthread.php?t=135882&page=3)
Hope this helps...

BTW:
Do you have the backports repo enabled? Because that is the version (Ver. 3.17) 
that I'm currently using.

---

### Post by nismoskys on 2006-03-04
sorry man, thanks for the help, i just tried what you said, but nope doesnt work.. this is what my about: plugins looks like.. those are ALL the plugins i have.. :(  lol

i installed mozilla-mplayer 3.17

[[IMG]http://img216.imageshack.us/img216/9600/screenshotaboutpluginsmozillaf.th.png[/IMG]](http://img216.imageshack.us/my.php?image=screenshotaboutpluginsmozillaf.png)

---

### Post by akiro.yamamoto on 2006-03-04
[QUOTE=akiro.yamamoto]Use Synaptic, search for mplayer. You should see one package called:
mozilla-mlpayer
Use that, uninstall 
mozplugger (1.7.1) 
and all should be good. This is my current set-up and it just works. ;)[/QUOTE]

In Synaptic, is the entry like this?
Didi you install Firefox 1.5 according to the wiki?
Try to locate your plugins directory for firefox then either copy or link the installed plugins
Example
```

cd /opt/firefox/plugins/  (Or wherever you installed firefox)
sudo ln -s /usr/lib/mozilla/plugins/* . 

```

Edited for Clarity ;)

---

### Post by nismoskys on 2006-03-04
duuuuuudde :) !! THANK YOU :) worked perfecttly! It was the symlink. as soon as i did ```
cd /opt/firefox/plugins/  (Or wherever you installed firefox)
sudo ln -s /usr/lib/mozilla/plugins/* . 
``` and started up ff all the plugins showed up inside.. thanks alot man.. now i dont have to go into epiphany everytime i wanna watch something :)

---

### Post by akiro.yamamoto on 2006-03-04
Ahhh!!! I was starting to get worried:)
Glad to hear it!!!

---

### Post by nismoskys on 2006-03-04
everything works great!.. **but** some media types LAG like crazy... like the playback it just lags and skips.. yes the content was fully loaded.. well ive only experienced this with embedded mp3 playback but it might be in other things as well? i dunno.. if you have any clue.. other than that.. working great man thanks.

---

### Post by akiro.yamamoto on 2006-03-04
Can you give a little more detail?
I know you can adjust the cache buffer size, so it may just be that.


EDIT:
Post the link that your having trouble with....
I'll see if I'm having the same error.

---

### Post by nismoskys on 2006-03-04
sweet nvm but thanks for the tip on adjusting the cache buffer size... all i did was right click on the embedded mplayer and went to configure, went to Audio Output and selected oss.. works perfectly.. only thing now is if i try to scan the music to a different part i get extreeme distortion.. but thats cool, i can deal with that :) thanks man.

---

### Post by akiro.yamamoto on 2006-03-04
De nada ;)

---

