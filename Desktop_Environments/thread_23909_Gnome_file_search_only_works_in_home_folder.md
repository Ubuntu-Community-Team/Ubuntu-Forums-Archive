---
title: "Gnome file search only works in home folder"
date: 2005-04-04
forum: Desktop Environments
---

### Post by jnoreiko on 2005-04-04
Gnome's search for files tool (gnome-search-tool from the command line, of Computer -> Search for files) has a dropdown box for the start location, which lists my home folder and the filesystem root.

However, a search initiated on the root stops immediately (no hard drive activity, unlike searching in my home holder) and yields the message "no files found".

I understand that searching the root may have problems with permissions, but having the option there suggests to the user that it's possible.

Is this a bug in ubuntu or in gnome? Should I report it or has it been fixed in newer versions?

---

### Post by allans on 2005-04-04
In the console run sudo updatedb, then try your search again.

Allan

---

### Post by jnoreiko on 2005-04-05
Thanks!

---

### Post by Jagera27 on 2005-04-05
[QUOTE=allans]In the console run sudo updatedb, then try your search again.

Allan[/QUOTE]

I have warty. Yes I tried this, but it doesn't allow all files to be found from root. I just downloaded and extracted some files that appear in File Browser in /tmp but are not found by Search for Files. They can be found but only if you choose /tmp to search in. If it's not a bug then its poor implementation and very discouraging for newbies like me. Sure hope they address these simple user issues at the Sydney Conference.

---

### Post by allans on 2005-04-05
I'm no expert on the gnome search tool, but I remember on mandrake 10 running updatedb and it crashed the whole system, although that was a kde distro, no idea how kde handles searching.

If you search the entire filesystem, you will have to run updatedb beforehand so that gnome search knows whats there.  The idea being that it can find things much faster if its been indexed, like a google search.  If you leave the search running long enough, it might find it, but that obviously isn't optimal.

Hoary has the same search features, as far as I've seen anyway, same problems with updatedb.  Breezy (the next release) should feature beagle and dashboard which will vastly improve searching, check out the website here: [www.gnome.org/projects/beagle](www.gnome.org/projects/beagle).  There is no need to update the database and it constantly updates its search results with relevant information.

Btw you should keep any downloads etc in your /home directory if possible unless instructed otherwise.

Allan

---

### Post by iomicifikko on 2005-04-06
[QUOTE=allans]I'm no expert on the gnome search tool, but I remember on mandrake 10 running updatedb and it crashed the whole system, although that was a kde distro, no idea how kde handles searching.

If you search the entire filesystem, you will have to run updatedb beforehand so that gnome search knows whats there.  The idea being that it can find things much faster if its been indexed, like a google search.  If you leave the search running long enough, it might find it, but that obviously isn't optimal.

Hoary has the same search features, as far as I've seen anyway, same problems with updatedb.  Breezy (the next release) should feature beagle and dashboard which will vastly improve searching, check out the website here: [www.gnome.org/projects/beagle](www.gnome.org/projects/beagle).  There is no need to update the database and it constantly updates its search results with relevant information.

Btw you should keep any downloads etc in your /home directory if possible unless instructed otherwise.

Allan[/QUOTE]
 i usually use

$sudo find / (or any other dir u wanna start from) -name (searching in filenames) string_to_search (usually between **)

bye

---

### Post by Jagera27 on 2005-04-06
Thanks Allan. I just did another sudo updatedb and sure enough Search for Files was now able to locate new files that it hadn't previously. However it still couldn't see things in /tmp. Maybe /tmp is a special case? But anyway who wants to wait whilst the rather lengthy update takes place-surely this could have been going on in the background periodically. I will be looking forward to new Search versions for sure.

Nick
PS this is not the first time this gripe has been raised

---

### Post by skyryder on 2005-05-07
Could not find "Search for Files", but did stumble on "slocate" under cli.
[man locate, or info locate, for more]
Cheers

---

