---
title: "Steam on Linux not loading properly"
date: 2015-08-02
forum: Gaming &amp; Leisure
---

### Post by ogdencam on 2015-08-02
I'm using Ubuntu 14.04 with an Intel i5-3210M CPU and a Intel HD4000 GPU.
When I load Steam, the first issue is that the store fails to load, it just has a black screen and the loading icon. Of the 4 tabs (Store, Library, Community, and my profile) only content under Library loads. When viewing my library, it says none of them are downloaded even though they are. When I try to install any game, it says there is not enough space despite having over 90 gigs available.


Using steam --refresh to refresh the files didn't fix it.
Changing whether I'm opted in or out of Steam beta does nothing.


Any help would be appreciated, let me know if you need me to provide anymore information.

---

### Post by efflandt on 2015-08-03
Those symptoms happened for kernel 3.13.0-59-generic, which resulted in problems for Steam, wine, and other things. It would work if you either boot the previous -58 kernel, or run **Software Updater** which should update to 3.13.0-61-generic which works.

---

