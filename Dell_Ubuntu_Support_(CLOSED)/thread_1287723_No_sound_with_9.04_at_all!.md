---
title: "No sound with 9.04 at all!"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dweaver81 on 2009-10-10
of Course, I'm a noob.  But I don't care about that.  What I do care about is why Ubuntu doesn't play anything at all through my speakers or headphone jack. I want to say its a hardware issue, but i was hoping that there are other people with the same issue out there that may have an idea.

I own a Dell Inspirion 1501.  I know, its not the newest thing out, but it works overall.  I just need to hear my tunes!  Pc speaker works fine.

---

### Post by coffeeaddict22 on 2009-10-11
Have a look [ here on the wiki]("https://help.ubuntu.com/community/SoundTroubleshooting") where there's a fairly comprehensive description of getting sound working on a Dell Dimension.

---

### Post by ugm6hr on 2009-10-12
Give us some info Re: audio hardware,

```
lspci
lshw -class multimedia
```

Generally, all it takes is an adjustment of he settings / volumes / mute in alsamixer

---

