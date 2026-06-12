---
title: "No bar, no Window Manager issue [9.04 notebook remix version]"
date: 2009-06-25
forum: General Help
---

### Post by id.pedro on 2009-06-25
First of all, hello !
I'm new to either this forum and to the linux OS, realy new.

So... I just installed this new version and made the proper updates, but, once I turned my lap on again, the initial bar and window manager program didn't load. I read some stuff here and on some other forums about this issue. The main solution given was to rename a file called session, on ~/.gnome2 , but there is no such file on my folder.

I managed a solution, going on Start up programs and, as read on the forums, added the gnome-panel and the metacity commands.

It actually worked, but I realy want to know about the session file thing... also, the new Desktop style of ubuntu doesn't work quite right...

I hope I could make myself clear, but if I didn't, do tell so I can try and explain it better

Anyway, I'm already greatful for any help I can get.
Thanks

---

### Post by Vikhyath on 2009-06-25
Does Ubuntu accept your login? or is this where the problem arises? screenshots would be helpful

---

### Post by id.pedro on 2009-06-25
I can login just fine, but, the desktop bar wasn't showing, just like what happened in this thread: [http://ubuntuforums.org/showthread.php?t=406225](http://ubuntuforums.org/showthread.php?t=406225)
and also, I had issues with the window manager, like, the windows weren't opening on full screen an sorts...

They said, on this old thread that one way of solving it was to rename the session file, but I can't find it where it was supposed to be.

So, like I said, I figure a way to solve it by adding the metacity and gnome-panel commands, but still, I'd like to know why did it happened and why can't I find this session file.

thanks

---

### Post by davidryderuk on 2009-06-25
It sounds more similar to this problem.

[http://ubuntuforums.org/showthread.php?t=1139314](http://ubuntuforums.org/showthread.php?t=1139314)

You might want to read the post shown below.

> This a bug in the desktop-switcher package ([https://bugs.edge.launchpad.net/desk...er/+bug/349519](https://bugs.edge.launchpad.net/desk...er/+bug/349519)), which I'm trying to fix and get uploaded to Jaunty before release.

To fix the issue you have currently (gnome-panel and/or windowmanager not starting), please run the following command depending on which mode your currently running in:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I have updated desktop-switcher .debs available in that bug for which I am looking for testers (I would appreciate feedback on that bug). Once you've run the above commands, you can install the latest deb from that bug and hopefully further switches will work without issue.

Thanks and sorry for desktop-switcher screwing up

-- Neil

The commands mentioned should be run in terminal. 

The folder you were trying to find is a hidden file, as donated by the dot at the front of the name. You should be wary of touching these files as they contain all the program settings you may have changed since installing Ubuntu on your computer. Hence deleting these files effectively takes your computer back to 'factory settings'. If you want to see them however just use the key combination ctrl+H when viewing the home folder.

---

