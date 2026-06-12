---
title: "Desktop sound events just don't play..."
date: 2009-01-28
forum: Desktop Environments
---

### Post by MikeTheC on 2009-01-28
I've noticed in both 8.04 and 8.10 that only a very few desktop sound events seem to work at all, and then I think except for the startup and shut down ones, I can only get them to "play" when I hit the preview play button in the list.

The rest won't even work at that point. Anybody else experiencing this?

I know it's not a problem with my sound card, since I can play movies and music with no problems at all.

---

### Post by jimbog on 2009-01-28
Yep, I have exactly the same problem (Kubuntu 8.10). The only notification sound I get is the logging out music but music, films, games etc are fine.

I started a thread about this last week but didn't really get anywhere. Sorry, I haven't been using linux for very long so I can't suggest a solution...

---

### Post by XanTrax on 2009-01-28
Please try

```
alsamixer -c 0
```

command and see if anything is muted or you do not have some parts of your speakers turned off/down

---

### Post by MikeTheC on 2009-01-28
> **XanTrax said:**
> Please try

```
alsamixer -c 0
```

command and see if anything is muted or you do not have some parts of your speakers turned off/down

Everything looks normal. The only muted things are sound inputs.

---

### Post by XanTrax on 2009-01-28
> **MikeTheC said:**
> Everything looks normal. The only muted things are sound inputs.

This sounds like a similar to another users problem.  Can you first please post the output of:

```
sudo lshw -C sound
```

and

```
sudo lspci | grep -i audio
```

If the above command comes up blank, please post the output of

```
sudo lspci
```

---

