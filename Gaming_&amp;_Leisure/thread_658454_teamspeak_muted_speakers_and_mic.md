---
title: "teamspeak muted speakers and mic"
date: 2008-01-04
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2008-01-04
I just installed teamspeak on 7.10, and I can not unmute my mic or sound. I've searched the forums, and someone had the same problem, they solved it by un-installing pulseAudio, but I never had that. What else could be interfering with my sound?

---

### Post by Tyke91 on 2008-01-04
I think that the problem is that my sound input seems to be through Control1 instead of Control0, but teamspeak is trying to default through it anyway. I don't know how to fix this though...

I know the mic is good because I used it to record some stuff with audacity

---

### Post by Tyke91 on 2008-01-04
hmm... still haven't solved it yet.

---

### Post by HeinekenPissr on 2008-01-19
i'm having the same problems with Teamspeak 2 on 7.10.

I have the mic working fine in skype but i don't know how to get ti to work in teamspeak.

---

### Post by HeinekenPissr on 2008-01-19
oh yeah i forgot to mention that i can't hear the others in the room either, even though there is a green light by my name.

---

### Post by 3rdcoast on 2008-01-19
mine was working and now its not. it must be an update I ran.

---

### Post by darkazurka on 2008-01-28
HeinekenPissr: I could only hear the other people in the room but could not speak.

About "i can't hear the others in the room either, even though there is a green light by my name."
The green light means that you are currently speaking. I hear by green lights popping up by other members.

So it's natural you don't hear anything when your green light is on. When other's green lights are on, then you should hear what they say.

Now about my issue which I specify in the title as solved: I couldn't speak and I went to the menu Settings->Options->"Sound and Options" tab->It was originally selected as "Default (oss /dev/dsp)". I let it be that way, but for those settings to work I need to install alsa-oss through synaptic.

I think the key was to install the package alsa-oss through synaptic, since it's the default sound device. (and it's logical that it doesn't work in the beginning if it isn't even installed)

---

### Post by HeinekenPissr on 2008-01-28
well i do have alsa-oss installed already but when i try to switch over to oss it shows that i am muted in the chatroom and i can't unmute myself in the teamspeak program.

When i use ALSA the green light is constantly on in the chat room and i see others with green lights consistently on as well.  However i can hear nothing and they can't hear me.

I don't know what is wrong with it.  Everything works fine in skype so i don't think it's my ubuntu settings.  I've noticed lots of threads with this problem and no one really seems to have an answer. 

<-- getting pretty frustrated at this point

---

### Post by shaolinchamp on 2009-03-20
im having the same problem, but im using 8.04 64bit

---

