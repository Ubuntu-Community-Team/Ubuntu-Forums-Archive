---
title: "Firefox/FoxyTunes issue."
date: 2009-09-10
forum: Desktop Environments
---

### Post by aeiouna on 2009-09-10
I'm having the same issue as expressed [here]("http://ubuntuforums.org/showthread.php?t=251300"), and would have posted there (yeah, necroing the thread.), but it's locked.

I tried to execute the code as shown in the fifth post down, but I don't know what I'm doing wrong (I go to Terminal to execute that code, right?) It keeps telling me there is "no such directory" even taking off subfolders enough to be going to my profile folder (which obviously exists).

I'm also not sure if that is meant to be one command or two. (I rarely use my command prompt in Windows as well, I'm a GUI kinda person, not a CLI one.)

I'd like it to control my Rhythmbox player.

Diagnostics: Ubuntu 9.04 Jaunty Jackalope, Firefox 3.0.13, FoxyTunes 4.0.2.1, Rhythmbox 0.12.0.

Edit: Okay, I fixed this problem by finding the libstdc++5 package in Synaptic and installing it. However, while it now finds Rhythmbox as a player, it doesn't control it as it should. Trying to do so just maximizes the window.

---

