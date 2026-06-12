---
title: "Odd XMMS issue."
date: 2005-10-13
forum: Desktop Environments
---

### Post by InsomniacUK on 2005-10-13
When I had Hoary Hedgehog installed, I used XMMS as my main media player, and would like to continue to do so. There is an odd bug that seems to have appeared in Breezy though.

When I go to the Add -> File menu from the playlist menu and attempt to load some files from disc, instead of seeing the disc structure, XMMS displays just, "Track01.cda".

Is anybody else having this problem?

Any idea how to fix it?

Thank you for any help or advice offered. :)

---

### Post by Wolki on 2005-10-13
[QUOTE=InsomniacUK]When I go to the Add -> File menu from the playlist menu and attempt to load some files from disc, instead of seeing the disc structure, XMMS displays just, "Track01.cda".
[/QUOTE]

Unless it's a AAudio cd this is quite weird bahavior... Can you open the cd in nautilus? And if you do, what happens if you drag a file from ther into xmms?

---

### Post by InsomniacUK on 2005-10-14
[QUOTE=Wolki]Unless it's a AAudio cd this is quite weird bahavior... Can you open the cd in nautilus? And if you do, what happens if you drag a file from ther into xmms?[/QUOTE]

The discs will open fine in Nautilus, and dragging and dropping into the XMMS playlist window works fine. That's actually how I am loading media into XMMS at the moment.

After playing around, it seems to only happen with version **1.2.10+cvs20050209-2ubuntu2**. As a test, I uninstalled this version and replaced it with an older version from apt-get.com and the bug disappeared.

It's a bit annoying, because XMMS is my preferred media player. I'm a Windows convert and miss Winamp. :razz:

---

### Post by Stormy Eyes on 2005-10-14
Have you tried Beep Media Player (sudo apt-get install beep-media-player) It works similarly to XMMS, loads XMMS and Winamp skins, and might not run into the same issues loading songs from a CD.

---

### Post by InsomniacUK on 2005-10-14
[QUOTE=Stormy Eyes]Have you tried Beep Media Player (sudo apt-get install beep-media-player) It works similarly to XMMS, loads XMMS and Winamp skins, and might not run into the same issues loading songs from a CD.[/QUOTE]

That sounds perfect, i'll give it a try, thanks! :)

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=InsomniacUK]That sounds perfect, i'll give it a try, thanks! :)[/QUOTE]

No problem. I can't help much with it, though, since I don't use it. I stick with rhythmbox. :)

---

### Post by InsomniacUK on 2005-10-14
[QUOTE=Stormy Eyes]No problem. I can't help much with it, though, since I don't use it. I stick with rhythmbox. :)[/QUOTE]

Just installed Beep and it's working great. Works with AudioScrobbler too. :)

---

