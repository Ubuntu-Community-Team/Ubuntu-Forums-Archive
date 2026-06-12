---
title: "tar fails with cryptic error message"
date: 2009-05-12
forum: General Help
---

### Post by Miles_Prower on 2009-05-12
So, I'm trying to tar up this folder (ssh in, screen, run tar -cvf home_movies.tar home_movies, disconnect from screen, go to work). The du command reports that this folder weighs 17 GB. After almost all of the files are reported to be tarred up, tar fails with this error messgae.


tar: home_movies.tar: Wrote only 4096 of 10240 bytes
tar: Error is not recoverable: exiting now


10240 bytes is not 17 GB. it's like ten k, which is over 9000, but not near the size of any of the files. furthermore, this is the exact same error I get when trying to tar up another folder of a different,  yet still large size. Has anyone ever seen this before?

---

### Post by Miles_Prower on 2009-05-13
I can't tar things. I've never been so friggin frustrated. 75 gigs I want to put on my server, and I can't even friggin compress it. Eff this.

---

### Post by Miles_Prower on 2009-05-13
it was because there was no room left on the HD. I was only able to figure it out, 'cause I'm the world's sexiest genius. Seriously, though, what kind of error message was that?

NOT VERBOSE ENOUGH, TAR CVF!

---

