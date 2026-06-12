---
title: "Problems with evince"
date: 2011-03-26
forum: Desktop Environments
---

### Post by Olin Shivers on 2011-03-26
Could someone advise me on evince issues? I have three problems.

1. Evince is somehow screwing up font creation when displaying dvi files.

   I can preview the dvi file fine under xdvi. When I try with evince,
   I kicks off a slew of metafont font-creation runs, then shows me
   totally garbled pages -- the layout is correct, but none of the
   characters are right. This happens for documents that primarily use
   Times Roman fonts.

2. *Every* time evince comes up, it insists on starting in continuous /
    "fit page width" mode. I don't want either one. I want continuous-mode
    *off* and the window in the "best fit" view. So I have to click, drag,
    click, click, drag, release *every* time I pop up a file. It's very
    annoying. There doesn't appear to be any key in the gnome gconf config
    database I can set to affect these things. How do I fix this?

3. Evince appears to have *no* documentation. The application has been
   around for *years*. Yet there is no documentation. Someone took
   the trouble to put up a slick, attractive web page at 
   [http://projects.gnome.org/evince/](http://projects.gnome.org/evince/), which has some nice marketing for
   evince, but no one has bothered to write up any documentation on the
   app -- flags, settings, paging behavior, mouse chords, accelerator keys,
   arrow key behavior: nada. Have I missed anything, or is this really true?

   I stumbled over this issue in my attempts to answer issues 1 & 2.
   I *did* find a FAQ which included issue #2. But it is just, apparently,
   a frequently asked *question*; there was no corresponding frequently
   replied *answer*. Just the question.

I'm aware that these questions probably more appropriately belong on
a gnome discussion list, but I couldn't find one when I was poking around.
If someone could direct me to a better place to post these questions, I'd
appreciate that, as well.

Thanks!
    -Olin

---

### Post by Copper Bezel on 2011-03-27
Well, Evince does have a help page, accessed from its own Help menu, that does include some of the information on shortcuts and such that you mentioned. It's very limited, admittedly.

I couldn't find a config file for it, either, just a file that reports its accelerators at /home/[username]/.gnome2/accels/evince . It used to insist on displaying the navigation sidebar on my machine every time it started until I turned it off in View instead of closing the sidebar with the little X, but it's definitely saving some config settings *somewhere*.

Have you tried using Adobe Reader instead? It's heavier but tends to be more complete.

Edit: I'm not in the kind of field to be dealing with LaTeX, but I'm assuming you have all the relevant TeX support installed, so Evince should be able to handle this - I ran into a couple of bugs filed to Evince under Ubuntu involving .dvi, but not this one specifically. Obviously, the bit about Reader isn't going to apply to .dvis, either.

---

