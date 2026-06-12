---
title: "Fluxbox will no longer start"
date: 2006-06-26
forum: Desktop Environments
---

### Post by RaoulDuke on 2006-06-26
I installed Fluxbox looking for a faster desktop and all went well. I had a torrent downloading with BitTorrent, when it was done I clicked Stop, and then clicked Close. When I clicked Close Fluxbox crashed and it brought me back to the login screen.

I am able to use Gnome, however when I log into Fluxbox it brings up a window saying that my session lasted less than 10 seconds and show me the contents of the .xsession-errors file:

/etc/gdm/PreSession/Default: blah blah
/etc/gdm/PreSession/Default: blah blah blah
/etc/gdm/Xsession: Beginning session setup...
INFO: imwheel started (pid=31597)
imwheel: the -p option is deprecated.
INFO: imwheel started (pid=31603)

I have been unable to acquire any post on any of the forums I know that pertains to this error.

Any help is greatly appreciated.

Thanks

---

### Post by jpkotta on 2006-06-26
If you don't have one already, make a ~/.xinitrc:
```
echo "fluxbox" > ~/.xinitrc
```

Then, go to the console (CTRL+ALT+F1), log in, and run
```
startx -- :1 > ~/errors
```
The "-- :1" is unnecessary if you don't have gdm running.

If this works, then we'll know it's not Fluxbox, or at least not just Fluxbox.  If it doesn't, post the errors file that gets created in your home directory.

---

### Post by RaoulDuke on 2006-06-26
Weel, that started Fluxbox on tty8 (while Gnome was still running on tty7).
So now how do I get it to start from the login screen?

Thanks for the quick reply btw.

---

### Post by Kosh on 2006-06-28
I'm having the same problem, I'm also a fluxbox user and I get a similiar .xsession-errors file.  If I create a new user then fluxbox will load fine so I'm guessing that it's some gnome or gdm setting, unfortunately I don't know much about their configuration files to know what to wipe out.

Also, I noticed that this is in the 5.10 forum.  This problem began for me when I upgraded from 5.10 to 6.06 but I'm guessing it's the same error.

---

### Post by jpkotta on 2006-06-28
I use FVWM, and I compile it from source.  That means that it's not very well integrated with the rest of my system.  Therefore there is probably a better way to do this, but this way should work.

Make an ~/.xsessions file.  I just symlink mine to my ~/.xinitrc.  The difference between the two is that .xinitrc is used with startx, while .xsession is used with graphical logins like gdm.  There is no difference in the syntax of the files; they are essentially just shell scripts.
```
ln -s ~/.xinitrc ~/.xsession
```

Then when you are at gdm, set the session to "default system session".  It should look for ~/.xsession and run whatever commands are in that file.  The simplest possible ~/.xsession file just has the window manager invocation command, e.g. "fluxbox".  If you followed my previous post, you only have to make the symlink.

---

### Post by RaoulDuke on 2006-06-28
That seems to have done it for me! When I choose Fluxbox from gdm it still gives me the same error. However when I choose Default instead of Fluxbox it starts right up.

Is there any way I can get it to start up by actually selecting Fluxbox? (fix the problem instead of just bypassing it)

Thanks again!

---

### Post by szudden on 2006-07-05
I had the same (or similar) problem.  When I updated to Dapper, it turned out that fluxbox was installed to a different location.  It used to be in /usr/local/bin, but now is just in /usr/bin.  My old ~/.fluxbox/startup contained the line:

exec /usr/local/bin/fluxbox -log ~/.fluxbox/log

but the new location for fluxbox means ~/.fluxbox/startup should contain:

```
exec /usr/bin/fluxbox -log ~/.fluxbox/log
```

which points to the new location.    

BTW, If you don't want to keep a log, it's just:

```
exec /usr/bin/fluxbox
```

---

