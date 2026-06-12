---
title: "unstable desktop concerns"
date: 2005-05-17
forum: Desktop Environments
---

### Post by neighborlee on 2005-05-17
...today I downloaded ( because I heard that was how to fix the weird gnome desktop crashes ive been seeing and that MaNY others have ) the nvidia driver from their site and did telinit 1 ( although the compiling gives errors about it being wrong 'level', - and frankly what init level actually does work in debian to avoid this, whereas in redhat telinit '3' does the job nicely with no nviida errors dudring compile so I WISH all distros would agree to a standard here !!) , and even though I got errors saying telinit 1 might cause erors..I never got any during the ./NV*.run session..so I then do: startx < and saw nvidia logo and gdm starting and I got into desktop fine..

I then restart the company and find that not even gdm will not load ( and the nvidia logo which tries to display only gives a black screen ).

if I do ./NV*.run again ..and then startx..things go smoothy..w-t-h is going on here ?.

Im' not sure how much more time I can devote to this problem..sure I can use the canned synaptic drivers but then im' back to a unstable system ( if you believe the forum posts)..

so i'm mass confused by now and HOPE someone enlightened out here knows what is going on here..

cheers
neighborlee

---

### Post by Stormy Eyes on 2005-05-17
If you're not going to use transparency or do 3D gaming, then you don't *need* nVidia's drivers. You might be better off using the free drivers provided by X.org with their X server ("nv" driver).

---

### Post by neighborlee on 2005-05-17
[QUOTE=Stormy Eyes]If you're not going to use transparency or do 3D gaming, then you don't *need* nVidia's drivers. You might be better off using the free drivers provided by X.org with their X server ("nv" driver).[/QUOTE]
---------------
hi and thanks for kind reply..

  I definitely need 3d drivers because I am not only a gamer but a game developer
[http://www.heartseed.org](http://www.heartseed.org)

I gotta solve this quick or i'm going to have to either go back to warty (ugh?) or face using a different distro which really bites as I really LOVE ubuntu and the community..I just can't trust stability of the packaged drivers , which according to forum posts seems to be the problem ?

much thx
neighborlee
*sigh*

---

