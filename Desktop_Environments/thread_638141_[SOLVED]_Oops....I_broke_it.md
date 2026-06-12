---
title: "[SOLVED] Oops....I broke it"
date: 2007-12-11
forum: Desktop Environments
---

### Post by t3hi3x on 2007-12-11
OK....so. I broke ubuntu. it was a dumb thing to do, but i want to fix to both learn and to not have to reconfigure the world.

i have a feisty server (with gnome) installed on a nice little p3. it's a web server, print server, you name it, it probably does it (dont test that).

i wanted to turn it into a video surveillance server just for fun <---theres the problem right there ;0--- and i was going to install a program called zoneminder. this is a deb file that is in the gutsy repositories but not fiesty. i did find a deb file for generic debian installations.

zonemidner requires libc6 v 2.6 or higher. fiesties repositories only include 2.5. so i found a deb file for libc6 v 2.74

now i would consider myself an intermediate linux user: i can program some c, install crap, troubleshoot most stuff, but i didnt know that libc6 was like the cornerstone of linux applications.....oh how was i mistaken

welp i installed 2.74 and it broke say 15 packages including g++ (i need that!) and some others. then i'm like crap. i cant install those packages and bla bla. 

so....i decided it would try to reverse my action and go back to 2.5 (i dont need this software that bad!!) and i cant. it says that the dependencies are missing. i cant upgrade to gutsy for "some unknown error calculating the upgrade" and if i try to uninstall libc6 v 2.74 then it will unistall EVERYTHING...of course everything relies on it.

is there a way i can revert to the old library without reinstalling linux? it wouldnt be the end of the world if i did, but i know everything can be fixed in linux ;)

ask away!!

thanks for reading my ramble, but it helps you know whats going on.

---

### Post by bingoUV on 2007-12-12
You are lucky the system is still usable i.e. basic stuff like X server, bash etc. did not break.
When you upgraded your libc to 2.74, did you "force" it using dpkg? Because if you did not, dpkg should not have let you upgrade libc as packages are dependent on libc 2.5. If you did not need to force, it is a bug in the packaging of the broken packages (e.g. g++) that they did not mention they cannot live with 2.74.

If you forced it, try downgrading to 2.5 instead of uninstalling 2.74 and then installing 2.5. dpkg has an option (I forgot what exactly) that allows older version to replace newer version.

If it does not work, see which files are in package libc 2.74. Extract replacement files from 2.5 and put them in appropriate places. I think adding the /lib, /usr/lib , and /sbin files should be enough to start with. /usr/lib and /sbin files will not have version in their file name so you will need to replace the files. After you are done replacing the files, run /sbin/ldconfig to make the change effective (hopefully).

---

### Post by t3hi3x on 2007-12-12
sounds great. i didnt necessarily force it. all it said was "there is aversion installed in apt, we recommend you install software from there" it's kinda weird. i will give the downgrading thing a try. i was not aware that was an option for dpkg.

---

### Post by t3hi3x on 2007-12-12
Great Success!! lol. i have successfully downgraded libc6. it is letting me install all my other programs that got broken during the upgrade.

Here is what I did:

i went into to synaptic and selected the libc6 package. i then clicked on Package --> Force Version

then i select the feisty version (2.5) and all my dependencies are fixed! w00t.

thanks and i hope this helps someone, i was not aware you could do such a think.

---

### Post by Lostincyberspace on 2007-12-13
Thank you for posting how you fixed it to many people get their problems fixed and don't put up the solutions.

---

### Post by t3hi3x on 2007-12-13
> **Lostincyberspace said:**
> Thank you for posting how you fixed it to many people get their problems fixed and don't put up the solutions.

i agree. whats the point of a forum if you dont post the solution?

---

