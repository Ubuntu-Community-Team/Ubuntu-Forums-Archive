---
title: "File not showing up in Nautilus"
date: 2009-11-07
forum: Desktop Environments
---

### Post by pveurshout on 2009-11-07
I'm having a really strange problem with Nautilus. For some reason it doesn't make all icons appear in a certain folder. What happens is this:

1) I double-click the folder (while being in its parent) and Nautilus opens it.
2) The folder contains one folder and one pdf-file. The folder shows up just fine, the pdf-file does not.
3) The cursor changes into this 'hour glass equivalent'-icon (it's an 'hour glass' in Windows; I don't know what to call this thing under Gnome. Think you know what I mean, though.) and stays like that. Reloading has no effect.
4) If I open the folder that's within this folder, and then hit 'Up' or 'Back' (to go back to the folder where the problem occurs), everything works just fine all of a sudden.
5) It keeps working fine until I close Nautilus and open it again.

**This is what I already tried:**
If I copy the file to another folder it works just fine, but if I then remove it from its original location and copy it back, I'm getting the same problem all over again.

I've changed the file and folder names, shortened them to make sure it had nothing to do with a path that's too long, but unfortunately that all led to nothing. In a terminal window it has no problems and just shows up when I give the 'ls' command, so it seems like it has to do something with Nautilus.

I just remembered that there's a symbolic link somewhere in the path. When I go to this folder without using the symbolic link but just by following its real path, it works just fine. Shouldn't be a problem, though, as all other files that I access via this symbolic link work just fine.

**(update)** I made a copy of the file and put it on my Desktop. If I then try to copy the file to the respective folder (while it does not show up in Nautilus), I do get a message that the file already exists and whether I want to overwrite it. Somehow it does seem to know it's already there.

Anyone have any ideas on this? :)

---

### Post by Simian Man on 2009-11-07
It could be the fact that Nautilus, by default, displays those file previews for PDF files.  Perhaps the code to do that is not handling symbolic links (thought that does seem unlikely) and is not able to generate the preview and so hangs.

Try turning off the previews (under Edit->Preferences->Preview tab) temporarily and see if that fixes the problem.

---

### Post by pveurshout on 2009-11-07
That actually did the trick! However, I have many more pdf-files which I access through the same symbolic folder, all of which show up just fine with the previews enabled. The file that's causing problems is not even unusually large (1.1 MB).

---

### Post by pveurshout on 2009-11-07
I just rebooted and now it's fine again. Still curious as to why it showed such behavior, though. Anyway, thanks for your help :)

---

