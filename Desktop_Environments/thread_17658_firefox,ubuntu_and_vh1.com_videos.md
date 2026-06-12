---
title: "firefox,ubuntu and vh1.com videos"
date: 2005-03-01
forum: Desktop Environments
---

### Post by luvdemheels on 2005-03-01
When trying to watch vh1.com videos it says I need the windows media player 9 plug-in. Is there a way to make this work?? Thanks for any help.

It does have a link to click to download but it tries to download a .exe file.

---

### Post by jimmt on 2005-03-02
You can use Kaffeine, a Xine library based application, or Mplayer and their respected plugins for Mozilla/Firefox. You will also need the w32 dll files that can be downloaded from MPlayer's website. Kaffeine, Xine, Mplayer, kaffeine mozilla plugin, and mplayer mozilla plugin can be downloaded from the repositories. 

I prefer Kaffeine. Its a very well written multimedia player application that can play DVD's along with other multimedia files. You will also be able to play real, wmv, and quicktime files with the above players. Kaffeine requires KDE-Libs on your system. 

Enjoy!
Jim

---

### Post by bored2k on 2005-03-03
[QUOTE=jimmt]You can use Kaffeine, a Xine library based application, or Mplayer and their respected plugins for Mozilla/Firefox. You will also need the w32 dll files that can be downloaded from MPlayer's website. Kaffeine, Xine, Mplayer, kaffeine mozilla plugin, and mplayer mozilla plugin can be downloaded from the repositories. 

I prefer Kaffeine. Its a very well written multimedia player application that can play DVD's along with other multimedia files. You will also be able to play real, wmv, and quicktime files with the above players. Kaffeine requires KDE-Libs on your system. 

Enjoy!
Jim[/QUOTE]

[Add this repositories](http://ubuntuguide.org/#extrarepositories) 
apt-get install mozilla-mplayer . dont even need 2 restart firefox

---

### Post by luvdemheels on 2005-03-05
mplayer installed with no problems with apt-get. I now can see a mplayer in my plugins directory by cannot watch anything on vh1.com. Where do the w32 dll files go??

I searched for a codecs directory but nothing comes up associated with mplayer just

/usr/lib/RealPlayer/codecs
/etc/gconf/gconf.xml.defaults/ (2 of these)

any more help?? I think all I need is to figure out where to put all the dll files.

---

### Post by yoha on 2005-03-05
[QUOTE=luvdemheels]mplayer installed with no problems with apt-get. I now can see a mplayer in my plugins directory by cannot watch anything on vh1.com. Where do the w32 dll files go??

I searched for a codecs directory but nothing comes up associated with mplayer just

/usr/lib/RealPlayer/codecs
/etc/gconf/gconf.xml.defaults/ (2 of these)

any more help?? I think all I need is to figure out where to put all the dll files.[/QUOTE]
 luvdemheels,
     Visit [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by macewan on 2005-03-05
[QUOTE=yoha]luvdemheels,
     Visit [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)[/QUOTE]


From what I saw they are trying to "detect" the proper plugin in the browser but they don't provide you the ability to set & save your setup to by pass the sniffing.

---

