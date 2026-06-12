---
title: "Problems with thunar"
date: 2011-07-23
forum: Desktop Environments
---

### Post by The Cog on 2011-07-23
Since 11.04, a couple of things seem to be broken in thunar on windows shares that I've connected to using gigolo. 

Firstly, right-click and "Open Terminal Here" on the mapped directories is no longer an option. I can however navigate to ~/.gvfs/* and right-click open terminal that way, but it's a pain to have to do that all the time. I frequently want to do this, mainly to use grep.

Secondly, renaming or deleting files on shares doesn't show up in thunar's window until I use View->Reload. 

Thirdly (if I remember right), drag/dropping a file from thunar to an application no longer works if it's a windows share. 

These all worked in 10.10. Does anyone know of a way to correct this breakage, or whether it is likely to be fixed in 11.10?

---

### Post by Toz on 2011-07-23
Although initially I was excited about gigolo and gave it a chance, I eventually gave up on it (too buggy) and moved back to cifs mounting via smbfs. None of the problems you mention above affect me using this method.

---

### Post by The Cog on 2011-07-23
I quite like gigolo. Its most annoying feature is that although you can name servers in its bookmarks, it only lists the connected ones by IP address and I have a bad memory. I often have to go edit/bookmarks just to see which one of the connected addresses is the one I want to re-open. 

But that's beside the point. I think all the problems I describe are problems in thunar, not gigolo. I think the breakage is because gigolo now points thunar to cifs or smbfs locations (can't remember which) rather than pointing it to the .gvfs locations that gigolo creates, and thunar just doesn't handle them as well.

---

### Post by The Cog on 2011-07-27
Bumpitty-bump-bump.

---

