---
title: "Problem to display Russian text: got '?' questions marks"
date: 2007-07-08
forum: Desktop Environments
---

### Post by mcglnx on 2007-07-08
Dear All,

I've received a russian (or ukraininan) CD.
however I got issue while displaying the MP3 content: I got only '?' question marks!

I've installed the language support and selected russian and ukraininan.
But this does not seems sufficient.

Any idea? Any clue?

Thanks,
M.

---

### Post by PryGuy on 2007-07-08
What CD are you talking about? A CD with MP3s that have tags written in Russian/Ukrainian?

That's because the ID tags are written in different (presumably CP1251 in our case) encoding if that's the case... Ubuntu uses Unicode. So basically Totem or Rythmbox reads these tags in Unicode. You may correct ID tags manually, in Rythmbox for instance. Right-click on the song you want to rename and choose 'Properties'. I couldn't automate the process so far... :(

---

### Post by mcglnx on 2007-07-09
Exatly an MP3 Cd.

Rythmbox says: 
- Problem occured without error being set. This is a bug in Rhythm.... (unable to read more.
Then 

- The GStreamer plugins to decode "MP3" files cannot be found.

---

### Post by PryGuy on 2007-07-10
Here you go, buddy! You're a newcomer, right? You have to read [this topic]("http://ubuntuforums.org/showthread.php?t=486525&highlight=MP3+codec") for instance. Do you know what codec is? Haven't you had the same problem in WindowsXP that can't playback MP3s out of the box as well?
This```
sudo aptitude install totem-gstreamer
```would solve your problem. Use forum search instead of blaming Rythmbox. ;)

---

### Post by mcglnx on 2007-07-11
> **PryGuy said:**
> Here you go, buddy! You're a newcomer, right? You have to read [this topic]("http://ubuntuforums.org/showthread.php?t=486525&highlight=MP3+codec") for instance. Do you know what codec is? Haven't you had the same problem in WindowsXP that can't playback MP3s out of the box as well?
This```
sudo aptitude install totem-gstreamer
```would solve your problem. Use forum search instead of blaming Rythmbox. ;)

Thanks - this was done + fixed.
BTW: I do not blame anything :) I just quoted what the guy says! :) (please re-read)

However this does not solve the font issue :(

PS: I'm not newcomer - may be getting too old to read 100G posts ... :(
PPS: I'm a developer, hence very lazy :)

---

### Post by PryGuy on 2007-07-11
What guy? It's not the font problem, it's encoding problem.

---

### Post by mcglnx on 2007-07-11
> **PryGuy said:**
> What guy? It's not the font problem, it's encoding problem.

Rythmbox - I give him some life.
Right - but still no solution.

---

