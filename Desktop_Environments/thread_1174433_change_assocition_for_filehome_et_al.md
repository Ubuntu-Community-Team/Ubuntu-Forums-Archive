---
title: "change assocition for file:///home et al"
date: 2009-05-30
forum: Desktop Environments
---

### Post by narnie on 2009-05-30
Hello,

I seem to be having the same problem that several others have been having without a resolution.

I have ubuntu (8.10) installed, but also have xfce installed, which has made thunar take over my places->home and so on.

There is a script out there that changes the default file manager/file browser from nautilus to thunar and a separate one to change it back. This doesn't work for those of us having this problem.

Also, running nautilus and right-clicking a file and selecting open with -> file browser doesn't work. Nor does changing the folder properties-> open with tab to file browser (if it is not there, click add and enter nautilus)

I have deleted the ~/.local/application/mimeapps.list and even deleted the thunar reference there.

After each of these steps, gnome was restarted with ctrl-alt-backspace

To see more about what is going one, I changed the name of the Thunar binary in /usr/bin/

Then clicking on places->home gives an error 

Could not open location 'file:///home/myusername'
Failed to execute child process "Thunar" (No such file or directory)

so it is a problem with the association of 'file://' Where is this controlled?

As a temporary work-a-round until as solution is found, I have done a symbolic link of Thunar to nautilus, but this means I have to run Thunar binary as a separate command (I've renamed it Thunar2) and i'm sure xfce is useless from the file management standpoint but at least I get nautilus when I click places->home in gnome

Where are associations like 'file://' kept and how can they be edited such as when you alt-F2 and put in 'file:///home' it will bring up the correct file manager?

This has been listed as a bug report seemingly for years, but it seems it is low on the totem pole in priority.

With thanks,
Narnie

Also, from this thread [http://ubuntuforums.org/showthread.php?t=299927]("http://ubuntuforums.org/showthread.php?t=299927") I checked the /usr/share/applications listings there. Each had nautilus as the command. Hence, the problem doesn't live at this level.

---

### Post by Colt725 on 2009-05-31
Update to nautilus - 1:2.26.1-0ubuntu2 use synaptic package manager.

---

### Post by narnie on 2009-05-31
Well, I looked in Synaptic and there is no option for a Nautilus of that version. I have looked at intrepid backports even jaunty backports and nothing is there either. I know the version you recommend is the one used in jaunty, but don't see how to get it (reasonable stabily that is) for intrepid.

---

