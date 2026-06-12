---
title: "Why does Ubuntu use vim-tiny instead of VI?"
date: 2009-02-07
forum: General Help
---

### Post by uberlinux on 2009-02-07
This has always been an annoyance for me, and there's a thread fixing it here:  [http://ubuntuforums.org/showthread.php?t=636601](http://ubuntuforums.org/showthread.php?t=636601)
Fix is:  sudo apt-get remove vim-tiny, sudo apt-get install vim.

My question is:  Why does Ubuntu use VIM-tiny (aliased to vi), rather than vi "classic"?  This seems to trip up a lot of vi users, and I've not seen another distro choose to do this.  I see what the downsides are firsthand, but what are the *wins*???

Thanks,

 - Kodiak

---

### Post by spiderbatdad on 2009-02-07
ftw vim-tiny is tiny...smaller than nano. I think Ubuntu's primary movement is toward desktop environment and so, gui. uber-users should delight in remedying the command line editor short-comings

---

### Post by mb_webguy on 2009-02-07
Vi has a terrible user interface.  It's one of the most difficult editors I've ever had the displeasure to use.  I still have nightmares of using vi from years ago when I worked on an Aix server through telnet.

Vim, as the name suggests, is an implementation of vi with numerous improvements, though its still not as easy to use as nano in my opinion.  Vim-tiny is conveniently small, yet offers the basic functionality you'd expect from a text editor.  Vim-tiny is preferable to other text editors when installing Linux on small storage device such as a USB flash drive, or on computers with very limited system resources.

---

### Post by dcstar on 2009-02-08
> **mb_webguy said:**
> Vi has a terrible user interface.  It's one of the most difficult editors I've ever had the displeasure to use.  I still have nightmares of using vi from years ago when I worked on an Aix server through telnet.
......

vi = **V**irtually **I**mpossible to use....... ;)

---

### Post by heindsight on 2009-02-08
vim may be slightly confusing for complete beginners, and it does take some getting used to, but once you've learned how to use it, it is infinitely more powerful than the likes of nano or gui editors like gedit.

If you do a lot of text editing then a basic editor just isn't good enough, you need something with the the power of vim (or emacs, if you're that way inclined).

---

### Post by mb_webguy on 2009-02-08
> **heindsight said:**
> vim may be slightly confusing for complete beginners, and it does take some getting used to, but once you've learned how to use it, it is infinitely more powerful than the likes of nano or gui editors like gedit.

If you do a lot of text editing then a basic editor just isn't good enough, you need something with the the power of vim (or emacs, if you're that way inclined).

Pardon me while I pull the stitches out of my sides.

I used vi *everyday* for *three years*, coding FORTRAN and C++ on an AIX server.  I think that was plenty of time for me to have "gotten used to it".  It sucks.  If you do a lot of text editing, then you need an editor that has an intuitive interface that actually *helps* you to use its functionality rather than concealing that functionality from you with an obscure and completely unintuitive interface.

So what if nano doesn't have every tiny bit of the functionality of vi.  With nano, I can be in the eighth hour of a marathon coding session at 3:00am, barely coherent, and still do what I need to do without screwing things up because I momentarily forgot what mode I'm in, or beating my head against the keyboard because I can't *quite* remember the exact obscure command I need to do an otherwise simple task.

---

### Post by madverb on 2009-02-08
[http://www.swaroopch.com/notes/Vim](http://www.swaroopch.com/notes/Vim)

---

### Post by mb_webguy on 2009-02-08
Actually, I'd like to apologize *slightly* for my previous post.  I misread heindsight's post, and thought he was talking about vi, not vim.  Vim is still vi, but it *is* an improvement.  I *wish* I'd had the option of using vim back then...  

(Though nano would still have been even better.  I was serious about beating my head against the keyboard.  I have scars. ;) )

---

### Post by heindsight on 2009-02-08
> **mb_webguy said:**
> Actually, I'd like to apologize *slightly* for my previous post.  I misread heindsight's post, and thought he was talking about vi, not vim.  Vim is still vi, but it *is* an improvement.  I *wish* I'd had the option of using vim back then...  

(Though nano would still have been even better.  I was serious about beating my head against the keyboard.  I have scars. ;) )

well I've been using vim every day for seven or eight years, coding C, C++, java, python, bash and writing latex documents. I can't say that I ever found it unintuitive or obscure.

Of course I've had to spend some time learning new commands, but that was time well spent because once I'd learned the commands, they saved me countless hours of drudgery.

I can't see myself ever being satisfied with another editor. But, to each his own. That's the beauty of GNU/Linux and Free software in general, isn't it? If you don't like vim then there are plenty of alternatives - and if you don't like any of them you can create your own (or modify an existing editor to better suit your needs).

---

### Post by neur0 on 2009-02-08
Actually, what the OP is asking, i think, is why is vim-tiny installed by default instead of vim-full.
I know vim-full has more dependencies, but I don't know the exact reason why.
But some other distributions are implementing their vis much weirder then Ubuntu like Fedora 10 which doesn't have a binary called vim at all, only vi which is actually vim, so you can only invoke vim by vi.
I think the big difference is syntax highlighting, though I'm not sure since I don't code, so I use vim (vim-tiny) all the time only to edit config files and maybe write some quick notes and I don't need more then that.

---

### Post by mechanic on 2009-02-08
> **neur0 said:**
> Actually, what the OP is asking, i think, is why is vim-tiny installed by default instead of vim-full.

I think the clue is in the name! All those syntax and color files take up a lot of room.

m.

---

### Post by heindsight on 2009-02-08
Yeah, I suspect vim-tiny is installed by default simply because vim proper would take up too much space on the CD. It would be nice to have proper vim installed by default, but I guess anyone who's experienced enough to be comfortable with vi(m) shouldn't have any difficulty installing it...

---

