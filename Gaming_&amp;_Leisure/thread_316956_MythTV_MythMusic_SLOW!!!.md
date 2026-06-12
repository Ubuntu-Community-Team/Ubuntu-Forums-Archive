---
title: "MythTV: MythMusic SLOW!!!"
date: 2006-12-11
forum: Gaming &amp; Leisure
---

### Post by ghstzr0 on 2006-12-11
I have installed MythTV 0.20 from the SVN repositories and all setup went off without a hitch.  I am really happy with the program except for one thing:

The MythMusic plugin (as well as many other menu areas, such as MythVideo) ARE REALLY SLOW when traversing the menu (browsing my music).  I can't find any relevant info on this.

The strange thing is that if I visit 'System Info' first, then the problem is fixed (only have to do this once per time I open MythTV).  I am pretty sure it has something to do with wither the database or the Backend (I have the backend installed, but am not using it at this time, so I leave it not running).

I have previously tried using the Edgy packages for MythTV, but I had the same problem there.

Any Ideas?

---

### Post by ghstzr0 on 2006-12-19
bump...

---

### Post by leech on 2006-12-19
Unfortunately I thought you meant something else.  I use Debian Unstable and the mythtv packages from debian-multimedia.org, and the menus themselves aren't slow.

I thought you were talking about the fact that it takes hours to rip a music CD in MythMusic.  Not quite sure why it takes so long, it's a good thing I don't use it that much.  I think MythMusic is one of the plugins that need the most love as far as the usability goes.

Leech

---

### Post by pbardet on 2007-01-12
Do you happen to have an Nvidia video card ?

When I installed Ubuntu on my Nvidia-based media center, it used the default nv driver as well as gnome. When I added MythTV, I noticed a very slow mythmusic (as you did) while my previous install using gentoo (Nvidia proprietary + kde) did not show such a problem.

After switching to proprietary Nvidia driver + kdm (under Ubuntu), everything went back to normal (no more slow menus). I personnally doubt the switch from gdm to kdm did anything since I'm still using metacity as a window manager in my .xsession and I won't take the time to try switching back to gdm. When something works, I tend not to try to break it intentionnally, since usually, an upgrade takes care of it.

Hope it helps.

---

