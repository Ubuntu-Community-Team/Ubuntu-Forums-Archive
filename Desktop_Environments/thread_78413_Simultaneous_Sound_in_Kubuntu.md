---
title: "Simultaneous Sound in Kubuntu"
date: 2005-10-18
forum: Desktop Environments
---

### Post by gingermark on 2005-10-18
I was wondering if someone could please advise me (or direct me to a thread or other webpage - I did search though) how to best attain a sound set-up close to what Windows (ahem) has.

By that I mean, the ability to be playing something on XMMS, and have Gaim make a little sound cos someone is talking to you, and have that sound combined with the music as it plays, and then maybe realise that the webpage you're looking at is playing an annoying midi track.

Ok, so that wasn't so eloquently put, but you get the idea. Currently I have all KDE system sounds turned off, because they would interfere with video or music playback, and have resorted to a console beep in Gaim for when someone says hello.

There must be some way to combine all the sounds wanting to use the soundcard into one signal, and then feeding that to the soundcard??? Or something like that! :)

---

### Post by cuboconojos on 2005-11-19
Hi, so how's that Breezy goin', I'm still with Hoary....
Well, look, I found a guy that claims to have achieved what you want (and me too), check if this helps you:

[http://movabletripe.com/archive/simultaneous-sound-streams-with-alsa/](http://movabletripe.com/archive/simultaneous-sound-streams-with-alsa/)

I just tried it yesterday, but didn't make it. I had to work, so I stopped trying. Hope you get lucky!!

Greetings from Chile

---

### Post by Brando569 on 2005-11-19
what the dude said on the website doesnt work, it actually breaks your audio output. just for the heck of it i tried it. i closed amarok, made the file, saved it, and then reopened amarok. i went to play a file and Gstreamer was giving me and ALSA error or something. essentially it couldnt play the files. so i was curious and renamed the .asoundrc file i created and voila! amarok worked again! :D so yea i wouldnt really go by that website, if it works for you good job. but it didnt work for me, just a warning.

---

