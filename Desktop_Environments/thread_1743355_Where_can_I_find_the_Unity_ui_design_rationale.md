---
title: "Where can I find the Unity ui design rationale?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by igouy on 2011-04-29
Somewhere I hope there's a document explaining and justifying the ui design decisions behind Unity - where can I find that document?

Where can I find the user studies that show that the new scroll buttons are significantly easier to use than the old scroll bars? (On a large monitor?)

---

### Post by Copper Bezel on 2011-04-29
Well, there weren't any on that latter. They're [specifically designed]("http://design.canonical.com/2011/03/introducing-overlay-scrollbars-in-unity/") for the benefit of smaller screens and touch devices; obviously, the ordinary GTK scrollbars can be re-enabled instead, and there's no *dis*advantage to the overlay scrollbars.

I doubt if there's a publicly available, central, single document of Unity design goals. That said, design.canonical.com would be a fairly good place to start looking.

---

### Post by igouy on 2011-04-29
> **Copper Bezel said:**
> obviously, the ordinary GTK scrollbars can be re-enabled insteadWhat are the exact steps I need to follow to do that? (I already tried switching to Ubuntu Classic but that wasn't enough.)

> **Copper Bezel said:**
> and there's no *dis*advantage to the overlay scrollbars.Playing hunt for the scroll thumb gets old really quickly. For previously opened documents the scroll thumb might be somewhere in the middle of the document. That didn't matter with ye olde scrollbars, because clicking in the top or bottom of the scrollbar would cause the page to scroll - but now it seems I have to find where the scroll thumb is before I can scroll with it.

---

### Post by Copper Bezel on 2011-04-29
WebUpD8 has a [how-to]("http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html").

It's kind of crazy, but while I don't use scrollbars, overlay or otherwise, because that's what scroll wheel emulation is for,  I *would* kind of like a "scroll indicator" ; I work with a lot of documents and hate getting lost. I think the best thing for *either* use case would be if the overlay never fully disappeared but became transparent instead.

---

