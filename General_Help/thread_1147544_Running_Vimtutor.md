---
title: "Running Vimtutor?"
date: 2009-05-03
forum: General Help
---

### Post by bill516 on 2009-05-03
I use vim from time to time and I rely on vimtutor to help me repair my rusty knowledge of how it works.  Getting to vimtutor is simple.  I open a terminal, type "vimtutor" and then do those parts of the tutorial I want to review.  At least that is how it has worked in the 32 bit versions of Ubuntu I have run.

When I tried doing that in 64 bit 8.10 on my Pangolin typing "vimtutor" seemed to put me in vim rather than vimtutor, which was not what I wanted.  I assumed vimtutor was not loaded by default, but a search on Synaptic seemed to suggest that it is.

Some further poking around suggested that it appeared to reside in /usr/share/vim/vim71/tutor.  But no luck, I could not find it.

I did a search on the Ubuntu forums and ran onto a very helpful post by bodi.zazen on Feb 16, 2009 at this thread:

[http://ubuntuforums.org/showthread.php?t=1071689&highlight=new+learner](http://ubuntuforums.org/showthread.php?t=1071689&highlight=new+learner)

In essence the suggestion he made was to load vimtutor by doing:

&#65279;sudo apt-get install vim-full

Not having anything to lose I did that and it worked.  Vimtutor now works as it should.  So if you have been looking for Vimtutor in your 64 bit Ubuntu 8.10 installation this might work for you.

Note that Vimtutor evidently resides in /usr/bin.

Question:  Does anybody know why this works?

I'd feel better if I knew.  Everything I read says that vimtutor is installed by default with Ubuntu.  So what did "install vim-full" do that the default installation did not do?

---

### Post by thomasaaron on 2009-05-04
I've got vim-common and vim-tiny installed by default on Intrepid 32-bit. I had to install vim-full to get vimtutor.

---

### Post by bill516 on 2009-05-05
Thanks Thomas, much appreciated.  As popular as vi/vm are in the Unix/Linux world, would it be a good thing for System76 to just do the vim full install on the machine as it ships?  Or perhaps a note on the tech support site?

Just a thought.  Have a good day!

---

### Post by thomasaaron on 2009-05-05
I so see your point. But we try to only install software above and beyond a default Ubuntu installation if it is necessary to support a piece of hardware.


For instance, we install the fprint project software to support the fingerprint readers.

I guess if there was enough demand for it, we probably would strongly consider it. But, so far, you're the only person to ever suggest it (to my knowledge).

And I can just see the backlash: Emacs fans in an uproar!:lolflag:

---

### Post by bill516 on 2009-05-05
I surrender!  There's no Emacs like a mad Emacs!

---

### Post by go_beep_yourself on 2009-12-13
[IMG]http://lca2srv30.epfl.ch/sathe/data/emacs_learning_curves.png[/IMG]

---

### Post by cgul1 on 2010-04-24
incase anyone is coming across this later
installing 'vim-full' did not work for me to get vimtutor to work, however install vim did work in Ubuntu 10.4 RC

---

