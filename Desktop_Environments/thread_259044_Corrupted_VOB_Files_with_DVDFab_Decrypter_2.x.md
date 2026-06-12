---
title: "Corrupted VOB Files with DVDFab Decrypter 2.x"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Corp_Punisher on 2006-09-16
Well, I finally got DVDFab to actually launch and decrypt a DVD (One that even DVD Decrypter should do, but I used it as a first run test for DVDFab). 

The cached results would not play, and the initial analysis in DVD Shrink was way too fast. As I previewed the Shrink results in the DVD Shrink program, many of the files appeared totally green and unviewable. The same was true when using Totem to actually play the movie. 

I placed around 19 dlls and one drv file from my WinXP installation into my .wine/dosdevices/c:/windows/system32 folder which helped to get DVDFab to actually work. I also updated my NVidia driver for Ubuntu Dapper, which works perfectly. 

The only issue is the poor decryption results so far with DVDFab 2.x 

Would DVDFab 3.x beta do better? It appears to work in Ubuntu from what I've seen on the Ubuntu forum. 

Also, I have been wondering if it might be good to go ahead and copy all genuine WinXP system and system32 files into my .wine installed /system and /system32 folders? Has anyone ever tried that?

P.S. I have the newest codecs and such that allows the viewing of store bought DVDs.

---

### Post by orb9220 on 2006-09-16
No not all windows dll's are compatible with wine. If installed w32codecs from automatix or easy ubuntu that should suffice.

And I ripp all my movies 650+ so far with dvdshrink under wine. Why do you use dvd decrypter since that adds an extra step?

And yes I hear that ver3 DVDFab works with wine.

---

### Post by Corp_Punisher on 2006-09-16
I've primarily used to use DVD Decrypter to do the Decryption and then Compress with Shrink simply because more than half of the DVDs could not be decrypted with Shrink. So I just made the habit of using both as a procedure (especially in teaching my sister to use these programs so she has one method to get used to). Also, I hate starting one process like DVD Shrink, just to have it fail first, and then switch to a different decrypter.

But now, with many DVD encryptions beyond even DVD Decrypter, I have turned to DVDFab Decrypter in WinXP which works very well, and then shrink to a single layer. So with those types of current issues I need something like DVDFab Decrypter and want to be able to do more of this in Ubuntu and less in Windows.

Another possible wrench:
I just read a post under General that states ver 3 beta works in wine, but this guy is having the same issues I am with a corrupted decryption result. Looks like the same type of result too.

Thx Orb for responding. I appreciate that, and also the past responces you've made to my queries.

---

### Post by orb9220 on 2006-09-16
I guess I am not getting the latest encryption dvd's. I have ripped like 650+ movies and all with shrink.

---

