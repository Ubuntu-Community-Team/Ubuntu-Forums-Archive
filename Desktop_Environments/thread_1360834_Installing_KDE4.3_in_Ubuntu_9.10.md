---
title: "Installing KDE4.3 in Ubuntu 9.10"
date: 2009-12-21
forum: Desktop Environments
---

### Post by snoguy986 on 2009-12-21
I'm in need of some help.  I have searched and searched (this site and google) for some sort of guide or informative web page that will allow me to install KDE4.3 in Ubuntu.  I like both desktop environments and I'd like to have both available on my system.

I found one guide [html]http://tuxarena.blogspot.com/2009/08/how-to-install-kde-43-in-ubuntukubuntu.html[/html] that showed how to install 4.3 on Ubuntu 9.04, however when I tried changing the deb line from```
[COLOR=black]deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main[/COLOR]
```[COLOR=black]to[/COLOR]```
[COLOR=black]deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main[/COLOR]
```and I ran ```
sudo apt-get update
``` it comes back with an error stating that the public key is not available.  I have no idea where to obtain the public key for this repository and it isn't listed in the guide I mentioned above.

Any help on this would be greatly appreciated.  Thank you.

---

### Post by snoguy986 on 2009-12-21
So after doing a bit more digging, I discovered that the public key usually can be found at the PPA site you're trying to add as a repository.  I pointed Firefox to [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) and searched from there.  I managed to find a file called "Release.gpg".  From what I can recall, that is an encrypted key, either public or private.  I saved it to my desktop and tried importing it into Ubuntu's Authentication section, but it wouldn't do it, stating "The selected key may not be a GPG key or it might be corrupt."

Hoping this helps anyone who knows what might be going on.  Thanks.

---

### Post by snoguy986 on 2009-12-21
Found the solution to the problem.  Solution is found at this page: [http://ubuntuforums.org/showthread.php?t=1053126](http://ubuntuforums.org/showthread.php?t=1053126)

---

