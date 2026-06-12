---
title: "Rhythmbix and KDE"
date: 2005-05-11
forum: Desktop Environments
---

### Post by MyBestLaidPlans on 2005-05-11
I am having trouble getting rhythmbox to work in KDE... using GCONF I see that gsteamer needs two paramters to work correctly., audiosink and audiosource.  I have the first param set to osssink and I think I only need the second parem.  So I was wondering what I needed to set the second param to, to enable playback.


Also the error I am getting is:
"could not open resource for writing", it is possible I am way off with the solution so if you have anyother suggestions pleas post.

---

### Post by fromoze on 2005-05-12
Have you try amaroK? JuK?  May be is easier to stay on KDE-apps :) 

The problem can be about arts and esd; the sound daemon of KDE and Gnome. You must use artsd because I think esd won't starts when arts is working.

---

### Post by F for Fragging on 2005-05-12
amaroK owns Rhythmbox. I recommend that you simply use amaroK and ditch Rhytmbox, then your problem will be solved.

---

### Post by JonahRowley on 2005-05-12
I erm..  third that.  amaroK wipes the floor frontwards, backwards, upside-down and inside-out with Rhythmbox.  To get the best performance (in my experience) install and use the Xine engine.

---

### Post by MyBestLaidPlans on 2005-05-12
I am not a fan of amarok...it will not add AAC to the library.  Now I understand not many ubuntu users use AAC, but I do.  This in my eyes makes amarok a lesser player.  As linux users I am surprised this community went for the bells and whistles of amarok over fuctionality of players like XMMS, Rhythmbox or any other that has managed to support a huge number of formats.  Now I am not saying amarok can't play them... I am only saying amarok doesn't work well with them and amarok has no intention of correcting this.  So pleas... the problem at hand?

---

### Post by fromoze on 2005-05-12
The solution is go a step forward and use amarok-gstreamer. Amarok will use the same media layer than Rhythmbox on KDE4, but you have the possibility to switch yet. I'm using amarok-gstreamer whitout any problems, and is on kubuntu repositories  :)

---

### Post by -Rick- on 2005-05-12
[QUOTE=MyBestLaidPlans]I am not a fan of amarok...it will not add AAC to the library.  Now I understand not many ubuntu users use AAC, but I do.  This in my eyes makes amarok a lesser player.  As linux users I am surprised this community went for the bells and whistles of amarok over fuctionality of players like XMMS, Rhythmbox or any other that has managed to support a huge number of formats.  Now I am not saying amarok can't play them... I am only saying amarok doesn't work well with them and amarok has no intention of correcting this.  So pleas... the problem at hand?[/QUOTE]
IMO Amarok has "all the bells and whistles" + even better functionality than other players. For example you can hide it away and still use the keyboard to control it.
The only downside is that it uses arts, because of this sound will stutter(atleast for me) when any other program tries to use arts.

---

