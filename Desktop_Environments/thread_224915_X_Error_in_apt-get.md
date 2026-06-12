---
title: "X Error in apt-get"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Bosonator on 2006-07-28
Hello,

I'm running Kubuntu Dapper 6.06.

I always obtain my programs using "apt-get" on the command line in a terminal (Konsole). Lately, I've been getting an error message when ever I run "sudo apt-get upgrade". Upgrading of my programs works just fine, but the following error gets displayed:

"X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device"

(The quotes are mine, just to separate terminal display from the rest of this posting). The previous error repeats about 4 times, then I get 

"Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 1.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 1."

If this is a clue, the errors seem to have begun occuring after I ran the "EasyUbuntu" script ([http://easyubuntu.freecontrib.org/get.html)](http://easyubuntu.freecontrib.org/get.html)).

Thanks if you can help. This is obviously not a debilitating problem... I just have a general dislike for error messages.

---

