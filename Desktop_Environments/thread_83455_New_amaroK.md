---
title: "New amaroK"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Freddy on 2005-10-28
I don't know if a similar thread already exit but I just wanted to mention that there is a new version of amaroK 1.3.5 compiled for kubuntu. 
You can find amaroK 1.3.5 with the gstreamer package at: [http://kubuntu.org/announcements/amarok-1.3.5.php](http://kubuntu.org/announcements/amarok-1.3.5.php) 
and some other engine's at: [http://kubuntu.org/packages/amarok-1.3.5/](http://kubuntu.org/packages/amarok-1.3.5/)

You can install this over 1.3.1 that you installed from your repos, just download the package, open up a konsole and browse to the place on the harddrive that you downloaded the .deb to and write.
```
sudo dpkg -i packagename
```
/// Freddan

---

### Post by Sykil on 2005-10-28
Awesome. :D And installing it on Ubuntu will work too, correct?

---

### Post by Freddy on 2005-10-28
Hmm I don't really know but I would think so, I'll guess you would have to try and plz post the outcome here.   /// Freddan

---

### Post by mlomker on 2005-10-28
Packages are an easier way to go, but the [SVN version]("http://www.ubuntuforums.org/showthread.php?t=80492") is on 1.4 already...

---

### Post by Jvaldezjr on 2005-10-29
I keep having Amarok crash everytime I try to play an MP3....anyone else have that problem?  Im using 1.3.5

---

### Post by Snakey on 2005-10-29
[QUOTE=Jvaldezjr]I keep having Amarok crash everytime I try to play an MP3....anyone else have that problem?  Im using 1.3.5[/QUOTE]
Have you installed the codecs?
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by Freddy on 2005-10-29
Try to update with the new amarok some of the former bugs has been squshed and also uncheck the services for the last.fm community, those is  monsters for most cpu's.   /// Freddan

---

### Post by Freddy on 2005-10-29
[QUOTE=mlomker]Packages are an easier way to go, but the [SVN version]("http://www.ubuntuforums.org/showthread.php?t=80492") is on 1.4 already...[/QUOTE]
If you are that much a fan of compiling, why aren't you using Slackware or Gentoo :), I compile when needed to and use precompiled packages when availible, as a matter of fact I do use the svn version but just wanted to let everybody know thet there exist updated packages.   /// Freddan

---

### Post by Jvaldezjr on 2005-10-29
[QUOTE=Snakey]Have you installed the codecs?
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)[/QUOTE]

Yea I did that, all the ones on there, except divx4linux, since apt-get can't find it in the repositories.  Amarok still crashes....using 1.3.5

---

### Post by Freddy on 2005-10-29
You don't need that, install the gstreamer package and you have mp3 support, do as I said before disable the last.fm service and upgrade to 1.3.5 as I posted previously and you should be alright.   /// Freddan

Edit: Ohh I didn't read your hole post, now I see that you already use 1.3.5, have you disabled last.fm, in amarok settings ? Did you download the gstreamer package where you took 1.3.5 ?, if so have you choosed to use the gstreamer engine in settings ?

---

### Post by mlomker on 2005-10-29
> I compile when needed to and use precompiled packages when availible, 

I haven't tried a packaged version that worked 100% yet.  The current SVN is solid.

---

### Post by Rob2687 on 2005-10-29
Is it just me or does Amarok use a lot less CPU % lately. :D

---

### Post by angrykeyboarder on 2005-10-30
[quote=Freddy]I don't know if a similar thread already exit but I just wanted to mention that there is a new version of amaroK 1.3.5 compiled for kubuntu. 
You can find amaroK 1.3.5 with the gstreamer package at: [http://kubuntu.org/announcements/amarok-1.3.5.php]("http://kubuntu.org/announcements/amarok-1.3.5.php") 
and some other engine's at: [http://kubuntu.org/packages/amarok-1.3.5/]("http://kubuntu.org/packages/amarok-1.3.5/")

You can install this over 1.3.1 that you installed from your repos, just download the package, open up a konsole and browse to the place on the harddrive that you downloaded the .deb to and write.
```
sudo dpkg -i packagename
``` /// Freddan[/quote] 
Most importantly it cured this bug

>  Fix amaroK attempting to destroy your computer, reach through the       monitor and violently strangle you if you attempt to exit while the       collection is being scanned. ([BR 114597]("http://bugs.kde.org/show_bug.cgi?id=114597")) ([BR 114859]("http://bugs.kde.org/show_bug.cgi?id=114859"))

---

### Post by DeeZiD on 2005-10-30
Why not use the xine-engine instead of gstreamer?

Xine is the only engine which works correctly on my computer with Kaffeine and amaroK (arts is even better than gstreamer, too!)


Dennis

---

### Post by Freddy on 2005-10-30
[QUOTE=DeeZiD]Why not use the xine-engine instead of gstreamer?

Xine is the only engine which works correctly on my computer with Kaffeine and amaroK (arts is even better than gstreamer, too!)[/QUOTE]
Ofcourse you can use the xine-engine or even arts. It's just that the amaroK team themselfs suggest Gstreamer and some functions in amaroK is only availible when using that engine but if you are having problems with Gstreamer and none with Xine, use it, there are a compiled xine enginge for amarok in the links I provided in my first post.   /// Freddan

---

### Post by manicka on 2005-10-30
[QUOTE=Freddy]Hmm I don't really know but I would think so, I'll guess you would have to try and plz post the outcome here.   /// Freddan[/QUOTE]
Great! Works perfectly in Ubuntu

---

### Post by manicka on 2005-10-30
[QUOTE=Rob2687]Is it just me or does Amarok use a lot less CPU % lately. :D[/QUOTE]
Yes! 1.3.5 running on about 4.5 -5%. At least half of what 1.3.1 used to use

---

### Post by Freddy on 2005-10-30
> Great! Works perfectly in Ubuntu
I'm glad to hear it, even Gnome needs some of that amaroK feeling :).   /// Freddan

---

### Post by manicka on 2005-10-30
[QUOTE=Freddy]I'm glad to hear it, even Gnome needs some of that amaroK feeling :).   /// Freddan[/QUOTE]
With the right theme, it almost feels like it is made for gnome ;)

---

### Post by Freddy on 2005-10-30
Haha can't you Gnomefolks at least give KDE credit for one lousy app, without trying to make it Gnome :D   /// Freddan

(This post was intended as a joke, not the start of a boring and pointless flamewar)

---

### Post by manicka on 2005-10-30
hehe :p

---

### Post by angrykeyboarder on 2005-10-30
[quote=Freddy]Ofcourse you can use the xine-engine or even arts. It's just that the amaroK team themselfs suggest Gstreamer and some functions in amaroK is only availible when using that engine but if you are having problems with Gstreamer and none with Xine, use it, there are a compiled xine enginge for amarok in the links I provided in my first post. /// Freddan[/quote]

You can actually install the "the amarok-engines package wich installs GStreamer, Xine and Arts engines allowing you to switch between them as necessary".

However, with the way Kubuntu has set up this link it's not that easy.  I wonder if this has made it into the repos yet.....

---

### Post by Jvaldezjr on 2005-10-30
>  Edit: Ohh I didn't read your hole post, now I see that you already use 1.3.5, have you disabled last.fm, in amarok settings ? Did you download the gstreamer package where you took 1.3.5 ?, if so have you choosed to use the gstreamer engine in settings ?

I dont know how to disable last.fm, and I did install the new gstreamer package with version 1.3.5.

---

### Post by angrykeyboarder on 2005-10-31
[quote=Jvaldezjr]I dont know how to disable last.fm, and I did install the new gstreamer package with version 1.3.5.[/quote]

If you never had it enabled before, it wouldn't be enabled now.

---

### Post by Sankukai Monkey on 2005-10-31
[QUOTE=angrykeyboarder]Most importantly it cured this bug[/QUOTE]

Don't hate me for hijacking please !? Am I correct in thinking that Amarok won't play media on another PC ? All my content's on a Samba accessible network drive but I can't see how to let Amarok build the repository and then let me play it ?

S

---

### Post by manicka on 2005-11-01
If you have the Samba drive mounted then amaroK should be able to use it.

---

### Post by 23meg on 2005-11-01
1.3.5 totally shines: redesigned, much better looking volume control and less cpu usage (never exceeds 3% here). The debs installed smoothly over the Breezy version; I recommend eveyone to upgrade.

---

