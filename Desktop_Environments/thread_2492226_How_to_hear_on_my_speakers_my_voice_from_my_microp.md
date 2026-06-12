---
title: "How to hear on my speakers my voice from my microphone"
date: 2023-11-04
forum: Desktop Environments
---

### Post by johnaaronrose on 2023-11-04
[]("https://askubuntu.com/posts/1491441/timeline")  
          
                                        I'm using Ubuntu 22.04 desktop. I've noticed that both Pulse Audio & Pipewire both seem to be installed.  I would prefer it to be done bya GUI if possible.

I simply want to hear (on my speakers) my voice when speaking into my  microphone, situated at some distance from my speakers to minimise  feedback. I've tried all the suggested solutions at [URL="https://askubuntu.com/questions/123798/how-to-hear-my-voice-in-speakers-with-a-mic"]How to hear my voice in speakers with a mic?


[/URL][URL="https://askubuntu.com/questions/123798/how-to-hear-my-voice-in-speakers-with-a-mic"]
[/URL]

---

### Post by Autodave on 2023-11-04
There are some sound cards that are not bi-directional.  In other words, you can either record or listen to sounds, but not both at the same time.

---

### Post by #&amp;thj^% on 2023-11-04
This works on mine, but I'm one that use's very little GUI's, I prefer CLI
```
arecord -r 192000 -f s16_le --buffer-time=1 - | aplay -

``` 
Will record and play your mic at the same time....that is if your card supports it.

---

### Post by johnaaronrose on 2023-11-04
How do I find out if the sound card is bi-directional?

---

### Post by #&amp;thj^% on 2023-11-04
Run that code in post #3

---

