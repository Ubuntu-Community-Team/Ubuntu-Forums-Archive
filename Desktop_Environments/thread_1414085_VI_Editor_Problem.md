---
title: "VI Editor Problem"
date: 2010-02-23
forum: Desktop Environments
---

### Post by LittleU on 2010-02-23
Hi,

I Just installed Ubuntu 9.10.

When i type some program in vi Editor the arrow keys(left,right,up,down) are not working correctly. when i type them its writing some characters in the editors rather than moving accordingly.
 

( when i press up arrow its writing a )
( down arrow b)
( left arrow d )
( right arrow c)

is this the problem with the keyboard layout or i need to install some pkg.
  
please some one help me solving this problem.

Regards,
LillteU

---

### Post by lloyd_b on 2010-02-23
> **LittleU said:**
> Hi,

I Just installed Ubuntu 9.10.

When i type some program in vi Editor the arrow keys(left,right,up,down) are not working correctly. when i type them its writing some characters in the editors rather than moving accordingly.
 

( when i press up arrow its writing a )
( down arrow b)
( left arrow d )
( right arrow c)

is this the problem with the keyboard layout or i need to install some pkg.
  
please some one help me solving this problem.

Regards,
LillteU

It's a problem with terminal handling with the "vim-tiny" package that's installed by default.  I'd suggest installing a less minimal version of vim ("sudo apt-get install vim" or "sudo apt-get install vim-full"), which will fix that problem, plus add support for things like syntax highlighting.  Alternately, "export TERM=ansi" before invoking 'vim' should get you correct terminal handling.

Lloyd B.

---

### Post by LittleU on 2010-02-24
Any ways thanks,

my editor is working fine now.
I  installed vim-rnutime and vim . 

Thanks,

---

### Post by yaprak on 2010-10-13
I had this problem,too and I had searched solution very much but I saw your writing and applied , my problem is solved. &#305; want to share with you :)  thank you very much...

---

