---
title: "TV Card and Xaw TV help"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Joaobio on 2006-10-07
Well hello, i'm a new user to linux, i came from windows in which i was almost the ruler of the universe :P, now here in linux things are a bit different, but i already got used to linux and learned how to work with the terminal etc... But i'm having some problems, mainly, I have a TV Card, a Pinnacle PCTV Rave, and i searched for the web, on topics how to install it, but i found none useful for a begginer... on the other side, i installed XAWTV through apt-get and synaptic, and both ways make my x server crash (at least my monitor goes completely black, and nothing works except for ctrl alt backspace (server X restart) ) ... Do you know a simple way to install my card and make xawtv work? Thank you in advance..

Another problem i have is with enemy territories, because everytime i restart my computer i have to write in the console, 
```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```

To make the sound work... Is there a way so i only have to do this once more? and it stays that way?
And finally which are the best free FPS and 3D RPG Games in linux?

---

### Post by fragos on 2006-10-07
You may find tvtime a better viewer and its much more user friendly.

---

### Post by someguyouknow on 2006-10-07
> And finally which are the best free FPS and 3D RPG Games in linux?


for free FPS games, there are a bunch here
[http://en.wikipedia.org/wiki/List_of_free_first-person_shooters](http://en.wikipedia.org/wiki/List_of_free_first-person_shooters)
my personal favorite is Tremulous
[http://tremulous.net/index.php?section=files](http://tremulous.net/index.php?section=files)
and some more games are here...
[http://www.happypenguin.org/](http://www.happypenguin.org/)

---

### Post by Joaobio on 2006-10-08
Ok thank you for that links, and i'm going to try tvtime... but still i have no way to make the drivers for the tv card work...
On the other side i managed to make the sound work on et... finally...


Update: TV time works perfectly sound and everything, just one problem, it doesn't save my channels! i change the order of the channels i turn it off and it won't save my changes, in color and everything! Any ideas?

(Btw thanks for the TV time sugestion)
I've found out on the web that xawtv has been crashing with the new nvidia and ati drivers...

---

### Post by fragos on 2006-10-08
I've never tried to re-order the channels.  It may have its own reasons for maintaining numeric order.  TV guide aps like OnTV allow a different order of channels in their display.  Check out xmltv which builds a database that many guides and even tvtime access.  TVtime can pop up a discription of the currently viewed channel and tell what will be on that channel next -- very cool.  I have however eliminated many channels from up down arrow or mouse wheel selection.  Eliminated channels can still be selected by typing the channel number when the focus is on the tvtime window.

---

