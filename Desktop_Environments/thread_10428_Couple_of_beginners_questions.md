---
title: "Couple of beginners questions"
date: 2005-01-07
forum: Desktop Environments
---

### Post by palomar on 2005-01-07
Hello, I just installed Ubuntu. I'm not very experencied with Linux (already tried some distro's). I've searched google and ubuntu site/documentations, but some things i cant solve :(

1. When I try to access shares on a windows XP computer, i seethe workgroupname and i can browse the network (in Gnome), but when I click on a computername i get the  error:
> The filename "XP1800" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.[.....]

2. I cannot play MPEG files with Totem (default movie player). Error: Failed to open; reason unknown :S

3. more to come......

---

### Post by hardcandy on 2005-01-07
Have you set up folders to be shared on the WinXP side?
What number are the mpeg files? mpeg2, mpeg4?

---

### Post by jdodson on 2005-01-07
[QUOTE=palomar]
2. I cannot play MPEG files with Totem (default movie player). Error: Failed to open; reason unknown :S[/QUOTE]

read the [http://www.ubuntuguide.org](http://www.ubuntuguide.org) to get mpg, mp3 and anyother playback for ubuntu.  they even have directions on getting stuff to work in firefox for quicktime/realvideo/wmv streams.  

rock on.

---

### Post by CompShrink on 2005-01-07
As for 1, what is the entire message? Does it let you click "ok" vs "cancel"?

As for 2, yes, the default multimedia player is rather weak. I would suggest VLC. Use synaptic (on the top panel: Computer > System Configuration > Synaptic Package Manager) to install it, just make sure you include the universe. If my memory fails me, it might be on multiverse, which can be added same as universe. In synaptic, go to Settings > Repositories and check the boxes for universe and multiverse, if they are no there, add them;
URI:             [http://archive.ubuntu.com](http://archive.ubuntu.com)
Release:      warty
Section(s):   universe muliverse

also, refer to the link in the post above mine, though I consider VLC to be easier, it doesn't require any fo the optional libraries like w32codecs which is of questionable legality in the US.

---

