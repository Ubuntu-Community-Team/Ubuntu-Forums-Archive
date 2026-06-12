---
title: "'X' on desktop at boot"
date: 2004-10-18
forum: General Help
---

### Post by caymran on 2004-10-18
Strange problem, more of a nuisance actually.  Everytime Gnome loads, after the panel loads there is an unmobile 'X' in the exact center of the desktop, Like back in the old days (of linux) when you started X, the 'X' was your mouse then it changed into a regular mouse cursor/arrow.  

I have both, I have my mouse cursor/arrow, and the 'X' that stay on top of whatever window I bring up, unless I move the window underneath it (seems like it causes the screen to refresh, and the 'X' dissappears).  

What is causing this, and do others have this issue, any advice would be appreciated, (other than open a window and shift it around to make it go away everytime I boot).  

Thanks,
Caymran

-by the way, I am running Ubuntu on my Compaq presario 710us with my microsoft mn-720 wireless card using ndiswrapper, it works like a champ.  Love Debian, and the simplicity Ubuntu brings to it.

---

### Post by caymran on 2004-10-18
I just ran into the old [ post](http://www.ubuntuforums.org/viewtopic.php?t=494) that mentioned trying the "SWCursor on", and am trying it now.  I'll let you know how it goes.

  -it did not work, and turns out I have the same vid card as the other guy.  Any help, new/additional info would be appreciated.

---

### Post by Geekboy on 2004-10-18
Yeah, I still get it.  I do notice that if I launch FIrefox, then click on the top border of the browser, the X goes away.

Anyone have any ideas on how to get rid of this problem.  I've used tried several versions of Linux and never had this.

---

### Post by emamarro on 2004-10-19
same for me...  
 [http://www.ubuntuforums.org/viewtopic.php?t=1234](http://www.ubuntuforums.org/viewtopic.php?t=1234)

---

### Post by kazpox on 2004-10-20
Hi. Just wanted to add that I have the same problem on my Packard Bell E1245. I'm afraid I don't have the solution, though.

---

### Post by oohlaf on 2004-10-20
I have the same problem with a Savage S3 card if I use software cursors.

Just disable the hardware cursor in your XF86Config-4.

```
Section &quot;Device&quot;
        Identifier      &quot;S3 Inc. 86C270-294 Savage/MX-MV&quot;
        Driver          &quot;savage&quot;
        Option          &quot;HWCursor&quot;              &quot;false&quot;
EndSection
```

---

### Post by Geekboy on 2004-10-20
> I have the same problem with a Savage S3 card if I use software cursors.

Just disable the hardware cursor in your XF86Config-4.

```

Section &quot;Device&quot;
        Identifier      &quot;S3 Inc. 86C270-294 Savage/MX-MV&quot;
        Driver          &quot;savage&quot;
        Option          &quot;HWCursor&quot;              &quot;false&quot;
EndSection
```


That worked!!   :D   Thanks alot!

---

### Post by caymran on 2004-10-21
Worked flawlessly, 

Thanks a million,
Caymran

---

