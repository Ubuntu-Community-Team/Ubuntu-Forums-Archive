---
title: "Repository error..."
date: 2005-09-24
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-24
Here's an error message that I got after I tried to update my synap with top-left button that I clicked. Any ideas what it is and how I could fix it?

---

### Post by bsussman on 2005-09-24
Help me here - what part of the error message is unclear?

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=bsussman]Help me here - what part of the error message is unclear?[/QUOTE]
It says that the repository is unavailable. How would I switch to another repository so that this won't happen?

Or is the error temporary?

---

### Post by bsussman on 2005-09-24
I am not trying to play silly buggers with you - I dont know if there is a mirror and the only way to know if it is temporary is to talk to them.

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=bsussman]I am not trying to play silly buggers with you - I dont know if there is a mirror and the only way to know if it is temporary is to talk to them.[/QUOTE]
I'm not sure how 8-[ .

---

### Post by imagine on 2005-09-24
[QUOTE=][/QUOTE]
 Is there a special reason why you need the Marillat-repository? Be aware that it's a general Debian-repository, even though most of the software works well in Ubuntu without problems.
I can access the Marillat-server at the moment, so maybe it was just down earlier today?

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=imagine]Is there a special reason why you need the Marillat-repository?[/quote]
Well, since I'm not that familiar with Linux, in general, I really didn't know what that error was, so I figured that it must be important.

If someone thinks that this is a no big deal, then they can say so.

BTW, I tried sudo apt-get update in console and this is what I got at the very end...
```
Err ftp://ftp.nerim.net testing/main Packages
  Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Fetched 4B in 2s (2B/s)
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz  Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
Again, if someone thinks that this is something that I should not be worried about, then you can say so and I'll leave the matter as it is.

---

### Post by imagine on 2005-09-24
[QUOTE=YourSurrogateGod]If someone thinks that this is a no big deal, then they can say so.[/QUOTE]Of course an error should not be ignored, i just wanted to know why you need this Debian-repository. The Marillat-repository isn't included in Hoary or Breezy by default, so for some reason you must have added it. If you don't know this reason anymore or there never was one, I recommend removing that repository from the list.
Having the Ubuntu main/restricted/universe/multiverse/backports-repositories and the unoffcial extras-repository should be enough for most of the users ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories))


[QUOTE=YourSurrogateGod]BTW, I tried sudo apt-get update in console and this is what I got at the very end...
```
Unable to fetch file, server said 'Can't open /debian-marillat/dists/testing/main/binary-i386/Packages.gz: No such file or directory  '
```[/QUOTE]Your problem ist, that there's no testing directory anymore on the server. Since the Marillat-repository is a Debian-repository and some weeks ago a new stable release of Debian came out, the names have changed (see [http://www.debian.org/releases/)](http://www.debian.org/releases/)). If you really need the Marillat-repository replace "testing" in your apt-sources with "etch". If you don't, just remove this repository.

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=imagine]Of course an error should not be ignored, i just wanted to know why you need this Debian-repository. The Marillat-repository isn't included in Hoary or Breezy by default, so for some reason you must have added it. If you don't know this reason anymore or there never was one, I recommend removing that repository from the list.
Having the Ubuntu main/restricted/universe/multiverse/backports-repositories and the unoffcial extras-repository should be enough for most of the users ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories))[/quote]
Ohh... I follow ya. I got rid of the extra repository. Thanks for your help :) .
[quote=imagine]Your problem ist, that there's no testing directory anymore on the server. Since the Marillat-repository is a Debian-repository and some weeks ago a new stable release of Debian came out, the names have changed (see [http://www.debian.org/releases/)](http://www.debian.org/releases/)). If you really need the Marillat-repository replace "testing" in your apt-sources with "etch". If you don't, just remove this repository.[/QUOTE]
Nah... I think I'll be fine without that repository.

---

