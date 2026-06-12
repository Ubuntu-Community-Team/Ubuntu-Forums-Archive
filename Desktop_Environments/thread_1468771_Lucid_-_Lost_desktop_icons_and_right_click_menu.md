---
title: "Lucid - Lost desktop icons and right click menu"
date: 2010-05-01
forum: Desktop Environments
---

### Post by TheValk on 2010-05-01
I have checked quite a few post without coming up with an answer.
I have Lucid 32bit release installed with compiz visual effects normal.
I have lost the mounted drive icons from the desktop as well as the ability to save to the desktop or a right click menu on the desktop.
Any file saved to the desktop folder does not appear on the desktop.
I have reinstalled compiz, the nvidia driver and tried all manner of settings but just can't crack this one.
Any help would be appreciated.

---

### Post by P4man on 2010-05-01
open 

```
gconf-editor
```

browse to

/apps/nautilus/preferences/show_desktop

make sure its enabled.

---

### Post by TheValk on 2010-05-02
> **P4man said:**
> open 

```
gconf-editor
```

browse to

/apps/nautilus/preferences/show_desktop

make sure its enabled.


Thanks pal, I wish I had asked a few hours before I did.  It would have saved me much stress.
This forum and the people who help on it are just the best!

---

### Post by |-| [- |\| |&lt; on 2010-05-04
I'm sorry, but as far as I'm concerned, this problem is NOT yet solved. I've searched around and it seems like many more people including myself have the very same problem with the Gnome/Nautilus desktop not showing up in Lucid. Looks very much like it's some kind of system bug. For me, the problem started right after upgrading from Karmic to Lucid.
I had already tried the solution proposed here, either through gconfig or directly from the terminal with the following commmand:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
But in spite of this setting being 'true' (ticked, in gconfig) the contents of the user desktop folder, while being listed normally as files inside a Nautilus window, will still NOT show up as the actual desktop. I've tried several other things, rebooting right after resetting etc. but whatever I try, my desktop stubbornly remains blank.
Before I take the drastic step of trying a clean re-install of Lucid, would someone have another useful suggestion?

---

### Post by TheValk on 2010-05-08
> **'|-| [- |\| |< said:**
> I'm sorry, but as far as I'm concerned, this problem is NOT yet solved. I've searched around and it seems like many more people including myself have the very same problem with the Gnome/Nautilus desktop not showing up in Lucid. Looks very much like it's some kind of system bug. For me, the problem started right after upgrading from Karmic to Lucid.
I had already tried the solution proposed here, either through gconfig or directly from the terminal with the following commmand:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
But in spite of this setting being 'true' (ticked, in gconfig) the contents of the user desktop folder, while being listed normally as files inside a Nautilus window, will still NOT show up as the actual desktop. I've tried several other things, rebooting right after resetting etc. but whatever I try, my desktop stubbornly remains blank.
Before I take the drastic step of trying a clean re-install of Lucid, would someone have another useful suggestion?

Although the symptoms appear the same, this must be caused by a different set of circumstances.
Mine was a clean install and whilst setting up the desktop the way I liked it with regard to panels, menus and such, I must have knocked off the show-desktop indicator.

Good luck tracking down your problem.

---

### Post by mlnease on 2010-05-13
> **TheValk said:**
> Although the symptoms appear the same, this must be caused by a different set of circumstances.
Mine was a clean install and whilst setting up the desktop the way I liked it with regard to panels, menus and such, I must have knocked off the show-desktop indicator.

Good luck tracking down your problem.
Hello All,

This isn't solved for me either.  When I attempt the fix above I receive an error message to wit:  'This key is not writable'.  

I'll try opening gconf as root and get back to ye.

mike

Sorry--nope, opening gconf as root made no difference.  Still no desktop icons.

I tried every fix posted here to no avail.  Then it occured to me to select the Failsafe GNOME session to log on and, hey presto!  My desktop icons are back even after restarting with a regular GNOME session.

---

### Post by lyall on 2010-05-15
to get the ICONs back top the Desktop see the trhead the themusicalduck made
[http://ubuntuforums.org/showthread.php?t=1480586&highlight=desktop+icons]("http://ubuntuforums.org/showthread.php?t=1480586&highlight=desktop+icons")

my ICONs are now showing on the Desktop again

good luck and have fun learning

---

### Post by mlnease on 2010-05-16
> **lyall said:**
> to get the ICONs back top the Desktop see the trhead the themusicalduck made
[http://ubuntuforums.org/showthread.php?t=1480586&highlight=desktop+icons](http://ubuntuforums.org/showthread.php?t=1480586&highlight=desktop+icons)

my ICONs are now showing on the Desktop again

good luck and have fun learning

Thanks but no, still no luck.

mike

---

### Post by vatch23 on 2010-05-16
Maybe I should have started a new thread, but I dont think so.
Because somewhere about a week ago I could just click somewhere to show the desktop icons, or better said, choose which one to show.
However I have totally forgot where this was, can somebody please tell me again?
Vatch23

---

### Post by P4man on 2010-05-16
eeh.. post #2 in this thread?

---

### Post by pete_m on 2010-05-17
Hmmph .. not solved for me either...

I've checked in gconf  show_desktop is checked and tried the killall nautilus trick.

I have a small script that toggles that gconf parameter and I can see that it is still working.

This problem arose after I installed a bunch of alternate WM's - Flux ,Ice, LXDE,OpenBox for evaluation purposes. The install was fine and these are now available as sessions at login.
At my first login to Gnome after this my background had disappeared.
Interestingly the background appeared behind the NBR interface when I ran netbook-launcher and disappeared when it was killed.

Incidentally does anyone know how to configure compiz skydome - the ultimate background?
I mention this as i suspect it may be relevant- maybe nautilus/gnome are drawing the icons on a surface that is not visible...

i'm still comparitively new to Linux so any observations and guidance will be much appreciated ..
  
[SIZE=2][First screenshots]("http://www.youtube.com/watch?v=YoI4wRVVjBs")[/SIZE] - more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

---

### Post by tock on 2010-06-13
I had the same problem I found this command in one the posts. Itz worked for me.  I'm trying to add this solution to the posts that I've tried to make solving this problem easier.

rm -r ~/.local/share/gvfs-metadata

---

### Post by technodenbow on 2010-06-24
I agree that these suggestions are not solving our issue. I think mine resulted after configuring settings in either Ubuntu Tweak or failing to install Conky properly.

Ubuntu Tweak settings allow me to show desktop icons but they are not. I wonder if I remove/install again will the icons return?

---

### Post by pete_m on 2010-06-30
@tock
thanks for the
```
 rm -r ~/.local/share/gvfs-metadata 	
``` tip - I remember seeing that file and it seems to describe persistent desktop icon thingys - so i guess zapping it forces a rewrite. .
I'll look forwrd to trying it when I get my system back up - and if the original problem persists - I made the mistake of upgrading..and  have since made a clean install of EB4/ Aurora on my second hard disk

@[technodenbow]("http://ubuntuforums.org/member.php?u=1061815")

Hmm. . I seem to remember that it may well have been at abotu the same time that I decided Ubuntu tweak was not worth having around.  .
Perhaps something went wrong with its removal. . tho' I think one of the other Windows Managers may have been the culprit.

I'm still in the middle of upgrading and hopefully nearly there . .:popcorn:

---

