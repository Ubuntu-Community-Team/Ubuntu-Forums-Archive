---
title: "Realplayer question"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Jerrac on 2005-10-29
I installed RealPlayer 10 with the package provided by Real. Now when I try to open a movie preview on yahoo movies, it gives me this error:
> Could not find an appropriate hxplay or realplay in the system path to use as an emmbedded player.
I assume that means I need to edit my system path to include the RealPlayer excutable I have installed. How do I do that?

---

### Post by Jerrac on 2005-11-04
Ok, I figured out that I had to put a symlink in the /usr/bin directory. Wish someone had just told me... I had to do by trial and error.

Anyway, it works now. But the movie trailers are really choppy. Even when I tell it to buffer the entire clip. So, what can I do?

---

### Post by Xian on 2005-11-04
[QUOTE=Jerrac]Ok, I figured out that I had to put a symlink in the /usr/bin directory. Wish someone had just told me... I had to do by trial and error.[/quote]

This should be done automagically. Did you tell the realplayer installer explicitly that the install path was /usr/bin/RealPlayer, and then acknowledge when prompted by the installation script to configure system-wide symbolic links?

[QUOTE=Jerrac]Anyway, it works now. But the movie trailers are really choppy. Even when I tell it to buffer the entire clip. So, what can I do?[/QUOTE]

This really sounds more like a web connection issue.
Perhaps give a direct link so we can try and reproduce....

---

