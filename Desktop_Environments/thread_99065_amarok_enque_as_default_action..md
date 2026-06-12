---
title: "amarok enque as default action."
date: 2005-12-04
forum: Desktop Environments
---

### Post by royg1234 on 2005-12-04
Hey, I'm trying to find out if there's a way to make amaroK add songs to the que as the default action (Winamp does this as an option).  E.g. when you browse through your files, or through streamtuner, and you hit enter, the song(s) get added to the current playlist, instead of replacing it.

Thanks

---

### Post by royg1234 on 2005-12-08
anyone?

---

### Post by mrastas on 2006-04-28
[QUOTE=royg1234]anyone?[/QUOTE]

I think this should do it.

   Additional options:
       -e, --enqueue
              Enqueue Files/URLs

ie. modifie the start script of amrok...

amarok -e <url>
amarok -e <file>

For streamtuner you can edit the config file (~/.streamtuner/config) to start amarok with -e option.

I don't actually know where to modify this, to get it work in kde konquerror, Perhaps konquerror settings allows this in change in file associations.

---

### Post by Ramses de Norre on 2006-04-28
Nautilus > properties on a file of the kind the action is desired for > open with > add > custom command
Choose the command you like (amarok -e here).

---

### Post by louis_nichols on 2006-04-29
Also, if you're using krusader, it has a right click menu with user actions, highly customizable from settings. You can add such an option there.

---

### Post by Ch33zm0ng3r on 2007-01-02
I wanted to do a similar thing.  It was easy to create a new action for it by right clicking on the icon of an mp3 or m3u file and creating a new 'open with' entry under permissions and telling it to run 'amarok -e'.  However, i'm  using gnump3d and firefox still uses the plain old default amarok action and will replace the playlist when i click a song in the gnump3d menu.  Is there a way to append the -e option on the original default open action for amarok?

---

