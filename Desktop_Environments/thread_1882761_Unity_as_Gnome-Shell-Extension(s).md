---
title: "Unity as Gnome-Shell-Extension(s)?"
date: 2011-11-17
forum: Desktop Environments
---

### Post by gexi on 2011-11-17
Hey guys, just wanted to ask about your opinion on something that popped into my head a few days ago.

Wouldn't it be possible to create a gnome-shell-extension, or a set of extensions, that create a desktop-experience similar to unity?
It would consist of an elaborate dock, the globalmenu, the maximized window thingy, and maybe some other minor things.

I guess the main advantages would be:
[LIST]
[*]**Speed** - maybe it's my hardware, but gnome-shell/mutter seems to be a lot faster than unity/compiz; and i've heard this quite a few times from other users
[*]**Closer to the original codebase** - there would be less unity-specific code to maintain; which would mean more manpower on less code.
[*]**Customization** - gnome-shell-extensions are easy to disable or enable, and could be combined to the users bias. also  css/javascript makes it easy to theme.
[*]**Workspace-Management** - Unity could take advantage of the gnome-shell workspace-management, which, in my humble opinion, is superior to the present compiz workspace-management.
[*]...
[/LIST]


btw. don't get me wrong, i don't want to start a flamewar or something. in fact i love both environments. i just think, that the extension-system of gs (since 3.2) would make such a thing possible (which was not the case with natty / gnome 3.0 - i know).

also i imagine there would be some nice ways to integrate gnome-contacts, gnome-documents, gnome-music, aso, with ubuntu-one. come gnome 3.4 ...

what do you think? (i'm almost certain this won't be done, let alone the huge amount of work that have been put into the unity-compiz-plugin ...)

---

### Post by 3rdalbum on 2011-11-17
There might actually be more code. Unity is really quite far away from Gnome Shell, and it might be easier to maintain this stand-alone thing rather than maintain a massive bunch of hooks into Gnome Shell.

---

### Post by gexi on 2011-11-17
> **3rdalbum said:**
> There might actually be more code. Unity is really quite far away from Gnome Shell, and it might be easier to maintain this stand-alone thing rather than maintain a massive bunch of hooks into Gnome Shell.


Well, the idea is not to recreate everything to the last detail. It's about the main ideas behind unity:

[LIST]
[*]using the space of the screen more efficient, with fully maximized windows and a global menu. (possible through extensions)
[*]a unique user-experience through a unity-style launcher and having access to your data via lenses. (possible through extensions)
[*]a dock which is permanently shown (also possible through an extension)
[/LIST]

Is this really that far out of reach? Or am I missing something?
... Well maybe it's a bit of a 'best of both worlds' thing i'm aiming for ... but still ...

---

### Post by 3Miro on 2011-11-17
Gnome-shell is supposed to be very moddable, so I guess it is theoretically possible. There would be some features like the compiz effects that cannot be added at the moment (not until Gnome-shell supports more effects), but the general concept should be doable.

I don't know how, I just know it involves JavaScript.

---

### Post by aaronmfisher86 on 2012-03-16
You can currently do something very similar to what you're asking actually.  If you ad unity-2d-shell to the gnome3 startup applications you'll have the dock, lenses and all the features that are attached to the dock itself.  I know there's a few extensions in the works right now to develop the global menu bar from unity but none of them are really fully functional at the time of this post.  Really the only thing I was unable to get working correctly within gnome shell that I was looking to replace from unity was FULL pidgin integration into the messaging menu & the ability to have your music apps *stick* to the music menu even if they're closed like Unity.  Other than that and the lack of compiz you can pretty much replicate Unity within Gnome shell and have, as you put it, the best of both worlds!

---

### Post by Frogs Hair on 2012-03-16
The global menu is being worked on already . [http://www.webupd8.org/2011/11/install-gnome-shell-global-menu-in.html](http://www.webupd8.org/2011/11/install-gnome-shell-global-menu-in.html)

---

