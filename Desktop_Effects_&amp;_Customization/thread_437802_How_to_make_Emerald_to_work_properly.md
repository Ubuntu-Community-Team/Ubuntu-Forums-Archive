---
title: "How to make Emerald to work properly"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by JKoder on 2007-05-09
Hello
I think that with Ubuntu 7.04 alot of people have problems getting Emerald Window decorator to work.
I mean it's working but the window borders are invisible.

If you have Beryl setup and working and you only need to Make emerald work here is a simple trick.

One important package is missing in Ubuntu 7.04 repository (since i'm using x64 i only know it does not appear in this repositories ). And that package is beryl-xgl.

Now, from the attachment get that file, unzip it and put it in /usr/bin folder. Now restart your emerald window decorator ( mabye X i dont know for sure ) and try again.
At this point Emerald will display NICE window borders.

Hope this thread will help some people.
Please let me know if this helped you to !


P.S. the file inside the zip is 100% original, i mean it;s from an old version of bery, only one version older .
( sorry for my bad english )

---

### Post by aimran on 2007-05-09
I'm running x64 feisty.

What do you mean missing window borders? You mean there's no minimise/maximise/exit buttons? If so yeah I have that problem and when I get back home I'll try your package :)

Currently using GTK window borders instead of Emerald. Can't stand not having those buttons missing :<

---

### Post by trofim on 2007-06-25
I think JKoder means sth like here [http://ubuntuforums.org/showthread.php?t=483833](http://ubuntuforums.org/showthread.php?t=483833) in point #2.

---

### Post by mahasmb on 2007-06-26
Thanks!

This worked like a charm!

---

### Post by AriciU on 2007-06-26
Didn't work for me.

---

### Post by trstyrian on 2007-06-27
An additional step not mentioned is to run
```
sudo chmod a+x beryl-xgl
```

After making the file executable, it works great! Thanks JKoder!

---

### Post by Jonq on 2007-07-15
nvm

---

### Post by whirl on 2007-08-16
cheers for this mates. I got beryl working on my girl friends laptopwhich has ati radeon xpress200m.

---

### Post by whirl on 2007-08-17
Hmm.. It seems I was too hasty. For some reason it lost those minimize, maximize and close buttons from the windows. Quite odd. Everything else is working fine the cube and the rest but Im missing these borders. Any ideas what might have happened?

---

