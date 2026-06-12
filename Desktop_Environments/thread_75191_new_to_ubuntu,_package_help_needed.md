---
title: "new to ubuntu, package help needed"
date: 2005-10-13
forum: Desktop Environments
---

### Post by tbr on 2005-10-13
I am in no way new to linux but am definitely not an expert.  I just installed Ubuntu on my laptop and am trying to finish configuring it but am having some issues adding programs through both add applications and synaptic.  I have enabled all repositories and am trying to install gstreamer-mad, eclipse, vlc, and mono/monodevelop.  each one, as expected, has dependencies, but it puzzles me why some of them are "not installable."  for instance, gstreamer0.8-mad depends on libid3tag0 and libmad0, both of which are declared "not installable."  the only possible thing i could think of is that they have not yet been tested with breezy and are therefore being blocked.  this still should not prevent me from installing them, rather simply warning me would be sufficient.  i would prefer not to simply download the packages from their respective websites and install them that way since it would defeat the purpose of synaptic, but i am willing to do so if it is the only way.

---

### Post by kassetra on 2005-10-13
[QUOTE=tbr]I am in no way new to linux but am definitely not an expert.  I just installed Ubuntu on my laptop and am trying to finish configuring it but am having some issues adding programs through both add applications and synaptic.  I have enabled all repositories and am trying to install gstreamer-mad, eclipse, vlc, and mono/monodevelop.  each one, as expected, has dependencies, but it puzzles me why some of them are "not installable."  for instance, gstreamer0.8-mad depends on libid3tag0 and libmad0, both of which are declared "not installable."  the only possible thing i could think of is that they have not yet been tested with breezy and are therefore being blocked.  this still should not prevent me from installing them, rather simply warning me would be sufficient.  i would prefer not to simply download the packages from their respective websites and install them that way since it would defeat the purpose of synaptic, but i am willing to do so if it is the only way.[/QUOTE]

not installable usually means that the dependencies are in a different repository that you have not added / enabled - therefore it can't actually pull the files and install them; files are never blocked - they are either released or not, but that is not to say that a dependency might be in another repository.  Since you have enabled all the repositories, I would likely say that you need to add a repository to your list in order to install.

The repositories section most likely has the correct repositories for you to use, I cannot remember off the top of my head which ones you will need.

---

### Post by XDevHald on 2005-10-13
When installing packages they do require dependencies, in which some might not be installable and also depend on others to be installed. While doing this some packages and dependencies might not have a version ready for it to be released but just be sitting there to show it's going to be updated with a newer version.

Also, check if you're sources.list is up to date as I had the same problem just a few minutes ago before I updated my sources.list (This does make a difference and a big deal on what packages are being shown in synaptic)

I hope this helps a bit

---

### Post by tbr on 2005-10-13
where would i go about updating or comparing my sources.list to ensure it was up to date?

---

