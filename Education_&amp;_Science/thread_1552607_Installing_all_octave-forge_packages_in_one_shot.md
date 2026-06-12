---
title: "Installing all octave-forge packages in one shot"
date: 2010-08-13
forum: Education &amp; Science
---

### Post by madiyaan on 2010-08-13
Is there a way I can install all octave-forge packages in a single command? I want to install all of them and don't want to create a dependency tree myself and install all of the manually after downloading all the tarballs from the internet.

I am willing to checkout the svn repo locally and do it from there if need be. I want to install all of them cleanly, and in the order where dependencies will be satisfied.

Has anyone done this before?

---

### Post by carandraug on 2010-08-29
Can't you use synaptic. Search for octave in the name and most of the ones that will appear are octave packages (at least that's what hapenns with aptitude search octave). Just select them all, and mark to install. I think that's the fastest way to install all of them in one go.

---

### Post by carandraug on 2010-10-29
Someone just posted this on the octave-forge mailing list. I believe that's what you were looking for:
[QUOTE="octave-dev@lists.sourceforge.net"]Hi,
I just had to install all of the octave-forge packages on an Ubuntu 10.04 system and it turned out that the packages are not available via aptitude. The command
```
sudo aptitude install $(aptitude search ?description\(octave-forge\) | awk '{print $2}')
```
finally did the job. Maybe someone could put this in the Debian installation guide for other users that might come across this problem.
Best,
Eli[/QUOTE]

---

### Post by bziurac on 2013-01-17
And if someone doesn't use aptitude he can use apt instead as well
```
# apt-get install $( apt-cache search octave-forge | awk '{printf $1; printf " "}' )
```

---

### Post by overdrank on 2013-01-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

