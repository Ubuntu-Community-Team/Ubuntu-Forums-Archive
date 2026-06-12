---
title: "When will vim 7 hit the repositorys?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by marwal on 2006-06-09
and if i download and compile myself, could that be conflicts later?

---

### Post by FredB on 2006-06-09
[QUOTE=marwal]and if i download and compile myself, could that be conflicts later?[/QUOTE]

vim 7 is out ?!

Try to ask on backports, with a little luck ;)

And I think if you build it, it will be installed in /usr/local, so no war with the ubuntu version.

**EDIT** : build it, it installs under /usr/local and it works great ;)

No conflicts with the official version and the good point is that you can run graphical version ;)

---

### Post by neutro on 2006-06-09
I use Debian unstable on one of my computers and vim 7 got installed a few weeks ago. Just a warning: when calling vim 7 with the Debian defaults using the vi command, vim starts in the vi compatibility mode, which causes all kinds of peculiarities (e.g. insert mode is not highlighted at the bottom of the screen, backspace doesn't delete, arrow keys produce A,B,C,D instead of moving the cursor, etc.). 

The fix is to use a ~/.vimrc with the line "set nocompatible" (without quotes) in it, or call vim using the vim command and not vi.

---

### Post by FredB on 2006-06-10
[QUOTE=neutro]I use Debian unstable on one of my computers and vim 7 got installed a few weeks ago. Just a warning: when calling vim 7 with the Debian defaults using the vi command, vim starts in the vi compatibility mode, which causes all kinds of peculiarities (e.g. insert mode is not highlighted at the bottom of the screen, backspace doesn't delete, arrow keys produce A,B,C,D instead of moving the cursor, etc.). 

The fix is to use a ~/.vimrc with the line "set nocompatible" (without quotes) in it, or call vim using the vim command and not vi.[/QUOTE]

And no graphic mode using vim -g ?

Building vim 7.0 on my P4 took around 10 minutes or so... And I do like this version ;)

---

### Post by der_joachim on 2006-06-10
Elsewhere on the forums, there is [a thread]("http://ubuntuforums.org/showthread.php?t=172094&highlight=vim7") in which people made their own vim packages and posted them. I installed one of these and it works well. 

Otherwise, I'd wait for the backports.

---

### Post by FredB on 2006-06-10
Well, I had built it and it installed in /usr/local... No big deal. Backports will be a great idea :)

---

### Post by dpm on 2006-06-10
I couldn't wait for them to be backported (I'm not sure whether they will be backported at all), so I downloaded the packages from here:

[http://www.freshnet.org/debian/dapper/vim7/](http://www.freshnet.org/debian/dapper/vim7/)

They seem to work fine on dapper.

Cheers.

---

### Post by FredB on 2006-06-10
[QUOTE=desp]I couldn't wait for them to be backported (I'm not sure whether they will be backported at all), so I downloaded the packages from here:

[http://www.freshnet.org/debian/dapper/vim7/](http://www.freshnet.org/debian/dapper/vim7/)

They seem to work fine on dapper.

Cheers.[/QUOTE]

Maybe if I have to reinstall my ubuntu, I will use this link :o)

---

### Post by husky_tdawg on 2006-06-25
[QUOTE=desp]I couldn't wait for them to be backported (I'm not sure whether they will be backported at all), so I downloaded the packages from here:

[http://www.freshnet.org/debian/dapper/vim7/](http://www.freshnet.org/debian/dapper/vim7/)

They seem to work fine on dapper.

Cheers.[/QUOTE]

I installed from them, and it worked beautifully on Dapper.

---

### Post by ssmaxss on 2006-07-16
And what about amd64???

---

