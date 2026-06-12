---
title: "nVidia drivers problem"
date: 2006-07-04
forum: Desktop Environments
---

### Post by PryGuy on 2006-07-04
Hello there!
Ubuntu team has removed the "nvidia-glx" package from the 6.06 distribution? Is that possible? How do I install the bloody thing? The [recommendations from there]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") have really crashed my system. What do I do about the nVidia drivers?:cry:

---

### Post by Jagot on 2006-07-04
They haven't removed it - it was never included with the distro - it's in the restricted repo's.  The instructions there are fine.  Try removing the packages and try again.

---

### Post by PryGuy on 2006-07-04
I bet you are wrong!;) nvidia-glx was included in 5.10, I was installing it from the  Ubuntu 5.10 CD!

---

### Post by phillywize on 2006-07-04
[QUOTE=PryGuy]I bet you are wrong!;) nvidia-glx was included in 5.10, I was installing it from the  Ubuntu 5.10 CD![/QUOTE]

How much you wanna bet?  Sky's the limit...  Try [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=dapper&release=all&keywords=nvidia-glx&sourceid=mozilla-search").

Enable the right repo, and you're there.

---

### Post by PryGuy on 2006-07-04
Do you have your 5.10 CD? Check it out please!;)
EDIT: Just insert the Ubuntu 5.10 CD into your drive and check out the file:
/pool/restricted/l/linux-restricted-modules-2.6.12/nvidia-glx_1.0.7667-0ubuntu25_i386.deb

---

### Post by PryGuy on 2006-07-04
It worked! know what did i do? I have just manually replaced "nv" with "nvidia" in the driver section in xorg.conf and it worked!!!\\:D/

---

### Post by jvictor on 2006-07-04
Wt happened to the bet ? ;)

---

### Post by PryGuy on 2006-07-04
LOL
Well, you may check it out yourself. Just insert 5.10 into the drive and find the following file: /pool/restricted/l/linux-restricted-modules-2.6.12/nvidia-glx_1.0.7667-0ubuntu25_i386.deb
Well... I won... ;)

---

### Post by phillywize on 2006-07-04
[QUOTE=PryGuy]LOL
Well, you may check it out yourself. Just insert 5.10 into the drive and find the following file: /pool/restricted/l/linux-restricted-modules-2.6.12/nvidia-glx_1.0.7667-0ubuntu25_i386.deb
Well... I won... ;)[/QUOTE]
Hmmm...gloat away...we were, I think, talking about different things.

Are you running dapper?  Assuming you are, you'll still get a more recent version, and without weird dependency/config issues if you install the nvidia drivers from the right repo instead of from your breezy cd.

---

### Post by PryGuy on 2006-07-05
Noone tries to install the Breezy drivers on Dapper. The question was was the nVidia driver included in Breezy or not... 'Cause Jagot said that "it was never included with the distro" and it is not true.

---

