---
title: "Old Linux game"
date: 2020-11-15
forum: Gaming &amp; Leisure
---

### Post by heroquestelf on 2020-11-15
I have a question. I have a game that is designed for Ubuntu 8.0 that I would **_*REALLY*_ LOVE** to run called "OpenFracas", but I'm currently running the 20.04.1 Ubuntu MATE LTS. It's telling me I need libgtk2-ruby. Is there a workaround to this or am I just out of luck?

Here is the website: [URL="https://www.opendesktop.org/s/Apps/p/1109708/"]https://www.opendesktop.org/s/Apps/p/1109708/ 

[/URL]The website also includes the following note... (not sure it will help, but here goes)
> [B]
To run from source[/B]
OpenFracas is written in Ruby. To run the game, type `ruby ./Main.rb` from the top-level directory for the source.

OpenFracas  requires ruby >= 1.8, ruby/gtk, sdl-ruby (with mixer support) and  libglade2-ruby >= 0.16 in order to run. Exact package names may vary  depending on your distribution.                                                                                                                                                                                                           

---

### Post by CatKiller on 2020-11-15
Well, it's been abandoned. The last update about it was in 2009.

You might be lucky and be able to simply edit the .deb file's dependencies so that they're looking for modern versions of the libraries it uses, and have it still work if there weren't any breaking changes in those libraries between then and now.

Otherwise, the source is on Launchpad, so you could amend the program so that it uses the modern functions from the modern libraries. You might find the process enjoyable, and want to take over as maintainer of the project.

---

### Post by mastablasta on 2020-11-16
or run a vm (e.g. virtualbox) with ubuntu 8 in it

---

