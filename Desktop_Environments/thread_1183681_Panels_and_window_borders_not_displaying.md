---
title: "Panels and window borders not displaying"
date: 2009-06-10
forum: Desktop Environments
---

### Post by bobtfish on 2009-06-10
Solved (ish, completely reinstalled).

(Standard 9.04, gnome, compiz setup)
A few days ago my laptop stopped displaying the panels and window borders, making it nigh on impossible to do anything. 
I looked here: [http://ubuntuforums.org/showthread.php?t=1178765]("http://ubuntuforums.org/showthread.php?t=1178765") without too much luck.

However, if I right click on the Desktop and go to Change Desktop Background, then click any of the settings for Visual Effects, it brings back the window borders, and the other effects work fine (wobbly windows, scroll wheel switching between desktops, ...), but the panels are still not there. I can bring those back using a desktop launcher to run gnome-terminal, and running gnome-panel. However all this goes again as soon as I log out.
Once I had the panels back I created a new user and tried that, which worked fine, which I think indicates my user settings have been messed up.

So, does this seem likely? And how would I go about restoring them? Also, I'd be glad to know what might have caused this, in particular if it has any relation to some trouble I had installing Maple (a mathematics program used by my University) that day.
It has a Java interface which wasn't working properly, so on the advice of this page: [http://ubit.buffalo.edu/software/linux/maple11.php]("http://ubit.buffalo.edu/software/linux/maple11.php") I installed the Sun JRE (which I thought I had, but it seems the default one is a non-Sun alternative), which did a lot of nothing. Now I have Maple being launched from a script that includes the command on that page, and a bit ripped off from the default Maple launch script:
```

export AWT_TOOLKIT=MToolkit;

MAPLE='/home/chris/maple11'
export MAPLE 

"${MAPLE}/bin/maple" -x $*

```

---

### Post by miniyak on 2009-06-10
im not sure how your panels disappeared but i do without window decoration and borders just to simplify everything and just use alt-F4 to close windows

i'm assuming you are using the compizconfig setting manager in which case you may have accidentally disabled "window decoration". this may be how you lost window borders

---

### Post by amadeus266 on 2009-06-10
Try installing fusion-icon. You can then right-click the icon and reload the entire windows manager or just the window decorator, or even turn off compiz all together.

---

### Post by bobtfish on 2009-06-11
Thanks for the suggestions, but still not working. In the CompizConfig Settings Manager everything is still set as it should be, I even tried switching Window Decoration on and off a few times, nothing changed. It did work as expected after I had run compiz and gnome-panel from terminal.
It seems they are failing to start properly when I log in, as everything runs as normal if I start them myself, but as soon as I log out and in everythings gone again.

---

### Post by miniyak on 2009-06-11
Personally i have some missing panel items(power&network), so i have been looking around for solutions to get them back. Take a look at this thread- [http://ubuntuforums.org/showthread.php?t=1183848]("http://ubuntuforums.org/showthread.php?t=1183848"), the solution that netjackdaw found may work for you. Apparently it resets everything to default settings. i haven't tried it cause i only want a few items back and not have to redo all my customization

---

### Post by bobtfish on 2009-06-12
Thanks for finding that. I tried it this morning, and it did reset the panels to default behaviour, but they still don't load on log in. At least this seems to indicate that the settings file(s?) are being read ok.
I think it might work if I add gnome-panel and compiz to the login programs (I think Services, under the System menu?) but a) I'm not home right now, and b) that feels like working round the problem rather than solving it. Which is better than nothing of course, but I'd rather know why it's suddenly stopped, and sort it out directly.

---

### Post by Brandon Williams on 2009-06-12
Run the following commands and check the settings:
```
$ gconftool-2 --get /desktop/gnome/applications/window_manager/current
/usr/bin/metacity
$ gconftool-2 --get /desktop/gnome/session/required_components_list
[windowmanager,panel,filemanager]
$ gconftool-2 --get /desktop/gnome/session/required_components/panel
gnome-panel
```
I expect that the output from the first command on your system will be '/usr/bin/compiz'. The output from the second two commands should be identical. Is it?

If the first command doesn't list the correct path to the compiz executable, then compiz might not start when you login. If the second command doesn't include 'panel' in the list or the third command doesn't output gnome-panel, then the panel might not start.

---

### Post by bobtfish on 2009-06-12
Thanks for the response. My settings are correct:
```

$ gconftool-2 --get /desktop/gnome/applications/window_manager/current
/usr/bin/compiz

$ gconftool-2 --get /desktop/gnome/session/required_components_list
[windowmanager,panel,filemanager]

$ gconftool-2 --get /desktop/gnome/session/required_components/panel
gnome-panel


```

Also, if it narrows things down, I tried the various login options (xclient script, gnome, gnome failsafe) and had the same problem each time.

Edit:, and 
I also just tried "deleting" (moving so I could bring them back) a bunch of settings files: .compiz .config .gconf .gconfd .gnome2, and none of that helped (although, it did make the places menu try to open folders with rhythmbox, but I'm not worrying about that now).

---

### Post by bobtfish on 2009-06-16
Well I ended up completely reinstalling Ubuntu (had caused a few sound problems and file/program mismatches as well, too much playing about without knowing what I was doing I suppose). Thanks to everyone for the suggestions anyway.

---

