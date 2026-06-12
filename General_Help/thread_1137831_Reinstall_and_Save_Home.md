---
title: "Reinstall and Save Home"
date: 2009-04-25
forum: General Help
---

### Post by bkanuka on 2009-04-25
Just a quick question. I know this has been asked before, but never answered in the way I was looking for.

I'm reinstalling Ubuntu but want to save EVERYTHING in my home folder including .* folders and well, every file and folder.  Problem is, I cannot just backup externally (I have about 170GB home folder, and no external drive big enough), nor can I not format home partition because I do not have a home partition.

If I run through the Ubuntu Installer normally and choose to import settings (and not reformat anything), will EVERYTHING in my home folder be saved (assuming the install goes swimmingly)?

No .* folders overwritten, and not just things in ~/Documents, etc. Will ~/* be intact?

---

### Post by loomsen on 2009-04-26
Hi.

Usually there are some minor changes in the config every release. So, I would suggest you create a new account and copy your settings over afterwards.
But 170GB arent only settings...

So use any graphical disc usage app, like baobab for instance to determine which folders are the main part of the story (I guess music, videos and pics?) and move them to a directory, lets say /home/MyMedia.

Now your home folder should be of a reasonable size you could easily handle.

Tho, as I said, export your main settings, like compiz for instance, and have a new account generated. You can simply import them back in when done.
If you got a lot of icons or themes or whatever installed as well to your home, consider moving them to /home/share or so.

Then upon install, choose to mount that drive under /home and keep existing data.

Just use a different username, and have thing regenerated as far as possible (importing compiz is actually the only thing I care about, Opera is synched online anyway, everything else I can live with losing, however, you wont lose anything if you create a new account, and then l8r still be able to copy what you'd like to keep over to your new acc.

---

### Post by bkanuka on 2009-04-26
So I don't think this was exactly what you were saying, but reading your post gave me an idea. I'm going to let the installer resize my current partition and make a smaller one, then use the new smaller one as / and the larger one as /home.  I think then, nothing will be touched on the /home partition.  Thanks for giving me this idea.

---

### Post by loomsen on 2009-04-26
Yep, go for it. 
Basically, 20GB should be enough (if you're a messy user) for your root partition.

Big files like media, collections of pictures and so on usually shouldnt be anywhere on your root partition.

Enjoy.

---

