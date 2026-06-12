---
title: "Scripting from nautilus"
date: 2006-06-27
forum: Desktop Environments
---

### Post by frankerooney on 2006-06-27
Hi, I'm just trying to get aquanted with the nautilus-scripts folder by creating some scripts. Problem is, it doesn't quite do what I want it to. I am selecting a number of files to queue into xmms and then running my script. I've made it nice and simple so in the script it's just got

for arg
do
$player -e $arg
done

now it works if the $player - xmms or whatever is already open but if it's closed and even if I create a new instance of the player above this subroutine, it just opens one file into the playlist, then plays it, and when I close xmms, it opens another xmms windows with the next file. I've tried $player & at the start, but it still doesn't work! any ideas?

---

### Post by bDerrly on 2006-06-27
Have you installed the `xmms-shell' package?  I haven't dealt with xmms from the command line but I bet you'll have better luck with this package.

---

### Post by Sonofmoog on 2006-06-27
What follows is the Open As Administrator script that is part of the online Ubuntu documentation:

```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done
```

You might play a bit with this substituting xmms for gnome-open and removing the gksudo.  I haven't tried this, but my guess is that it will not work because it will probably open multiple instances of xmms.  

You might also try creating a playlist and loading that, so your script might look something like this.  In pseudo-code:

Test for Xmms.m3u in home folder
If it exists, truncate it to zero by cat /dev/null > $HOME/.xmms/xmms.m3u
Initialize the loop - for uri etc ..
ls $URI >> $HOME/.xmms/xmms.m3u
done
then, 
/usr/bin/xmms $HOME/.xmms/xmms.m3u
Exit 0

---

### Post by frankerooney on 2006-06-30
Thanks for the replies. I didn't know you could use playlists with xmms - mplayer has this facility listed in the --help menu, so I echo'd my list into a text file and got mplayer to open up the playlist. Useful to know xmms can do this too! Thanks. I'll try and have a look at xmms shell. Totem exhibited the same behaviour though which is odd. It seems to pause the script which runs until you close the current instance of the player, then carries on when you close it. Odd! I sort of got around it by opening up the player explictly first then test to see if $arg = $1 i.e. the first argument is the current one, for which I did a $player $arg, then for subsequent ones did a $player -e $arg, which worked. Wierd.
Thanks again!

---

