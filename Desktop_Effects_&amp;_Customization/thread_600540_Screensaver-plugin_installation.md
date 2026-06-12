---
title: "Screensaver-plugin installation"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by Nikitas350 on 2007-11-02
Can anyone tell me how can i install screensaver-plugin for compiz-fusion in gutsy? Thankssss :)

---

### Post by patmalcolm91 on 2007-11-02
I've been trying to figure the same thing out, i've also been looking for the 3d windows plugin. basically, you have to remove CF from your system, download compile and install CF from git, then you will be able to compile the plugin, which can also be acquired from git. The reason behind this is that gutsy doesn't have CF 0.6.0, and the newer plugins will not compile against the older version. However, i've read that the latest CF versions do not always run well under gutsy, so use at your own risk, personally, i'm just waiting for 0.6.0 to come out in the gutsy repositories...

---

### Post by jimerickso on 2007-11-02
my compiz upgraded to 0.6.0 today with automatic updates. might want to try:

sudo apt-get update

and see what happens!!

---

### Post by ocian on 2007-11-02
how do you check which version you have? I did the apt-get update but nothing new on the cf front... hmm do you have some other repo listed that you got it from?

edit: not even a minute after i posted, update manager says "hey new compiz!"

---

### Post by ocian on 2007-11-02
hmmm no new plugins though

---

### Post by Nikitas350 on 2007-11-03
Is there any .deb file with this plugin?. Or if there isn't can you write what exactly should i do because i am a beginner one. Thanks :)

---

