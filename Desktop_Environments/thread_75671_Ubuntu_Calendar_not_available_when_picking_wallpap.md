---
title: "Ubuntu Calendar not available when picking wallpapers"
date: 2005-10-14
forum: Desktop Environments
---

### Post by sander marechal on 2005-10-14
Hello,

I installed ubuntu caledar as well as the older wallpapers. There was a blue background in there somewhere that I really liked. I've installed everything but the wallpapers are not selectable when I right-click on my desktop and choose "change wallpaper". I tried restarting gnome (ctrl-alt-backspace) but that didn't help. Still only the 3 default wallpapers there that I got with the breezy install.

Help?

---

### Post by Ampersand on 2005-10-14
What happens if you select 'add wallpaper' in the change background window? I think they install to '/usr/share/backgrounds' but if they're not there, you can open Synaptic and go to the package you installed and look at 'installed files' to find them.

---

### Post by sander marechal on 2005-10-14
Thanks, I'll try that. I already tried to find the installed files before but I couldn't find them. It didn't cross my mind that apt keeps track of that.

But this would mean no monthly rotating wallpaper, right? Oh well, at least I'll have my nice blue one back.

---

### Post by hone on 2005-10-14
I ran into this particular problem too and googled but couldn't find anything.  I eneded up updatedb and then doing a locate an found out that they were stored in a different directory from where gnome actually looks for the backgrounds.  here's how I fixed it.  The xml files are put in /usr/share/gnome-wallpaper-properties/ but gnome looks in /usr/share/gnome-background-properties/  so I just copied over the files from gnome-wallpaper-properties and moved them into gnome-background-properties and then did a symlink, ln -s /usr/share/gnome-background-properties/ /usr/share/gnome-wallpaper-properties/

hope that helps.

---

### Post by psyguy92 on 2005-10-27
Thanks hone, that worked well.

I had to:[PHP]sudo su
su -[/PHP]

then cp the appropriate files and link as you said, and everything was fine.
One question though...  
I was wanting an actual calendar on the desktop for the current month.  After having done this, I just have the wallpaper.  Isn't this a calendar?  How do I enable this?  (And will it update monthly?)

psyguy92

---

### Post by joshuaxls on 2005-11-03
I don't understand... if I leave it on the default Ubuntu wallpaper, will it automatically update itself? Why does it default to march? Why nude models? So perplexing...

---

