---
title: "brutal firefox update today"
date: 2009-04-23
forum: General Help
---

### Post by elamericano on 2009-04-23
I applied some FF update this morning, after being prompted. This time however, when it prompted to "Restore" the program segfaulted. After another reboot it finally launched, but without any prompt for restore. Damn, some of those tabs had taken a long time to track down. Oh well, I should be able to find most of it in the browser history. Oh no! It nuked my history too. Not one site is listed. Is this normal behavior for 3.0.9?

Something else that's going on is that I can't set my homepage. When it opens it's blank. And when I click home, it loads "Mozilla Firefox Start Page". I have it set to load the homepage on opening, and that page is [http://www.google.com/](http://www.google.com/). Hey, I have no bookmarks either. I must not be connected to my default profile.

OK. I backed that up. I saw that my cache and session info were owned by root, so I did "sudo chown -R myuser:mygroup ~/.mozilla" That helped. Now I'm back to:

Segmentation fault

Anyone else have problems with this? Can you recommend a fix, or explain the easiest way to reload the last version I had? Recovering data would be a bonus at this point.

Thanks.

---

### Post by por100pre1 on 2009-04-23
Open Synaptic select the package(s) you want to downgrade and press Ctrl+E. Be careful, you may need to downgrade many packages in order to work fine.

---

### Post by elamericano on 2009-04-23
Thanks. That gives me the option to go to 3.0~b5. I think 3.08 would be what I was running before the update. Maybe apt-get has something.

The problem appears to be memory. Synaptic segfaulted too the first time I ran it. Reseating the memory card I just added seems to help. Now I'll memtest.

History is back, but only one of my Windows was saved. I was collecting some news articles for research. Although they were restored before, they don't get moved to the top of history when they're reloaded that way. I don't think I'll find those again. There's probably an extension to temporarily save a bunch of tabs to look at later...

---

