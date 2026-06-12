---
title: "installing kde packages in xubuntu"
date: 2006-05-15
forum: Desktop Environments
---

### Post by pillu on 2006-05-15
Hi all 

Is there any way I can install packages meant for KDE in xubuntu. I want to install kguitar and it cannot find the required kde libraries (obviously).  :-k

---

### Post by aysiu on 2006-05-15
Actually, that's not obvious at all--that's the exact opposite of what's supposed to happen.

Even if you're using Gnome or XFCE, you should be able to install a KDE application and Synaptic, apt-get, or aptitude will download and install all the necessary libraries that the application depends on.

Can you post the output of these commands? ```
sudo apt-get update
sudo apt-get install kguitar
cat /etc/apt/sources.list
```

---

### Post by pillu on 2006-05-15
[QUOTE=aysiu]
Can you post the output of these commands? ```
sudo apt-get update
sudo apt-get install kguitar
cat /etc/apt/sources.list
```[/QUOTE]

I was trying to build kguitar from source which is why it gave the 'libraries not found' error. apt-get worked fine and installed all the libraries and kguitar too. However now when I try to run kguitar it gives me a lot of warnings like 

**/usr/share/applications/xfmedia.desktop specifies undefined mimetype/servicetype 'audio/mp3'**

and the system just crashes after that and i have to do a hard reset. There must be some problem with P2 systems. So many linux programs crash on it. Wine didn't work either. I guess I will have to live with it. Is there any way to uninstall all the kde libraries that were fetched and installed and are probably of no use to me now ? ](*,)

---

### Post by aysiu on 2006-05-15
Try: ```
sudo cp /usr/share/applications/xfmedia.desktop /usr/share/applications/xfmedia.desktop_backup
sudo nano /usr/share/applications/xfmedia.desktop
``` Delete the line that specifies the MIME type. Then save (control-x), confirm (y), and exit (Enter).

---

### Post by pillu on 2006-05-15
After deleting the lines in xfmedia.desktop it gives me the same error but in mplayer.desktop. After deleting in mplayer.desktop it gives the same error for gimp.desktop. There are so many .desktop files in /usr/share/applications/ that it will be a monumental task opening everyone and deleting these lines from them....yawn....
I omitted a part of the warning earlier because i didn't  notice it then it says
[B]kbuilidsyscoca WARINNG:/usr/share/applications/xfmedia.desktop specifies undefined mimetype/servicetype 'audio/mp3'
[/B]

---

### Post by aysiu on 2006-05-15
Shoot. Well, [it doesn't look as if that error is very common, but these may help you...](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=WARNiNG%3A++specifies+undefined+mimetype%2Fservicetype+%27audio%2Fmp3%27&btnG=Search).

---

### Post by pillu on 2006-05-15
I uninstalled kguitar using apt-get remove and then tried to build it from source. When I do a ./configure it gives me and error which says

**Checking for X...Configure: Error: Can't find X includes. Please check your insallation and add the correct paths!**

Could this be the problem?
Also could you tell me how I can dump the error messeges from the terminal into this quick reply box. Its a big pain to type them.

Thanks

---

### Post by aysiu on 2006-05-15
[QUOTE=pillu]
Could this be the problem?[/quote] You know, honestly, this problem is way beyond my knowledge. I don't even compile from source... ever.

> Also could you tell me how I can dump the error messeges from the terminal into this quick reply box. Its a big pain to type them. Sure, just highlight the text, right-click, select copy, and then paste it in here.

---

