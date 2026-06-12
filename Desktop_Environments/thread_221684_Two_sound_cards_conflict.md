---
title: "Two sound cards conflict?"
date: 2006-07-23
forum: Desktop Environments
---

### Post by alrymala on 2006-07-23
Hi all! This is my situation, I have two sound cards in my system. One on-board and a PCI one. I currently use the PCI and have it selected as my default sound card in System/Preferences/Sound. When I play music through amaroK every works fine. Here the problem, whenever I load a video through Firefox, no sound whatsoever. The video plays fine. Even sites like youtube.com plays no sound for vids, and I believe it's all Flash. I have a feeling it's got something to do with my sound cards.

Anybody got a similar problem or can help?

Thanks! :-D

---

### Post by cwaldbieser on 2006-07-23
> **alrymala said:**
> Hi all! This is my situation, I have two sound cards in my system. One on-board and a PCI one. I currently use the PCI and have it selected as my default sound card in System/Preferences/Sound. When I play music through amaroK every works fine. Here the problem, whenever I load a video through Firefox, no sound whatsoever. The video plays fine. Even sites like youtube.com plays no sound for vids, and I believe it's all Flash. I have a feeling it's got something to do with my sound cards.

Anybody got a similar problem or can help?

Thanks! :-D

Try from the command line:
```

$ FIREFOX_DSP=artsdsp firefox %u

```
You may have to change "artsdsp" to the sound driver you are using (e.g. "aoss", "esddsp", etc.).
If that works, you can just change your shortcut to use that modified environment variable.

---

