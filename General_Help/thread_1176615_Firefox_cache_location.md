---
title: "Firefox cache location"
date: 2009-06-02
forum: General Help
---

### Post by elliotbeken on 2009-06-02
hi there i would like to move my firefox cache location to a media drive which runs over a network. i have mounted the drive but if i go in to the firefox config i cant map it to a location on the drive 

can i do this and is it possible?? thanks

---

### Post by zika on 2009-06-02
> **elliotbeken said:**
> hi there i would like to move my firefox cache location to a media drive which runs over a network. i have mounted the drive but if i go in to the firefox config i cant map it to a location on the drive 

can i do this and is it possible?? thanks
open in FF page **about:config**. Find **browser.cache.disk.parent_directory** and change its value to a location You want. Restart FF. Before doing this *clear cache* from FF menu.

---

### Post by elliotbeken on 2009-06-02
i know how to add the cache location i just dont know the path i need to put in to get it to work (sorry if i was not clear)

i know this is wrong but this is what i tried "computer:///media on mediadrive" 

(the drive shows up as media on mediadrive in computer)

can someone give me a example to point me in the correct direction thanks

---

### Post by mikey.duhhh on 2009-06-07
To find your cache location type

```
about:cache
```

in Firefox.

---

