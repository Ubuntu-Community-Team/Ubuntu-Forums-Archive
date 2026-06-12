---
title: "Digikam Help"
date: 2005-09-07
forum: Desktop Environments
---

### Post by jbinc1 on 2005-09-07
I am trying to add kipi-plugins so I can make slideshows in digikam. I added the repositories ([http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php](http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php)) to my sources.list file and the packages show up in synaptic. But when I try to install it gives me an error message that the software cannot be authenticated. Could someone give me a clue? I am terribly new at this. Thanks in advance.

---

### Post by ralphdewitt on 2005-09-07
This is a common problem with some of the repositories. Most people simply ignore the problem trusting the repositorie to be good. Most simply hit Y and continue to install the software. Hope this helps some.

---

### Post by jbinc1 on 2005-09-07
Thanks for the suggestion. There is no option in synaptic to tell it to go ahead and install. According to the digiKam website, those are the latest repositories. I guess I could compile it from source. That would be a whole new problem  :-P . I noticed when I was looking at the installed version/latest version in the synaptic pakages list that the latest version is not current. I checked the repository and it shows 0.7.4-0 as the latest. But syanptic and apt-get both show 0.7.3. Could I have conflicting repositories or something? I'm lost. ](*,)

---

### Post by sargo on 2005-09-08
If you can't install those packages with synaptic, download them and install with

sudo dpkg -i packagename.

Sorry for my English...

---

### Post by jbinc1 on 2005-09-08
Thanks. I'll give it a try.

---

