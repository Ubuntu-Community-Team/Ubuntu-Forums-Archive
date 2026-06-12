---
title: "Desktop record problem"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by bigbrovar on 2007-08-30
guys  is there any package i can use to video capture my desktop so that i can do record of my compiz-fusion effect and show off to my friends...i tried Istanbul..it seems to work but i found out that i could not play the output file with vlc, kaffeine or any video playeer i have on my system ...and i couldnt encode it to any player either...the out put file for istanbul is Ogg Theora video...any help would be appreciated

---

### Post by mckryptyk on 2007-08-30
you should look into using a re-encoding program for converting you Ogg/Theora to some other format. I reccomend Devede for converting to mpeg which plays in everything.

At the comand line type this to install from the repos.

You may need extra codecs in the repos, if so use synaptic to search for "devede" and right-click under 'suggested packages"

```
sudo apt-get install devede
```

---

### Post by bigbrovar on 2007-08-30
> **mckryptyk said:**
> you should look into using a re-encoding program for converting you Ogg/Theora to some other format. I reccomend Devede for converting to mpeg which plays in everything.

At the comand line type this to install from the repos.

You may need extra codecs in the repos, if so use synaptic to search for "devede" and right-click under 'suggested packages"

```
sudo apt-get install devede
```

 just installed the devede package but i dont know how to go about using it pls can u  enlighten me on how to use it and use it  and the codecs that i nned to download...am sorry if my question seems newbiesh

---

### Post by mckryptyk on 2007-08-30
You will need to go to "Applications ---> Sound and Video --> Devede" in the menu.
You can find Synaptic in "System --> Administration --> Synaptic Package Manager".

The codecs will all be in the repos that synaptic uses to update with.

The program is very "point and click" and you can safely play around with it.

Have you installed Medibuntu to add codecs for audio and video ?

Medibuntu is a repo (a collection of programs) dedicated to audio and video.

If not you may want to go to medibuntu.org and follow the how-to that is there to enable it too. 

Cheers.

---

