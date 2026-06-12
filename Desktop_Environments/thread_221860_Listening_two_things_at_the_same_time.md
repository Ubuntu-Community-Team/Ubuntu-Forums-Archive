---
title: "Listening two things at the same time"
date: 2006-07-24
forum: Desktop Environments
---

### Post by dolarsrg on 2006-07-24
Hi everyone :) 

I've a question about sound in ubuntu dapper. When I'm listening some music with Listen or with Amarok and I'm (for example) cheking my eMail or something, some times I get links to Youtube/Google Videos/Presentations for Openoffice Presentation/... I use to pause the music and open de Link, but the sound is always lost. I mean, if I've Amarok or Listen running (even in Pause mode) I can't play any sound with other programs.

Why? I'm I doing something wrong? Is a configuration problem?

I'm using Ubuntu Dapper in a Toshiba Satellite M30X with a Realtek sound card.

Thanks a lot!

---

### Post by SishGupta on 2006-07-24
The problem lies in Adobe Flash I think. 
If you watch the youtube version first, you may find that your media player does not play sound.

If there is a fix I do not know of one and I would appreciate anyone who can help. I have a thinkpad T42 with an onboard intel sound chip. I forget what its actually called, device manager doesnt list it with the right name.

I am new to ubuntu/linux and this would be my only hardware issue (wifi is excellent)

---

### Post by Kelnoky on 2006-07-24
Try this command:

```
ln -s /tmp/.esd-1000 /tmp/.esd
```

If it helps just add it to System -> Preferences -> Session and there under startup programs, then it will execute every time you boot. :)

---

### Post by dolarsrg on 2006-07-24
It seems not to work.

I'm trying listening Youtube with the Listen program running and the videos has no sound :( 

Thanks anyway ;)

---

### Post by LucidTaZ on 2006-07-24
I have the same problem. Always thought it was normal. :) It would be cool to listen to my own music and hearing sound effects of games, or whatever you want to hear, in the same time.

```
ln -s /tmp/.esd-1000 /tmp/.esd
```
Did not work for me.

---

