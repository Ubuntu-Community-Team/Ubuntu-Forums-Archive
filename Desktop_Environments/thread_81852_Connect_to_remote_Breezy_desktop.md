---
title: "Connect to remote Breezy desktop"
date: 2005-10-25
forum: Desktop Environments
---

### Post by mbailey on 2005-10-25
I have two boxes running breezy and would like to be able to manage both of them using the gui from the same screen & keyboard. Earlier attempts (under Hoary) to xterm over & run a gnome session apparently resulted in two copies of gnome fighting to control the screen. I tried VNC from a windows box to one of the breezy boxes, which was OK except that I have to leave a gnome desktop session logged in all the time & assume that the same restiction would be in force breezy to breezy.

How can I perform a secure, authenticated, connection to show the gnome desktop from one breezy box on the other?

---

### Post by Appolusionist on 2005-10-25
[COLOR=black]I would suggesting looking at FreeNX. Follow the steps listed [here]("https://wiki.ubuntu.com/FreeNX?highlight=freenx") for getting it installed for Breezy. It is secured via ssh and you don't have to leave a gnome session logged in as you do with VNC. I have multiple Ubuntu desktops myself and have had no problems with it. In my opinion as with many others here... It is alot faster than VNC, but of course YMMV. :) [/COLOR]

---

### Post by matw on 2005-10-25
I just tried to get the freenx package as described at [http://wiki.ubuntu.com/FreeNX](http://wiki.ubuntu.com/FreeNX) , but apt-get (and aptitude) report that "the public key is not available". Apt-get is a little more verbose: before reporting the   error, it says "Failed to fetchd http://<snip>/freenx/binary-amd64/Packages.gz 404 Not Found".

Any idea how I can work around this?

#ubuntu on freenode came to the rescue ...
from [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) ...

> 
 Packages is this repository can be gpg authenticated. The key that is being used for signing the packages is 1135D466. You can enter this key into the APT trusted keys database with the following commands:
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466
gpg --export --armor 1135D466 | sudo apt-key add -


---

