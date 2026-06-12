---
title: "Building Stepmania 4 in Oneiric? (ffmpeg related issue)"
date: 2012-03-16
forum: Gaming &amp; Leisure
---

### Post by Known unknownZ on 2012-03-16
Hey all. Trying to build SM4 in 11.10 via the instructions given [here]("http://www.stepmania.com/wiki/Build_the_StepMania_Source_in_Linux") but I've hit somewhat of a snag.

I installed the libraries and got the source just fine, but when I cd into my Stepmania folder to compile it  by running

```
./autogen.sh 
```and

```

./Utils/build.sh 
```.

Everything goes swimmingly until I put in the latter, which ends up going something like this

```
ism@ism-iMac:~/Stepmania/stepmania$ ./Utils/build.sh
Configuring ffmpeg...okay.
Building ffmpeg...failed.
Consider passing --verbose to ./Utils/build.sh. Pass --help for details.
ism@ism-iMac:~/Stepmania/stepmania$ 

```is there something (probably obvious) that I'm missing here? Or should I try installing ffmpeg by some other means?

Also, hoping I posted this in the right subforum... seemed like the best place to put this but I wasn't too sure :lolflag:

---

### Post by Known unknownZ on 2012-03-20
bump

---

### Post by FakeOutdoorsman on 2012-03-20
> **Known unknownZ said:**
> ```
Consider passing --verbose to ./Utils/build.sh. Pass --help for details.
```

Did you try adding *--verbose* as suggested by this output? It might give more output to help narrow down the issue.

---

### Post by topet2k12001 on 2012-06-11
> **Known unknownZ said:**
> Hey all. Trying to build SM4 in 11.10 via the instructions given [here]("http://www.stepmania.com/wiki/Build_the_StepMania_Source_in_Linux") but I've hit somewhat of a snag.

```
ism@ism-iMac:~/Stepmania/stepmania$
```

is there something (probably obvious) that I'm missing here?

Looking at your "command prompt", it gives me the impression that you went inside the subfolder of sm-scc and then you ran the command/script from there. The instructions didn't say anything about going into a sub-folder before executing the command/script, that's why the Terminal is saying that he can't find it (can't find the script/command). I have installed Stepmania (build from source method) before. I could be wrong though. :)

---

