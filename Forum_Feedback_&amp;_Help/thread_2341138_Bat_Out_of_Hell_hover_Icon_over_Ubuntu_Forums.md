---
title: "Bat Out of Hell hover Icon over Ubuntu Forums"
date: 2016-10-25
forum: Forum Feedback &amp; Help
---

### Post by ventrical on 2016-10-25
Ok..:) When I hover over the Ubuntu Forums header on the Left Top page of FireFox a 'bat' shows up. Is this a fun halloween joke or am I seeing things:)

[https://www.youtube.com/watch?v=pRqBn2kBxXQ&feature=youtu.be](https://www.youtube.com/watch?v=pRqBn2kBxXQ&feature=youtu.be)

Regards..

---

### Post by slickymaster on 2016-10-25
> **ventrical said:**
> Ok..:) When I hover over the Ubuntu Forums header on the Left Top page of FireFox a 'bat' shows up. Is this a fun halloween joke or am I seeing things:)

Regards..

No, or better yes, you're seeing thins, like a bat. :)

Like in previous years he have a bat leaving the forums dungeons and joining us in this season.

---

### Post by ventrical on 2016-10-25
Bwwahahahahahaha.. :)

kewl

---

### Post by bearlake on 2016-10-25
It's back! :)

---

### Post by sudodus on 2016-10-25
batterflies :-)

---

### Post by lisati on 2016-10-25
Beware of the black cat! :D

---

### Post by &amp;KyT$0P# on 2016-10-26
> **Bucky Ball said:**
> If you're serious, very doubtful. Report this in Forum Feedback and Help or the 'report forums bugs' thread rather than bringing it in here. Thanks.
So, continuing here as requested.

> If you're serious, very doubtful.
Bucky Ball, why do you say that?  Looking at the code -
```
a.logo-image:hover {
    cursor: url("[COLOR="#FF0000"]**http:**[/COLOR]//i.imgur.com/GljsZSe.png"), pointer;
}
```

For what it's worth, that URL does load over https.

---

### Post by &amp;KyT$0P# on 2016-10-30
^ Seems to be working again now :D
```
a.logo-image:hover {
    cursor: url("https://i.imgur.com/odkQswu.gif"), pointer;
}
```

In case the issue is browser-specific, I'm using SeaMonkey but spoofing other browser/OS. (currently Chrome 53 on Mac OS X 10.12 - and according to login.ubuntu.com information, it was spoofing Chrome 53 on Mac OS X 10.9.5 when I last saw the issue)

---

