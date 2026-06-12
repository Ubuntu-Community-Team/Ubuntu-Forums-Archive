---
title: "use debian for vim"
date: 2007-03-08
forum: Desktop Environments
---

### Post by yigal.weinstein on 2007-03-08
I am a vimmer

I have plain text database of everything important to me.  Its nice because I can search through my information with grep and all other bash tools available on the command line.  It irritates me a bit that vim is 7.035 in edgy not a huge deal but enough of a deal to try and upgrade.

Today I added a debian repository to /etc/apt/sources

```
sudo aptitude update
```

and installed vim 7.0.122. :) 

It works as far as I am aware without flaw.  Just though for anyone interested this work well.  I use vim-latexsuite this works no problem and all ctags etc are working.  So if you want nearly the bleeding edge for vim then this works very nicely - As most people who know would expect it too :) best

---

### Post by saphil on 2007-03-08
Cool..  So you have gotten VIM 7.1.x or did you actually back up?
I usually use VIM for configurations and quick notes.  My clients are always sending me word docs, so I am driven to OpenOffice to read and respond to those.

Do you have  any tips for intermediate level and beyond for VIM use?

-Wolf

---

### Post by yigal.weinstein on 2007-03-09
Don't back up, but I don't think there are really any reasons to do it.  vim 7 is vim 7.  Ubuntu does almost nothing to the vim package from Debian so I knew it would work but for a light hearted Linux treat I decided to indulge.  

I too use OOo for m.doc documents.  But for notes I keep for myself, latex, and programming its vim all the way.  [www.vim.org]("http://www.vim.org") is really quite good for tips and scripts.

---

### Post by maxamillion on 2007-03-09
I might be getting ahead of myself by saying that you got lucky with it functioning perfectly, but I have just always been told ever since my transition from debian to ubuntu that the two don't tend to mix all too well in the sense of repositories and packages.

(though this apparently isn't always true)

.... just a thought.

---

### Post by yigal.weinstein on 2007-03-09
It has nothing to do with luck.  It has to do with the structure of vim and its dependencies.  vim just doesn't have many and the file structure is exactly the same for both Ubuntu and Debian.  

If it were something else - like trying to install for instance OOo from Debian then that would probably break and visa versa trying to install Gnome 2.16 from Ub. in Debian would break Debian but vim is not really changed from these two distributions.  

It kind of bothers me in a way that Ubuntu developers seam to not realize that there are simple useful programs that are not going to break by porting and are virtually bug free, and a small but reasonably sized population of its users use these packages.

I end up making my own version of f-spot, maxima, and a few others.  I just didn't want to build vim from scratch why bother when Debian has it available.

---

### Post by maxamillion on 2007-03-09
I don't think it has to do with "not porting", I believe it has more to do with the time line of the development cycle and when package freezes happen.

Example: debian sarge is their "stable release" ... how old are the packages in that branch?

Don't get me wrong, I love debian and when I need stability I can rely on, debian stable can't be beaten but lets not go blaming Ubuntu developers because some time has passed since the last package freeze.

---

### Post by yigal.weinstein on 2007-03-09
Debian testing for many purposes is more stable than Ubuntu, even Sid with just the basics is arguably more stable than Edgy.  Testing has far newer packages related to programming.  

It cannot be argued that Ubuntu is a frozen 6 month developed Debian Sid any longer.  Edgy uses Gnome 2.16 which as most informed people on this site know is not in etch which came out many months after Edgy.  In fact Gnome 2.16 isn't even in the experimental section of Debian.

Feisty is using a 2.6.20 kernel and Sid is using a 2.18 kernel now and was using a similar kernel months ago.  They are very different beasts now.  This is fine with me.  What isn't fine is that packages that I want are being outdated with very little need.  Not only this but some of the packages Feisty has are already outdated, notably Maxima which is 5.12 but I believe is 5.10 in Feisty.  This is simply unnecessary.

---

### Post by yigal.weinstein on 2007-03-09
THANK YOU DEVELOPERS :) :) :) 

That is great you just upgraded vim :) :) and libgphoto :) that is awsome 

I bow humbly before you, best thank you again - I really do like Ubuntu.

---

### Post by yigal.weinstein on 2007-03-09
just did the 

aptitude update
aptitude upgrade

a few minutes ago 7.0.164 making me proud there we go, beautiful 
you guys are awsome.

---

### Post by Crooksey on 2007-03-09
> **maxamillion said:**
> I might be getting ahead of myself by saying that you got lucky with it functioning perfectly, but I have just always been told ever since my transition from debian to ubuntu that the two don't tend to mix all too well in the sense of repositories and packages.

(though this apparently isn't always true)

.... just a thought.

++

Couldn't you just compile it?

[http://www.vim.org/download.php](http://www.vim.org/download.php)

---

### Post by yigal.weinstein on 2007-03-09
Thanks for reading what I wrote

> I end up making my own version of f-spot, maxima, and a few others. I just didn't want to build vim from scratch why bother when Debian has it available.


> **Crooksey said:**
> ++

Couldn't you just compile it?

[http://www.vim.org/download.php](http://www.vim.org/download.php)

---

### Post by Crooksey on 2007-03-09
Sorry missed that...

My vim was just updated aswell, I typed my first response the got an update.. kinda creepy.

---

### Post by yigal.weinstein on 2007-03-09
People listen to what i have to say, ha ha ha

---

