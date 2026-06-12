---
title: "How do I get Transmission to work?"
date: 2008-12-04
forum: General Help
---

### Post by gandalf2000 on 2008-12-04
I have tried for weeks to get Transmission working without posting this question.  I have tried searching these and other forums to no avail.  My problem is that Transmission doesn't seem to have a search function.  There is a box on the upper right that looks like it should be what I need but isn't.  The help contents assume that you have all functions but under the "Torrent" button there is "Add", "New" and "quit", everything else is grayed out.  Could some one please tell me what I'm doing wrong or point me to a tutorial for Transmission.  This is weird because it was working on Hardy before I upgraded to Intrepid.  I am having a similar problem with Deluge by the way, or at least I was.  Now Deluge won't even start, perhaps I hurt it's feelings the last time it wouldn't work for me.;)

---

### Post by gabril on 2008-12-04
hahaha but.... why?

$ sudo aptitude install azureus

its a java bittrrent client... very simple or very advanced.... utorrent works with wine as well... default is not allways the best!

---

### Post by aggiemarine07 on 2008-12-04
I took a look at what you were talking about in transmission and I believe that that search bar is intended to sift through the active torrents in transmission and not to search the internet for them.

I'll take a look at deluge for you in a few minutes after i install it.


I personally have used utorrent and it works great through wine, just a thought.

---

### Post by aggiemarine07 on 2008-12-04
to get deluge working you might want to delete the config file in /yourhomedirectory/.config/deluge which is called prefs.state I think. and then try to open it again. If that doesnt work try deleting the entire directory (make sure that there are not any torrents in there that you want to save though). I had that problem one time where it wouldnt start and did this and it worked.

---

### Post by gandalf2000 on 2008-12-06
Thanks for answering,guys.  First off, I have Azureus but it won't show any results for some of the searches and I know that the files are out there.  Default is not always best but I am comfortable with Transmission and had it working fine once before.

I tried that suggestion with Deluge but it didn't make any difference.  I think that I may reinstall and see if that helps.

---

