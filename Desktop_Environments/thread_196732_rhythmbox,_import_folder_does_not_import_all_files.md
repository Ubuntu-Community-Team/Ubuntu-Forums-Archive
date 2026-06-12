---
title: "rhythmbox, import folder does not import all files"
date: 2006-06-14
forum: Desktop Environments
---

### Post by olafbooij on 2006-06-14
Hi,

After upgrading to Dapper I've been having all kinds of trouble with import music in Rhythmbox. I saw on the ubuntu forums that I'm not the only one, however I did not find solutions to my problems. I will try to explain all the strange things that happened and my attempts to avoid them.

At first start of rhythmbox 0.9.3.1 that comes with Dapper Drake, rhythmbox used all the cpu to look at all the oggs/mp3s previously imported and than quited unexpectedly. By starting it from a terminal I saw that it produced a segmentation fault. I ran "rhythmbox -d" a few times and found that each time it choked on a particular ogg file. Moving this file into another directory which was never imported in rhythmbox avoided the segmentation faults (jippie!). I then could import all the music on my disc with "Import Folder" including some new music I recently acquired.

However another user on the system using rhythmbox could not import all music. After running "Import Folder" and choosing my music directory it only imported part of the music. She could import the missing music by choosing the sub-directories in the music directory by hand. However the amount is too large to do this for all missing files.

I tried removing the .gnome2/rhythmbox directory, reinstalling rhythmbox, checked that the gstreamer0.10-plugins-ugly was installed, but nothing worked. Then I noticed that the music from most artists from A to F were imported correctly (although some were not and some from G-Z were imported. I pinpointed which of the artists seemed to be the first one not imported and moved those files away. After removing the .gnome2/rhythmbox again, and starting an import again, most of the music was imported (by this other user). But again: not all music, the music that I had added recently is still not imported.

Then I decided to... write this lengthy (sorry) post.

I hope someone can point me to a solution/work-around/insight. I do not know where to search. I read in some threads that people started using newer versions of rhythmbox. Is the problem I (tried to) describe really a symptom of a bug solved in a newer release?

Kind regards,
Olaf

(Unbelievable, just before I wanted to send this post, I had a power-outage in my housee. So a final question: is rhythmbox haunted? (Luckily I wrote my post in an editor and it was saved in a swap file...))

---

