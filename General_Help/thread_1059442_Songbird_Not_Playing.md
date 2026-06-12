---
title: "Songbird Not Playing"
date: 2009-02-03
forum: General Help
---

### Post by JK3mp on 2009-02-03
Not extremely new to ubuntu been using it a couple months and i've used fedora core before but Ubuntu works WAY better with the hardware for my laptop. But im having a problem with songbird not playing that songs. It skips through them as if maybe it doesn't have the codecs but from what i've heard it should come prepared with mp3 codecs, the songs in my songlist consist of mp4a's,mp3's, AND wma's. The wma's and mp4a's wasn't a suprise but mp3's i figured should all work right from the download. Any suggestions on how to fix this problem for me? Im running Ubuntu hardy if it makes much diffrence. I am planning on upgrading to 8.10 sometime in next week.

---

### Post by Crafty Kisses on 2009-02-03
Does music work on any other programs like VLC?

---

### Post by JK3mp on 2009-02-03
Yes it does. VLC player works pefectly fine but i would prefer songbird. ITs gotta be a setting in songbird im thinking but im just not sure what...thator an add on im missing :S

---

### Post by Crafty Kisses on 2009-02-03
Try running Songbird in the Terminal and see if you get any errors.

---

### Post by JK3mp on 2009-02-03
It runs fine but when i play a song it gets continuous exception errors with ns_ERROR and some database query text or something :S

---

### Post by JK3mp on 2009-02-03
ended out with an error like this. 
```
ERROR! Could not call boundObserver.observe(). 
Key = metadata.title
[Exception... "'[JavaScript Error: "observer.onDataChanged is not a function" 
{file: "chrome://songbird/content/bindings/observesDataRemote.xml" line: 204}]'
 when calling method: [nsIObserver::observe]"  
nsresult: "0x80570021 (NS_ERROR_XPC_JAVASCRIPT_ERROR_WITH_DETAILS)"  
location: "JS frame :: file:///opt/songbird/components/sbDataRemote.js :: anonymous :: line 326"  data: yes]
```

---

### Post by JK3mp on 2009-02-04
Any idea's anyone?

---

