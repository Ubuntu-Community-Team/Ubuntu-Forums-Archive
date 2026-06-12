---
title: "Icon Themes in Beryl -- how to install, where to find"
date: 2007-02-25
forum: Desktop Environments
---

### Post by satchelpig on 2007-02-25
I have installed and am actively using Beryl succesfully after some initial hiccups which seem to be par for the course.

I'm now obsessively tweaking my desktop to get it to look *just exactly* right.

In that vein, I have gone to gnome-look.org and downloaded some icon themes, thinking the relatively humdrum icons that seem the default with beryl could use changing.  I downloaded a number of icon themes I liked and, as I learned elsewhere in these forums, installed them into the theme manager.

The problem is that so far as I can tell, anything installed into the theme manager has no impact on the way that icons (or anything else) appears in Beryl.  If I boot into gnome (ie, no Beryl) I can see all these icon themes, etc. and choose and modify to my heart's content.  But  if I start Beryl, that's out.

For what it may be worth I am using XGL with Beryl, if that matters.

Do I need to be downloading some other kind of icon themes for use with Beryl?  Should the ones I'm installing into the general theme manager be working?  If so, what do I need to tweak?

Thanks for guiding a newbie.  I am having fun with Ubuntu but like anything new I am going to have to get by with stupid questions to those of you kind enough to answer them for a while.  Thanks.

---

### Post by stoffepojken on 2007-02-25
edit your /home/user_name/.gtkrc-2.0

add a line like this:

```
gtk-icon-theme-name = "Tango"
```

I use Tango in this example. Replace Tango with an icon theme of your choice.

---

### Post by satchelpig on 2007-02-25
> **stoffepojken said:**
> edit your /home/user_name/.gtkrc-2.0

add a line like this:

```
gtk-icon-theme-name = "Tango"
```

I use Tango in this example. Replace Tango with an icon theme of your choice.
Hmm.  I don't see any such file in my home folder.  Are you suggesting that I create one, or are you telling me something's missing that shouldn't be?

---

### Post by stoffepojken on 2007-02-25
create it

---

### Post by satchelpig on 2007-02-25
Wow! Worked like a charm.  Thank you.

Just curious -- is there supposed to be an easy/GUI way to do this?  Had you not been kind enough to take the time to answer my question, there is no way in a million years I'd have had even the dimmest idea that something like that would solve the problem.

---

### Post by mcduck on 2007-02-25
That seems rather strange way to do this :D All GTK and icon themes should work with Beryl just like they work with normal Gnome desktop.

Anyway, I bet your problem is with gnome-settings-daemon. Remove the .gtkrc-2.0 file and then try running 'gnome-settings-daemon &' from a terminal. If (and when :D) that makes all your themes & icons work then add 'gnome-settings-daemon' to your startup programs in System/Preferences/Sessions.

---

### Post by satchelpig on 2007-02-26
> **mcduck said:**
> That seems rather strange way to do this :D All GTK and icon themes should work with Beryl just like they work with normal Gnome desktop.

Anyway, I bet your problem is with gnome-settings-daemon. Remove the .gtkrc-2.0 file and then try running 'gnome-settings-daemon &' from a terminal. If (and when :D) that makes all your themes & icons work then add 'gnome-settings-daemon' to your startup programs in System/Preferences/Sessions.

Worked like a charm, thanks.  Actually it worked despite the fact (which I just realized) that I failed to remove that file.  

Thanks to both of you and to many others who have given of your own time to help me get started in Linux/Ubuntu.  It's been fun!

---

