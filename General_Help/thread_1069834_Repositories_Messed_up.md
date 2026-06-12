---
title: "Repositories Messed up"
date: 2009-02-14
forum: General Help
---

### Post by celtic426 on 2009-02-14
Hey,

In attempt to install Miro, I followed these instructions: [http://www.getmiro.com/download/for-ubuntu/index.php]("http://www.getmiro.com/download/for-ubuntu/index.php").  

But after I added their line to my third party software list, now when I reload the synaptic I get this message: 

"Failed to fetch [http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

I get this when I try to use the update manager too.  I took the line I added for miro, but still I get the same thing.  What else can I do?

---

### Post by hyper_ch on 2009-02-14
you can use my generator in my sig.

---

### Post by celtic426 on 2009-02-15
Thanks hyper_ch, I think the problem might have been ultamatix.  I just deleted all the stuff ultamatix added in to my sources.list.  After taking all that out the problem went away.  

Question, will I lose the ability to update the programs that I installed with ultamatix now that I removed that stuff from the list?

---

### Post by hyper_ch on 2009-02-15
no clue what's in ultamatix but it seems like you won't be able to update them.

---

