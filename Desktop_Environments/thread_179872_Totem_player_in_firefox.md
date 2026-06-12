---
title: "Totem player in firefox"
date: 2006-05-20
forum: Desktop Environments
---

### Post by sjpritch25 on 2006-05-20
Totem is the only media player that works flawlessly.  However, i get this message in Firefox.   I believe i should uninstall gmplayer plugin in firefox, however, i don't remember the terminal commands.  Same for installing totem plugin.  When i installed Ubuntu, the first thing i did was run Automatix.  Any help would be much appreciated.  Thanks](*,)

---

### Post by bluevoodoo1 on 2006-05-20
To uninstall a program from the terminal...

```
sudo apt-get remove nameofprogram
```

to install one...


```
sudo apt-get install nameofprogram
```

in this case, if you want to remove the mplayer firefox plugin (I think its name is mozilla-mplayer)

```
sudo apt-get remove mozilla-mplayer
```

**I don't know if this will fix your problem** since I don't know anything about automatix, but those are the commands.

---

### Post by sjpritch25 on 2006-05-21
How do i get totem to play .wmv files in firefox.  Otherwise, i have no problem playing .wmv files.  When i try and play a .wmv video in firefox i get the attached error in my first reply.  Thanks in advance.

---

### Post by zxcv70 on 2006-05-22
[QUOTE=sjpritch25]How do i get totem to play .wmv files in firefox.  Otherwise, i have no problem playing .wmv files.  When i try and play a .wmv video in firefox i get the attached error in my first reply.  Thanks in advance.[/QUOTE]

Try to install Plugger, but I'm not sure if it will work in totem,but it works fine with Mplayer and Kaffeine.

[http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html)

Actually you could install Plugger and than change all video formats in Fire Fox to be opened by Totem. 
I hope it will help.

---

### Post by sjpritch25 on 2006-05-22
Sorry, but i am new at linux terminal commands.  When i untar the archive what directory do i place it in??? Could you please tell me the commands.  Thanks

---

### Post by adamkane on 2006-05-22
Totem is a way from being fully functional.

gxine (xine-ui) with the mediaplayerconnectivity firefox extension is the way to play multimedia with firefox.

gxine-ui:
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29]("http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29")

mediaplayerconnectivity:
[https://addons.mozilla.org/firefox/446/]("https://addons.mozilla.org/firefox/446/")

---

### Post by sjpritch25 on 2006-05-22
I downloaded the totem plugin for firefox (xine) and everything seems to work.  I am not to sure how i did it.  Some sites the sound doesn't seem to work.  Here is site [thatvideosite.com](thatvideosite.com)

---

### Post by adamkane on 2006-05-22
I'm just offering my 2 cents. Others may be able to help you with Totem.

The point I'm trying to make is that Totem is not the best application to use with streaming media and firefox.

If you want to play all the streaming media possible, then I recommend that you install gxine (xine-ui) and mediaplayerconnectivity. I was able to play the videos easily using these apps. If you install, and have any issues, let me know. Be sure to check the mediaplayerconnecitivity options:
Firefox -> Tools -> Mediaplayerconnectivity -> Configure

If you continue to use Totem for streaming media, you will continue to come across media that you can not play, or playlists that Totem does not understand.

Totem will be functional some day. That day is not yet.

---

