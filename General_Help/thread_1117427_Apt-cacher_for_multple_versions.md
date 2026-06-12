---
title: "Apt-cacher for multple versions"
date: 2009-04-05
forum: General Help
---

### Post by kpoole on 2009-04-05
Quick background,  I have a number of machines on a LAN, one is running Hardy Heron Server with LAMP and serving as the apt-cacher for the other machines on the LAN still running Hardy Heron.  I have a few machines running Intrepid Ibex and one of those machines is running as the apt-cacher for Intrepid Ibex.

I realize what I'm asking might be considered bizarre but is there a way to run two instances of apt-cacher on a single machine so that single machine can be the apt-cacher for two versions of Ubuntu (and, eventually, three or more version as Jaunty Jackalope and K???? Koala coma along.) 

I'm sure it would require two different /var/cache/apt-cacher directories and different port numbers but being a bit on the lazy side I'd rather not re-invent the wheel if someone can point me to a set of directions to do this.

I might try to anticipate a question and answer "why keep Heron around so long if you're working with the other versions?"  Heron is a LTS version so it's on the machines that handle the email and other things that we don't want to upset at each version change but there are advantages to having the newer versions available on some machines as well.

Thanks in advance if you can point me in the direction of being able to do this.

---

### Post by Sam Lars on 2009-04-07
I would think that the apt-cache server would be able to handle different versions.  It would just keep copies of the different package versions.

---

### Post by kpoole on 2009-04-08
> **Sam Lars said:**
> I would think that the apt-cache server would be able to handle different versions.  It would just keep copies of the different package versions.

Sorry, I hadn't got back here yet but that seems to be correct.  An exchange with another user in a different thread pointed out that the single instance should be able to handle multiple versions and the quick test showed that seems to be true.  I have gotten side tracked just a bit by realizing that I was still working from 8.04 install disks when there were 8.04.2 versions available that included most of the hundreds of updates that I was caching and trying to update on my experiment.

I'm just installing an Ubuntu 8.04.2 and going to see how many updates there are from there before I go on.  I may restart the apt-cache from scratch after the 8.04.2 install.  The other thing to try is whether the distribution upgrade from 8.04 to 8.10 to 9.04 works through the consolidated apt-cacher.

more info - No, the distribution update process doesn't work through apt-cacher.  You can update the installed version to the next version using the alternate install CD for the new version and then pickup any further changes through the apt-cacher machine.  However, the amount of time it takes to update from the alternate install CD seems to take longer than doing a fresh install from the live desktop CD.

Anyway, I now have a little old machine sitting aside acting as the apt-cacher for the various other machines and their different versions and it works very nicely.

---

