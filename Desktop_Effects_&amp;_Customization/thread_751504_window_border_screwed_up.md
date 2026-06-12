---
title: "window border screwed up"
date: 2008-04-10
forum: Desktop Effects &amp; Customization
---

### Post by lolzlolz on 2008-04-10
ok, so i was stupid and interrupted an update in the middle, lesson learned never interupt an update
anyways after having to fsck and tons of other crap manually i was finally able to boot into ubuntu,
so now look what's happened, my once cool desktop in the hardy heron beta is now screwed with weird panels, window borders and icons
no it's not inside the appearance look at the screenshot and ull see what i mean
how do i fix this?
thanks

---

### Post by russo.mic on 2008-04-11
All of your gnome settings are stored in a bunch of hidden directories in your home folder.  try looking in /home/username/.gnome and .gnome2 and see what you find.  Also, look for .emerald there, as that is where your emerald themes and preferences reside.  I can't guess as to why these programs aren't find this stuff.

Is your 3d rendering still on?  i.e. is this an xorg.conf problem?

---

### Post by lolzlolz on 2008-04-11
what should i look for in there?
also ima be gone 2 weeks, so when i get back ill continue working

---

### Post by Zorael on 2008-04-12
I'd try creating a new user to see if the error is just in your user configuration and not something system-wide.

If so, you could try to resolve broken packages; there's an option to do so in the menu in Synaptic. I don't know the terminal command, I'm afraid. I'm not at all sure that'd help any - I'd put my money on the new-user workaround.

---

