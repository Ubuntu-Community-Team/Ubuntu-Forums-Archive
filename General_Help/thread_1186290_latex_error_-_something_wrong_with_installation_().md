---
title: "latex error - something wrong with installation (?)"
date: 2009-06-13
forum: General Help
---

### Post by annec on 2009-06-13
Hi and thanks in advance for the help

I just installed ubuntu 9.04 and I'm a beginner with linux.
I'm having a problem compiling a file in latex. Error states: "I can't write file on <mainfile>.log" after using command latex <mainfile.tex>.

I thought I had installed the right packages namely tetex-base tetex-bin tetex-extra and of course I installed latex.

However, I might just have forgotten something. Can't find the answer on the forum.

Thanks!

---

### Post by annec on 2009-06-13
I found the problem. So for the record, I don't understand why, but one has to run command latex as a administrator, i.e. command sudo latex <file.tex> works just fine.

I'm interested in knowing why though, because I have been using other linux machines where latex <file.tex> was enough. What does it depend on? 
Thanks

---

### Post by hugmenot on 2009-06-13
You don't have write permission in that folder. Or you don't ave write permission on these particular files.

It&#8217;s never necessary to run latex as root (with sudo).  Just make sure that you make your own user the owner of the files you work on.

---

### Post by annec on 2009-06-13
I thought something was not quite right with having to run latex with sudo... I'll look up this permission thing then.

Thanks for the answer!

---

### Post by unutbu on 2009-06-13
annec, tetex is no longer being developed. Nowadays, texlive is the right package to install for a modern, complete TeX system.

The tetex packages are only there so users with old systems can continue using their old system. Since you've recently installed Ubuntu 9.04, there should no harm and plenty of advantages to installing texlive instead.

So I would recommend that you open a terminal (Applications>Accessories>Terminal),
type
```

dpkg --get-selections | grep tetex
```

This will list all the tetex packages you've installed. Then go to Synaptic (System>Admin>Synaptic) and remove each of those packages.

Then install the texlive package (this can also be done with Synaptic).

Once you've done so, you should be able to run
```

latex file.tex
```

without using sudo. 

If you cannot do so, it might mean that file.tex is owned by root, not you, qua normal user. 

To make sure you own file.tex, type
```

sudo chown $USER:$USER file.tex
sudo chmod o+rw file.tex           # Gives you read/write permission.
```

---

### Post by annec on 2009-06-13
Excellent! It works perfectly now! 
I learned quite a lot within those lines you wrote :) (starting with the existence of Synaptic). 

Thank you so much for taking the time. 
Genuinely, it's really nice of you 'forums helpers' to look into our silly beginners problems! Indeed even when one's ready to read all about linux, it's not that easy to start with. 

Thanks again, both of you!

---

### Post by unutbu on 2009-06-13
Glad to be of help... and welcome to the forums.
I agree that Linux's learning curve can be very steep. 
Hopefully the forums can help smooth out some of the bumps.

---

