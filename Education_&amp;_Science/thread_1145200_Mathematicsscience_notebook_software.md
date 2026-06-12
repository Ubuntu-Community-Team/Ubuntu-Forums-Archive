---
title: "Mathematics/science notebook software"
date: 2009-05-01
forum: Education &amp; Science
---

### Post by Silentvoice on 2009-05-01
Hey, I'm soon to graduate with a degree in mathematics, and I'm preparing for graduate material that's soon to come.. 

As any of you know who do mathematics or science, you can't just open a book and read it and hope to learn anything.. you have to have something nearby to take notes, and follow the presentation, and attempt exercises (depending on how sadistic the author is 'this fact is trivial and is left as an exercise..' etc etc)

When I'm on my laptop (windows) I use scientific notebook for this purpose, it's fantastic in that you can produce a minimally formatted document and just worry about the note taking.. producing mathematics symbols follows from a very simple and intuitive set of shortcuts (from which you can define your own if you want), and all of the most basic formatting you could want just for readability later is accessible by very simple keyboard shortcuts..


The idea is that I have something to just slap down basic ideas as I'm reading a text, then later if I want to make them presentable I LaTeX them.

I haven't been able to find a linux variant of something that follows this idea though! I know there are a lot of great LaTeX front ends, but those are for producing a seriously formatted document (and I prefer to write the LaTeX myself).. worrying about that level of formatting is a huge distraction from studying for me. Unfortunately scientific notebook has not been able to work with wine yet, so other than that I'm not really sure what's available (I've searched this forum, sourceforge, and a few links provided on this forum, also)

Anyone have any ideas?

Thanks!

-SV

---

### Post by hubie on 2009-05-03
I was not familiar with Scientific Notebook, so I looked into it a bit.  I still do my latex the old fashioned way (text editor and command line), so I'm probably not the best source of information on this topic, but the screenshots I saw looked an awful lot like [LyX]("http://www.lyx.org/Home") to me.

The history of Scientific Notebook seems to be that it is a stripped-down version of Scientific WorkPlace, which is basically a latex front-end with an embedded computer algebra system.  The part that is stripped out of Notebook is the ability to do latex layout.

You might find [this paper]("http://www.jstatsoft.org/v17/s01/paper") informative.

---

### Post by Silentvoice on 2009-06-05
It's been a while on this, but I actually found what I was looking for. 

Scientific notebook is actually a little different from LyX, because it doesn't even pretend to give good formatting. This is actually a plus, because you have direct access to notation, and can produce it very quickly.. almost as fast as one could speak it when giving a lecture (In fact, one of my professors types his notes on scientific notebook whilst lecturing so that the class can see it in clean notation instead of hastily scrawled on the whiteboard)

I tried LyX, and I couldn't quite figure it out.. so I moved on to TeXmacs.

I tried TeXmacs out, and it turns out it was exactly what I was looking for. It isn't a pure frontend to LaTeX, but it does have exporting capability (which I probably won't use). What's great about it is that it will produce the symbols and notation you need, and its navigation interface resembles emacs. I can produce the most complicated formula in seconds with this, almost as I read. It's very nice, and very efficient. The automatic formatting it gives is a plus, but I don't really need it. It's just a place to put down my notes, which I will then write up in LaTeX myself later.


Thanks for the link, by the way. That was a pretty informative paper about LyX (it's what spurred me to try LyX first).

---

