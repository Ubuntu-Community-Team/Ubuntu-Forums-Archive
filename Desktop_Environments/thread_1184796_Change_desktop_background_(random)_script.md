---
title: "Change desktop background (random) script"
date: 2009-06-11
forum: Desktop Environments
---

### Post by bivasdas on 2009-06-11
Hi all,

I am a newbee to ubuntu... I have used linux previously but not that much. I baught dell mini 9 & 12 both with ubuntu and i loved it. I have written few scripts for easy tasking ;) I'll try to organize and post them. Someone around the corner might find them useful...

This one can be used to randomly change wallpaper.
*must run from the folders where your wallpapers are
```

ls -1 *.jpg | head -n`expr $RANDOM % \`ls -1 *.jpg | wc -l\`` | tail -n1 | echo `pwd`/`xargs` | gconftool-2 -t string -s /desktop/gnome/background/picture_filename "`xargs`"

```or you may want to add this code to the session so that it will change the wallpaper after certain time

```

cd $HOME/<path-to-wallpapers> && if ! test "$1" = ""; then if test $1 -gt 0; then while /bin/true; do ls -1 *.jpg | head -n`expr $RANDOM % \`ls -1 *.jpg | wc -l\`` | tail -n1 | echo `pwd`/`xargs` | gconftool-2 -t string -s /desktop/gnome/background/picture_filename "`xargs`" && sleep $1; done; fi; fi

```save the code to a file (say change-wall)
then do ```
chmod +x change-wall
``` to make it executable 
try running it with ```
./change-wall 2
``` to change wallpaper every 2 second
then add it to System->Preferances->Session->Add

Let me know if you came accross any trouble...

cheers,
bivas :D

---

### Post by Dullstar on 2009-08-01
Yeah, I know, this is an old thread, but it sounds cool.
Kind of confusing, though.

Can you or someone else clarify?

---

