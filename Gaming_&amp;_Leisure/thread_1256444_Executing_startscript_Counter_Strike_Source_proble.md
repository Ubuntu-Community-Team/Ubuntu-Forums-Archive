---
title: "Executing startscript Counter Strike Source problem"
date: 2009-09-02
forum: Gaming &amp; Leisure
---

### Post by Strega on 2009-09-02
Hello,

I've this weird problem going on.
I was able to set up 4 Counter Strike Source servers.
But my problem is that I can only execute the startupscript with root.
Well, not exactely, I can run it with my second account to because it doens't say I don't have the permission.
But the server just won't go online.
And there is no mistake in the script because when I do the exact same thing with root it does start up.
I tried to do ( with root ) chown -R user /dir/to/startscript but that still didn't work.
Any idea's how to solve this and what the problem might be?

Regards, Strega

---

### Post by Strega on 2009-09-06
No ideas ? :s

---

### Post by dfreer on 2009-09-06
I have successfully run 3-4 CS:S servers at the same time, all of them running under a limited user account (not root). So yes it can be done, the question I have is what are you doing specifically when starting your servers (what commands do you use, what additional scripts do you use, etc)?

For starters, I always ran each server from it's own directory (IIRC it's not a good idea to try to run 2 servers using the same binary). To save space I created a shared directory for all files that are pretty much read only (maps, skins, textures, etc), but you don't really want to worry about that until you get your servers set up.

---

