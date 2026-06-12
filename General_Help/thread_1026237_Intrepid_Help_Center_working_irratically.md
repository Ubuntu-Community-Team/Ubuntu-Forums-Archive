---
title: "Intrepid Help Center working irratically"
date: 2008-12-30
forum: General Help
---

### Post by sofasurfer on 2008-12-30
As far as I know my system is working fine. 
I have know idea if the Help Center (the '?' icon at the bottom of the screen) was working properly because I rarely use it, but here is my problem.

I was manually changing permissions in my /documents directory. I got tired of this slow process and decided to go to the help center to learn how to use 'chown'.

I opened the Help Center and typed 'chown' and the clicked on a search result. The Help Center window closed. I tried many other search result links. Some of them caused the window to close. Others froze the system until I exited the window and others did nothing. When the system froze after clicking on some links, and I clicked the 'X' to close the window, it took some time as if the system was working hard.

These were search result links. But if I clicked on links on the Help Center home page (non-search results), those links would open. 

Everything else seems to work fine.

---

### Post by adult swim on 2008-12-30
hmm that is strange, it does it to me too.  i figured out what the error is but i have no clue what to do about it. Yelp:ERROR:yelp-document.c:275:yelp_document_cancel_page: assertion failed: (document != NULL && YELP_IS_DOCUMENT (document))

as an alternative, you can open up a terminal and type in ```
man chown
``` and you can replace chown with any other command you are curious about.

---

### Post by sofasurfer on 2008-12-30
I accomplished the permission changes.

I found that the Help Center issue occurs on my other Intrepid system also. It must be a linux glitch as opposed to something we did.
I also found that some links do work but after I am taken to the linked page the system freezes.

Hmmmmm....
If you learn more please post.

---

