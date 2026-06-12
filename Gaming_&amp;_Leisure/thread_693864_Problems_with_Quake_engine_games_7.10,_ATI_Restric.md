---
title: "Problems with Quake engine games: 7.10, ATI Restricted,"
date: 2008-02-11
forum: Gaming &amp; Leisure
---

### Post by Malboury on 2008-02-11
Hi There,
I've been using Ubuntu for a while now, ever since version 5.something or other, and am a very big fan. Most of the problems I've experienced have been minor, and I've really enjoyed seeing Linux in general make such great moves towards user friendliness in general over the past few years, what with repositories and such.

Anyway, all my problems so far have been solved without having to post, except this one:(

I recently upgraded from Ubuntu 7.04 to 7.10 through the online upgrade option. Everything has been peachy, except that now no Quake engine games (Open Arena, Nexuiz, Tremulous) will play properly! Textures and in game menus are dark and distorted, though framerate and models are fine. I am, and have been, running with an ATI Radeon 9550 with restricted drivers enabled, Gnome desktop and Compiz Fusion switched on. I've tried everything I can think of; from enabling the community ATI drivers, disabling compiz, changing resolution, restarting X; everything obvious I can think of. The problem persists.

Finally, I'm not the first person to suffer form this; see also here [http://ubuntuforums.org/showthread.php?t=644995]("http://ubuntuforums.org/showthread.php?t=644995")

I don't post on forums much, so I'm not sure I should have posted there or not, but the post is a few months old and unresolved...

Anyway, thats the story. If anyone could help, that would be great. I'm trying very hard to convince a friend of mine that Linux isn't some crazy prank the internet is playing on everybody, and that it can work well with games. And I really don't want to downgrade!

Thanks again, hoping someone out there can help! If screenshots or console logs would help, let me know!

Thanks!

---

### Post by Malboury on 2008-02-11
Crazy stuff. I actually managed to fix the problem for all three games! Mental! It turns out that Lightmapping doesn't work in the new version of Ubuntu on my Graphics card; a Radeon 9550. (Well, at least not in Quake engine games.) Now, because the menu was messed up, I was unable to change this manually in some, and was forced to change over to vertex lighting in the config files by setting set r_vertex "1" instead of "0".

Now, I hesitate to call this fixed, as lightmapping should work as well. This has become mainly academic for me now that I can play Tremulous again, but any ideas? Okay, thanks anyway, I'm going to go PM the guys who was confused by this is December. Bye!

---

