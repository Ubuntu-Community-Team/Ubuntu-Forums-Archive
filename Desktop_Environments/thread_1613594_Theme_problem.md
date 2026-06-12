---
title: "Theme problem"
date: 2010-11-04
forum: Desktop Environments
---

### Post by blur xc on 2010-11-04
I tried installing the ["A New Hope"]("http://www.webupd8.org/2010/11/divergence-iv-new-hope-updated-to-v077.html") theme and it didn't seem to go right.  All my buttons and tabs look like they came from windows 95.  See pics attached.

Thanks,
BM

---

### Post by qamelian on 2010-11-04
It looks like maybe you don't have the the needed version of the Murrine engine for the GTK theme. Can you open a terminal and enter:
```
apt-cache policy gtk2-engines-murrine
```

and report the results?

---

### Post by blur xc on 2010-11-04
I'd be happy to- 

 ```
apt-cache policy gtk2-engines-murrine 
gtk2-engines-murrine:
  Installed: 0.90.3+git20100323-0ubuntu3
  Candidate: 0.90.3+git20100323-0ubuntu3
  Version table:
 *** 0.90.3+git20100323-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
```

And apparently I don't have the 0.98 version that's required.  Any suggestions on how I do that?

Thanks for the quick response...
BM

---

### Post by qamelian on 2010-11-04
You can get the newest Murrine engine by adding the elementary-art PPA.

In Synaptic Package Manager, go to Settings > Repositories to open your software sources. Go to the Other Software tab and click the Add button at the bottom. Paste the following into the space provided:
```
ppa:elementaryart/ppa
```

Then just do an update and Murrine should upgrade to .98.

---

### Post by blur xc on 2010-11-04
Thanks!

All better - thread marked solved.

BM

---

