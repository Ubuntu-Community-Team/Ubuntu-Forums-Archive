---
title: "About movie playing"
date: 2005-03-26
forum: Desktop Environments
---

### Post by wxm505 on 2005-03-26
I currenttly suffered a problem about the movie playing.
When I use xine , totem or realplayer to play a movie.
It worked. But it looked too bright.
I switched to another user , it worked very well.
I tought I might set up something wrong. The box display
workes well.
I am confused .
any help??  Thanks a lot

---

### Post by lorap on 2005-03-27
hi!
you've to go to the Computer-->Computer Management-->Synaptic Package Manager.once you've the synaptic window open go to the Settings-->Repositories.
once you've a new small window open mark all possible checkboxes ignoring the worning messages after what press Ok button.the window closes and you're back again to the main synaptic window.press Reload button and wait until the process completes.after the process's completed press the Search button and in the search window write in VLC then press Ok button.once the synaptic picks it up for you mark the VLC whose remarks're "for gtk+" but not for the gnome.that one for the gnome has a bug.after you mark it for installation press Apply button.that's all.
have a nice day friend!
pavel

p.s.:
it doesn't need any codec being installed.all codecs built in in its executable.

---

### Post by joplass on 2005-03-27
Is there a way to make VLC my default player?  Or simply bring it up when I need it?  I installed it and still can't use it.  I am trying to watch some trailers from apple.com.
I am familiar with VLC because I have used it under windows.
Please help.
When I look at my plugins in Mozilla I see VLC in there with its plugins but the program does not come up when I need it.
Thank you,

---

### Post by lorap on 2005-03-27
my friend,i've paied attention to yor question.
this's the answer-yes you can!
let's work.
all you need is to uninstall all players exept XMMS for mp3 and VLC for movies.
once you've all other player uninstalled they become the default ones.
to uninstall them just go to the Computer-->Computer 'Management-->Synaptic Package Manager.once you've it open press the Search button and in the search window write in TOTEM.then choose the option "names and descriptions" after what press Ok button.when the synaptic picks it up for you deselect it and press Apply button.that's all :-)
have a nice day friend!
pavel

p.s.:
uninstall everything except the players i've mentioned above.
don't worry,it wouldn't make any harm to the system.

---

### Post by joplass on 2005-03-27
Thanks pal but no video, audio only.
 :mrgreen:

Never mind I had to change the way it reads codecs and now I am up and running.  Next I have to see if live streaming is working as well.

---

### Post by lorap on 2005-03-28
should i understand VLC doesn't render avi files?
it's very strange cause it has all codecs needed built in.
moreover,it's possible to render all kinds of mp files,mp1 as well as mp4.

---

### Post by iomicifikko on 2005-03-29
[QUOTE=lorap]should i understand VLC doesn't render avi files?
it's very strange cause it has all codecs needed built in.
moreover,it's possible to render all kinds of mp files,mp1 as well as mp4.[/QUOTE]
 --->IM A NEWBIE<----

it happens sometimes to have audio only. if i was in u i'd install again totem-xine version (not gstreamer) couse xine is a really good player and try that one (install the w32codecs pack too); then if u want to use vlc as your default player everytime u find a new mediaformat just rightclick on it and select "properties" then go to the "open with" part and select your default program (if u cant see it just add it with the search button)

hope to be useful

---

