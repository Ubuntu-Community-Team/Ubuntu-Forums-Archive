---
title: "Ubuntu updates shared across the network"
date: 2013-10-13
forum: Desktop Environments
---

### Post by Bob_Baker_Jr. on 2013-10-13
My current network does not have a very fast or large bandwidth for its internet connection, and I happen to have quite a few ubuntu desktops on my network. To help minimize overhead on my network when security updates are released, I wanted to see if there was a way I could designate one of my desktops as a master update server for the rest of my ubuntu PC's. My first thoughts are basically to add this master server's LAN IP address to the sources.list file that would be checked first and foremost, that way my large LAN infrastructure could easily disperse these updates to the other PC's without any extra internet overhead. I was wondering if that is feasibly possible to do as of 12.04.3, and if so how to accomplish it? Obviously this would be great to do later down the road for any server groups I would have to help reduce the outbound internet traffic once a large influx of security updates are required with a new server installation (when the desktop and server versions are freshly installed, the updates list gets to be about 500+ updates, and having to download them over the internet can take quite some time), so sharing the updates on my 1Gbps lines within my network would be significantly faster than 10-12 PC's or Servers all trying to download these updates at the same time, when instead one could download them, and then spread these updates across the network much faster than the others could possibly download them (I know I'm getting repetitive).

I understand that package-specific updates that only a small group of machines would be using would need to get their updates from the internet, but these aren't my worry, its the massive 500+ ubuntu updates that come with installing a new desktop or server on the network and having to download them at a very slow rate as opposed to fetching them from a server or desktop on my network at 1Gbps. This would also be perfect for LTS upgrades since only one machine would have to download the ISO and updates for it once, and spread it over the network once it is installed, thus keeping the outbound traffic to a minimum.

---

### Post by Irihapeti on 2013-10-13
Apt-cacher-ng is made for this purpose and is available in 12.04. You can install it on one machine and have all the other machines get their updates from it. [http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/](http://linuxexpresso.wordpress.com/2011/02/13/howto-apt-cacher-ng-on-ubuntu/) gives brief instructions on setting it up, and the complete user manual is at [http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html](http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html)

Essentially, one machine is a server and the others use it as a proxy. I've found it very useful when doing a complete reinstall plus updates, because most of the packages can be reused.

---

