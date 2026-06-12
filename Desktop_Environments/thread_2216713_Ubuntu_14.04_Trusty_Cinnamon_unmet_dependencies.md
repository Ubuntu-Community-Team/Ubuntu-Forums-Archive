---
title: "Ubuntu 14.04 Trusty Cinnamon unmet dependencies"
date: 2014-04-13
forum: Desktop Environments
---

### Post by Redalien0304 on 2014-04-13
Have unmet dependencies with Ubuntu Trusty Cinnamon Nightly
"the following packages have unmet dependencies:
 cinnamon : Depends: cinnamon-translations (>= 2.2.0) but 2.0.3-20140413040026-trusty is to be installed
            Depends: cinnamon-control-center (>= 2.2.0) but it is not going to be installed
            Recommends: cinnamon-bluetooth but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

Had some Older kernels (3.13.22) Autoremoved them no problems. but Cinnamon Cinnamon-control-center cinnamon-translations were being Held back. tried upgrading these packages but they removed insetad. Tried upgrading Via sudo apt-get cinnamon upgrade & so on. they were removed instead. Cannot Reinstall Cinnamon keep getting unmet dependencies: with Msg above.
Any Info is much Apprciated Thanks.

---

### Post by Redalien0304 on 2014-04-13
Update: Installed Ubuntu Trusty & updated on another another partition, Exact same message
"the following packages have unmet dependencies:
 cinnamon : Depends: cinnamon-translations (>= 2.2.0) but 2.0.3-20140413040026-trusty is to be installed
            Depends: cinnamon-control-center (>= 2.2.0) but it is not going to be installed
            Recommends: cinnamon-bluetooth but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Also tried Stable version (changed Repo from trusty to saucy) Exact same thing.
So does this mean Cinnamon is Broken??
Any info much Appreciated Thanks

---

### Post by Frogs Hair on 2014-04-13
> Cinnamon Nightly You are running an unstable Cinnamon build on an unreleased operating system so you may have to be patient until the final release of 14.04 because there are usually quite a few updates in the last days. The stable version should be working by release day and if not  a bug report would be in order.

From   Launchpad > /!\ WARNING : Nightly builds are unstable, use only for debugging purposes /!\

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly)

---

### Post by Redalien0304 on 2014-04-14
I have also tried the Cinnamon Stable same Results. I believe cinnamon is currently broken. Have also Tried Cinnamon Stable/Nightly on Ubuntu Gnome 14.04 also. Not getting the unmet dependencies, but is starting in flashback  mode. Any help is Appreciated Thanks.

---

### Post by Frogs Hair on 2014-04-14
I use 14.04 Unity/Gnome Shell, but haven"t tried Cinnamon since 13.04 and I don't want test it because it was hard to remove. Even with a PPA Purge. The PPA may have caused dependency problems if it wasn't  fully purged. If there were any upgraded libs left from the the nightly build it could cause problems with any Cinnamon version installed.

---

