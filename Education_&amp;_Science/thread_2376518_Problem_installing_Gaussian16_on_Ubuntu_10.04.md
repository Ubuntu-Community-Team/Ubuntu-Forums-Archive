---
title: "Problem installing Gaussian16 on Ubuntu 10.04"
date: 2017-11-03
forum: Education &amp; Science
---

### Post by flutz on 2017-11-03
Hello,

i tried to upgrade our server with Gaussian09. From my predecessor, i received a tutorial to install Gaussian09 which caused some minor problems which are described and solved in this older thread: [https://ubuntuforums.org/showthread.php?t=1551193](https://ubuntuforums.org/showthread.php?t=1551193)

I did all the steps described in the older thread, yet when i try to compile the program by running    /bsd/bldg16 >&make.log             the task runs for about 30 seconds and then "finishes". The make.log file looks good for the first ~1000 lines, but then it starts posting "./gau-machine: Command not found." and "./gau-hname: Command not found" over and over again, although these files are definitely present in BOTH the ./g16 and the ./g16/bsd folder. I can also run both files manually, giving out "amd64" correctly. Can anybody help me with this problem? It's getting really frustrating =(

---

### Post by Kirboosy on 2017-11-03
Hi flutz! Welcome to the forums!

I would love to try and help out with this, but unfortunately its very difficult to get the source code to attempt installation myself. 

I did manage to find these two links that might point you in the right directions.

[http://gaussian.com/g16/g16src_install.pdf](http://gaussian.com/g16/g16src_install.pdf)

[https://ubuntuforums.org/showthread.php?t=2360113](https://ubuntuforums.org/showthread.php?t=2360113)

If I had to take a guess at what the issue could be I would suggest skipping step 4 of the forum post you linked and try again. That guide was written for version 09 and you are using 16 it might not be needed anymore. The scripts might work as is without any additional tweaking.

---

### Post by Topsiho on 2017-11-08
Hello,

I'm not able to help here, I'm afraid, but note that Ubuntu 10.04 is very old and deprecated by now.
So you first have to replace it with a newer version. If you want LTS you should install Ubuntu 16.04.3, or wait a few months until Ubuntu 18.04 becomes available. LTS versions get 5 years support and are more stable.
(intermediate versions such as 17.10 are only supported for a very short time, and being experimental they are less stable, but more state of the art :) )

That's all I can say here ...

Topsiho

---

