---
title: "RStudio"
date: 2011-02-28
forum: Education &amp; Science
---

### Post by gunksta on 2011-02-28
A new IDE for R. It's new and all I've done is play with it a little, but it looks promising. The download is deceptively large. It's a 20MB download, but after looking at the .deb, it looks like QT and the other dependencies are statically compiled with the application, so most of this is actually dependencies, not application.

[RStudio]("http://www.rstudio.org/")

---

### Post by spinoza666 on 2011-03-01
Cool!

Thanx:)

---

### Post by rg4w on 2011-03-01
Look gorgeous.  Thanks for posting that.

---

### Post by gunksta on 2011-03-01
After using this for a small project last night, I am impressed. It's not going to replace Vim or Emacs, but it does provide the sort of UI that R has needed for a long long time.

I would like to see this included in the Ubuntu repos sooner rather than later. I wonder if it is possible to squeeze it in for Natty.

---

### Post by earlycj5 on 2011-03-01
Impressive.

Looks like a nice, cross-platform application.

---

### Post by akniss on 2011-03-02
Thanks for the heads up. I've been playing with it on my Mac for a few minutes.  Its very well done.  I think I'll stick to Emacs, but I might start recommending this for my students as they learn how to use R in class.

---

### Post by PGScooter on 2011-03-02
I agree, this is a great app! And it seems like it has a good support set up and has the goal of being around for awhile. It will be exciting to see what they do.

It would be cool if we could use vim instead of its text editor...

---

### Post by hzambran_cl on 2011-03-03
Thank you very much !!.

While I'm downloading it, I'm looking forward to try the *Extract Function* function...

---

### Post by gunksta on 2011-03-03
> **akniss said:**
> Thanks for the heads up. I've been playing with it on my Mac for a few minutes.  Its very well done.  I think I'll stick to Emacs, but I might start recommending this for my students as they learn how to use R in class.

Agreed. I don't actually have any students, but I think RStudio could quickly become THE default tool for teaching R. Like I said in my OP, those of us using Emacs/Vim are unlikely to suddenly stop believing that our editor of choice is the best thing since sliced bread.

I want to see this promoted in the new Ubuntu Software Center. 

A couple of days ago I opened up Synaptic and I noticed that R now has it's own section, like Python and Perl. I suspect that Canonical's partnership with Revolution Computing had something to do with this change in how R is presented in Synaptic. R deserves this level of attention and I'm glad to see it get promoted in this way. Before, someone had to know to search for r-cran to find R packages in Synaptic.

I think the current organization in Synaptic is perfect. In the Ubuntu Software Center, I would like to see this RStudio application referenced as the preferred or default GUI for R. While I don't see me using it much, it has few dependencies and I would not be offended if installing r-recommended suddenly included this IDE. Too many people install R on Linux and then have to ask, how do I start R? I don't see if in my menu. RStudio seems like a perfect solution to this. The people behind the project appear to have quite a bit of steam/resources because this is a fantastic product for a beta. It already outperforms any comparable product that I can think of (Rcmdr, etc.).

I might wander over to their site and ask if they have made any efforts to get into Natty. I know it's a work in progress but it would be a shame to not get this in there.

---

### Post by maja_z on 2011-03-03
Promising indeed! I've just installed it and started playing around and I must say I love it. Not being emacs calibre myself, for me this is a step up from using Rcmdr and after only five minutes on Rstudio I'm not going back!

I have a question though, that may or may not have anything to do with Rstudio itself. But my installation (on ubuntu karmic) seems to have some issues with - not sure how to explain this - but with some elements of the gui not showing up. Eg I can see the scroll bar, but not the actual slider. If I guess where it is, it works, but it is invisible. Also I cannot see the "Source on Save" tick box. And the options dialogue box, well, I'm attaching a screenshot to show what it looks like. 

As I said, this might have to do with something else being wrong with my computer :( but I would really appreciate any pointers!

Still, I'm pretty sure I'll stick with it even if I can't fix this!

---

### Post by hugmenot on 2011-03-03
Sounds like something related to Qt or Qt themes is broken.

---

### Post by gunksta on 2011-03-03
I think hugmenot is probably correct. RStudio appears to use a statically compiled version of QT4. I'm pretty sure Karmic predates even the early QT4 stuff. I suppose it is possible that the QT3 theme is messing with RStudio's theme settings somehow. 

Dunno.

It will be better once it is in the repo and it uses the installed QT4 libs and not a statically compiled version of QT.

---

### Post by maja_z on 2011-03-03
I've been meaning to find the time to upgrade.. Hopefully that's all it is!
Thanks guys!

---

