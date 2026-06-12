---
title: "Quake 2 defies me again"
date: 2009-08-10
forum: Gaming &amp; Leisure
---

### Post by Rogue Jedi X on 2009-08-10
So, now I have 64-bit version of Kubuntu and have downloaded Icculus' Quake 2 port and so far so good...except the sound. Thing is, I had the exact same problem back when I was on 32 bits and I solved it by creating a .asoundrc file in my homedir and pasting this in:

```
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
```

Not sure what this does exactly, but it worked like a charm! Now, I tried doing the same, only this time, I get NO sound. OpenAL is installed, before anyone asks. Any ideas?

---

