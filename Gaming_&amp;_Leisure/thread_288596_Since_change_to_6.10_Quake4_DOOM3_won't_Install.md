---
title: "Since change to 6.10 Quake4 DOOM3 won't Install"
date: 2006-10-30
forum: Gaming &amp; Leisure
---

### Post by LateNighter on 2006-10-30
When I was running Dapper 6.06.1 Quake4 as well as DOOM3 would install and run fine.

 But since I installed and configured Edgy 6.10 they won't install.
 They will initialize but STOP with the following ERROR Messages:

 root@manicmess:~# '/home/bipolarpenguin/Desktop/quake4-linux-1.3-2.x86.run'
Verifying archive integrity... All good.
Uncompressing Quake 4 (TM)....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
./setup.sh: 268: /root/.setup5542: not found
./setup.sh: 279: /root/.setup5542: not found
The setup program seems to have failed on x86_64/glibc-2.0

Fatal error, no tech support email configured in this setup
root@manicmess:~#


Fatal error, no tech support email configured in this setup
root@manicmess:~# '/home/bipolarpenguin/Desktop/doom3-linux-1.3.1302.x86.run'
Verifying archive integrity... All good.
Uncompressing DOOM III............................................................................................
./setup.sh: 279: /root/.setup5630: not found
./setup.sh: 290: /root/.setup5630: not found
root@manicmess:~#

 Does anyone have any idea whatsoever as to whats going on.

 I've ran it in any Terminal Konsole I can/could.

 Am I missing something in my Setup/Install?

 I use to run KDE on top of Gnome, Could that have allowed it to work?

 I'd install in KDE, but run them in Gnome because they wouldn't run in KDE, But they would run in Gnome?:rolleyes: :confused:  

 I've had sound issues cause this sometimes.
 Could this be a possibility?

 My Graphics Card has be reconfigured with the regular nvidia modules.

 Any and all ideas I'd be VERY Grateful...
 Thanks in advance.:KS

---

### Post by scheuri on 2006-10-30
> **LateNighter said:**
> [...]
The setup program seems to have failed on x86_64/glibc-2.0
[...]
This error message is pretty obvious, still I can not assure you its the real deal.
I am not on 64bit-systems (as I still think it needs some time for the software to really deal with it), but I woul suggest you do the following:

sudo aptitude update
aptitude search glibc

There should be results comming back with packages having glibc in their names. You then should install what is closest to glibc-2.0 (or mabe even newer like glibc-2.2 or whatever).

You can use paket-manager like synaptic or adept as well, of course.

And then try to run the installer again.

good luck
stefan

---

### Post by LateNighter on 2006-10-30
> **scheuri said:**
> This error message is pretty obvious, still I can not assure you its the real deal.
I am not on 64bit-systems (as I still think it needs some time for the software to really deal with it), but I woul suggest you do the following:

sudo aptitude update
aptitude search glibc

There should be results comming back with packages having glibc in their names. You then should install what is closest to glibc-2.0 (or mabe even newer like glibc-2.2 or whatever).

You can use paket-manager like synaptic or adept as well, of course.

And then try to run the installer again.

good luck
stefan

 Thanks I'll give it a shot and let you know...

---

### Post by tommcd on 2006-10-30
Well, I have been wondering about this myself, so I just had to try it! I am on 32 bit Edgy, and Doom3 installed just fine. First I ran the sh installer, then I copied all the *.pk4 files to /usr/local/games/doom3/base/ and it installed just fine.

---

### Post by LateNighter on 2006-10-31
> **tommcd said:**
> Well, I have been wondering about this myself, so I just had to try it! I am on 32 bit Edgy, and Doom3 installed just fine. First I ran the sh installer, then I copied all the *.pk4 files to /usr/local/games/doom3/base/ and it installed just fine.

 Thats GREAT I could have told you that it would work on that setup.
 I use to run one myself. And they run just fine.

 I'm running a AMD Athlon 64bit X2 Dual Core 3800+ Socket AM2 setup.
 And both the Dapper as well as the Edgy installs are of the 64bit Versions. 

 In Dapper it ran just fine with Quake4 and DOOM3 but, since I upgraded to Edgy, it's Crapped out on me.

 The only difference I know of is that the Kernels are different.
 I was using the K8 Kernels, instead of the Newer Generic kind.

 Which are to be better then the K8's.
 But I was thinking of installing the K8 Kernels to see if that might be it.
 It's worth a shot, and having two kernels on board NEVER Hurts anything, because if One Craps Out onn you, then you've always got the other one to boot into, Giving you the chance to fix it maybe avoiding a reinstall.

 Thanks for the reply. I'm most Grateful....8)

---

### Post by LateNighter on 2006-10-31
> **LateNighter said:**
> Thanks I'll give it a shot and let you know...

 Well Thanks anyway I tried it, and it Didn't Work....:mad: 

 But sooner or Later I'll figure it out.](*,)

---

### Post by LateNighter on 2006-11-01
The K8 Kernel Idea didn't work either.

 I use to have the KDE Desktop installed, Thought maybe a file there might have been what Helped to get them too run.

 Installed KDE that didn't work either.

 I know one thing this is Driving me Mad!!!

 OH Well back to the OLD Drawing Board... "WISH ME LUCK"

---

### Post by dmn_clown on 2006-11-01
You are missing the 32-bit libs that the games require.

---

### Post by LateNighter on 2006-11-01
> **dmn_clown said:**
> You are missing the 32-bit libs that the games require.
 I know I just found that out not Long ago, from another Thread.
 Dreadmo was the one who gave exactly the List of 32-bit libs needed.

 In any event I got them installed and Both are running GREAT.

 I'm going to attach dreadmo's list here so who ever is looking for a Solution to the same problem, Hopefully won't have to look no Further.

 Note: for this to work You "MUST" be running the Nvidia glx Modules and not beryl, At least thats the way it is at the moment.
 But it's worth it to do without a little bit of eye candy, to be able too FRAG some Strogg and Demons...

 ENJOY and FRAG On....;)

---

