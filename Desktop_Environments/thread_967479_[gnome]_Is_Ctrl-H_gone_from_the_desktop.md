---
title: "[gnome] Is Ctrl-H gone from the desktop?"
date: 2008-11-02
forum: Desktop Environments
---

### Post by LucasHenderson on 2008-11-02
Prior to upgrading to Intrepid, I used to be able to toggle the visibility of hidden files on the desktop by pressing Ctrl-H. I had some .folders which I would sort stuff I saved to the desktop into, and then hide, so as to keep a clean desktop. Now, Ctrl-H has no effect on the desktop itself, though as before, it can be used while browsing the Desktop folder with Nautilus. While it may seem somewhat trivial, it's one of those small things I'd gotten used to.

I'm assuming this is related to the new version of gnome/Nautilus. I considered filing this as a bug, but I don't know if it's an intentional change or what. Is there any way to re-enable this?

---

### Post by ciscosurfer on 2008-11-02
Did you have this GConf key set to True before?

GConf key: /apps/nautilus/preferences/desktop_is_home_dir

---

### Post by ciscosurfer on 2008-11-02
In case you don't know, to enter the configuration editor, press Alt+F2, enter in **gconf-editor**, then navigate to the key I mentioned.

---

### Post by LucasHenderson on 2008-11-02
No, my Desktop is still ~/Desktop.

What I had done is I'd created a few folders on my desktop,
.Class Materials
.Unsorted Stuff
.CSassignments
.GFXprojects

By default, these folders wouldn't be visible, but all I had to do was tap Ctrl-H, and they would be. Since I upgraded, Ctrl-H doesn't work on the desktop.

---

### Post by ciscosurfer on 2008-11-02
Right, I understand what you want to do.  I remember this coming up in the past, just didn't remember exactly what the answer was :-)  Fear not!  I've found an answer for you: [http://ubuntuforums.org/showthread.php?t=789684](http://ubuntuforums.org/showthread.php?t=789684)

---

### Post by ciscosurfer on 2008-11-02
Lucas, this has gotten me intrigued (again).  You're probably trying to get those methods to work, and to no avail?  I'm having difficulty with them myself.  I can get a file to hide, but it's the unhiding part that's tricky.  Ideally a key combo would be nice for the Desktop.  I think we can get something going more along the lines of right-clicking and having Show Hidden Files / Hide Hidden Files pop up in the menu.  I used this script a while ago, but since Feisty, it hasn't worked for me (some say as of Hardy) and  I quite honestly forget all about it until now.  What we really need is a set of programmers' eyes to modify this for today's version of Ubuntu ([maybe some of these guys?]("http://ubuntuforums.org/showthread.php?t=789684")).  You should probably also ask one of the moderators to move this thread over to Development and Programming, as it's more likely to get viewed over there than over here.  But anyway, this is what the code [used to look like]("https://help.ubuntu.com/community/NautilusScriptsHowto"):```
#!/bin/sh
# When hidden files (.emacs, etc) are hidden, shows "Show Hidden Files" option.
# When hidden files are shown, shows "Hide Hidden Files" option.
# Uses gconf to toggle between the two Nautilus options.
# Should be placed in ~/.gnome2/nautilus-scripts/ with executable permission.
OLDSTATE=$(gconftool-2 --get "/desktop/gnome/file_views/show_hidden_files")
if [ "$OLDSTATE" == "false" ] ; then
  NEWSTATE="True"
  mv ~/.gnome2/nautilus-scripts/Show\ Dot\ Files ~/.gnome2/nautilus-scripts/Hide\ Dot\ Files
else
  NEWSTATE="False"
  mv ~/.gnome2/nautilus-scripts/Hide\ Dot\ Files ~/.gnome2/nautilus-scripts/Show\ Dot\ Files
fi
gconftool-2 --set "/desktop/gnome/file_views/show_hidden_files" --type boolean $NEWSTATE

```The script/nautilus action that [ryanhaigh put together]("http://ubuntuforums.org/showpost.php?p=4985689&postcount=5") is nice, but there's no way to unhide once hidden.  The script from [PinkFloyd102489]("http://ubuntuforums.org/showpost.php?p=4986335&postcount=6") seems the most concise and maybe the easiest to fix up for our needs.  I'd like to see the old script that I once used get modified so we can use it today in Hardy and Ibex and beyond!

---

### Post by LucasHenderson on 2008-11-02
Well, I could try those scripts, and I'm pretty sure if I wanted I could get them to work, but it still seems slightly annoying that I should have to use some scripts to accomplish something that was previously built in.
When I get some more free time, I might also look into putting this in as either a bug or a feature request.(not sure which, since I can't tell whether its removal was intentional.

---

### Post by ciscosurfer on 2008-11-02
I don't think using Ctrl+H directly on your desktop was ever built-in.  I don't recall ever being able to use this combination in any prior release.  Maybe you had installed something or modified something that allowed for this?  I could be wrong though.  My guess is that the developers thought that opening up your desktop folder from within nautilus would be just as easy.

---

### Post by LucasHenderson on 2008-11-05
I booted a gutsy CD(couldn't find my hardy one, but I know the result would be the same) to verify that this key combo did indeed have an effect on the desktop on previous versions of gnome/Nautilus.
[[IMG]http://img221.imageshack.us/img221/4551/screenshot1phatchof5.th.jpg[/IMG]](http://img221.imageshack.us/img221/4551/screenshot1phatchof5.jpg)
Nothing done yet.

[[IMG]http://img221.imageshack.us/img221/7572/screenshot2phatchxg6.th.jpg[/IMG]](http://img221.imageshack.us/img221/7572/screenshot2phatchxg6.jpg)
Created a test folder called "Test Folder"

[[IMG]http://img221.imageshack.us/img221/7062/screenshot3phatchkn7.th.jpg[/IMG]](http://img221.imageshack.us/img221/7062/screenshot3phatchkn7.jpg)
Renamed "Test Folder" to ".Test Folder"


[[IMG]http://img221.imageshack.us/img221/3917/screenshot4phatchcr0.th.jpg[/IMG]](http://img221.imageshack.us/img221/3917/screenshot4phatchcr0.jpg)
Hit F5 to refresh, folder is now hidden

[[IMG]http://img221.imageshack.us/img221/4755/screenshot5phatchys4.th.jpg[/IMG]](http://img221.imageshack.us/img221/4755/screenshot5phatchys4.jpg)
Pressed Ctrl+H, folder is made visible(and afterwards successfully hidden again, by pressing Ctrl+H again)

---

### Post by ciscosurfer on 2008-11-05
Cool.  Would love to know how it's done.  Maybe it only works in a live environment?

---

### Post by LucasHenderson on 2008-11-07
No, I'm quite sure it's also present in installed versions. Again, I was able to use that feature on my current install, until I upgraded to Intrepid. It's not anything super special. Under gnome, nautilus manages the desktop, as well as the folder browsing window. Because of that, a  number of key combinations are shared, Ctrl-H and F5 refresh, Ctrl-Shift N, creates new folders, etc. Ctrl-H used to be one of those shared key combos.

 I've been using Ubuntu since mid/early 2007, and it's been my primary OS for about 6 months. I know the combo has worked since at least Feisty. I've done 2 clean installs, so I'd probably know if it were something special I installed or configured to get it to work like that.

---

### Post by ciscosurfer on 2008-11-07
Perhaps it is a bug.  Maybe it was done intentionally.  Either way, I'd say your next stop should be Launchpad.  If you find anything, please post your results here.

---

