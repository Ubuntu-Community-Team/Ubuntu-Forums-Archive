---
title: "updates destroyed gnome"
date: 2012-10-14
forum: Desktop Environments
---

### Post by elingeniero on 2012-10-14
I was trying to compile a programme ([engrid]("http://engits.eu/en/engrid")) and I was getting errors of missing libraries: (/usr/bin/ld cannot find -lGl) and after (almost) random package installation; it became worse (/usr/bin/ld cannot find -lqtopengl -lgl).

When I searched the internet for a package to get the libraries from. Lots of suggestions came up. After installing them one by one and trying to recompile again, I got bored with this process: *Why don't I just install all packages that has something to do with opengl & qt.* It seemed like a good idea and that is exactly what I did :guitar:. Good thing is, the program compiled and worked properly, bad thing; gnome doesn't work any more.

All I get is the background image and an error message from Docky about compositing or something like that. Logged out using <Alt><Prt Sc><K> and used unity, it works fine and I'm using it right now. My question is how to get gnome back working?

The first thought I had was to go Synaptic History and delete everything I installed. The moment I saw the number of packages installed yesterday, I got rid of the idea, maybe there is a better solution.

While searching for a solution, the problem seems to have occurred with nvidia drivers. I don't have nvidia and my AMD 7970m unfortunately has no drivers. I'm using the integrated graphics card.

Here's what I installed:
[http://pastebin.com/Q694ci9G](http://pastebin.com/Q694ci9G)

Ubuntu 12.04

---

### Post by DMGrier on 2012-10-15
Maybe I am not understanding what happened but are you saying that after you removed those packages gnome doesn't work anymore?

If this is the case I accidentally did something like that when I was running 8.04 and I fixed it by going into the command line and fully removing gnome and reinstalling gnome, I would say give that a try.

I would recommend doing this from ctrl+alt+F1

---

### Post by elingeniero on 2012-10-15
Thanks a lot. Problem solved by removing one of the packages I installed.

---

