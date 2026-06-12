---
title: "How to discover new programs in the repos?"
date: 2009-04-27
forum: General Help
---

### Post by shaggy999 on 2009-04-27
Ok, so every time there's been a new release of Ubuntu there's always some new interesting packages to look at. From Feisty to Gutsy to Hardy to Intrepid my way of discovering packages was to launch aptitude or synaptic and simply browse all 20,000+ packages going from a to z.

You can imagine this can take awhile. Hours, in fact. Is there an easier way to see just what packages are new to ubuntu between releases?

---

### Post by loell on 2009-04-27
youeither have to stay at the edge by reading developer blogs, or find something interesting each day.

[http://debaday.debian.net/]("http://debaday.debian.net/")

---

### Post by shaggy999 on 2009-04-27
There's gotta be a better way. I should be able to somehow grab all the packagenames from intrepid and jaunty and do a diff on them.

---

### Post by loell on 2009-04-27
probably, like diffing two **/var/lib/dpkg/available** 

it still is very noisy, with all the libs, docs and whatnot.

---

### Post by shaggy999 on 2009-04-27
Ok, so I was able to diff the files and it worked out quite well! I did not use /var/lib/dpkg/available because I wanted to be able to somehow grab this data on a single machine or maybe even compare two distributions that I'm not even running. Well, actually I didn't use that because I didn't know about it, but anyway... :) So what I did was this:

1) grab the Packages.bz2 files from my repository of the main/restricted/universe/multiverse sections of each distribution on my architecture. So:

./dists/intrepid/main/binary-amd64/Packages.bz2
./dists/intrepid/restricted/binary-amd64/Packages.bz2
./dists/intrepid/universe/binary-amd64/Packages.bz2
./dists/intrepid/multiverse/binary-amd64/Packages.bz2

./dists/jaunty/main/binary-amd64/Packages.bz2
./dists/jaunty/restricted/binary-amd64/Packages.bz2
./dists/jaunty/universe/binary-amd64/Packages.bz2
./dists/jaunty/multiverse/binary-amd64/Packages.bz2

This should work as the -updates and -security repositories should only be adding new versions of existing packages and not whole new packages entirely. Any new packages are probably insignificant anyway.

2) Uncompress them.

3) ran 'cat Packages | egrep ^Package: | awk '{print $2}' | tee -a <distro> for each package file in a distribution.

4) ran cat <distro> | sort > <distro>_sorted

5) Used the program 'meld' to visually diff the files. This works pretty well! This should be easy to automate in a script so that you can do something like 'showchanges intrepid jaunty'.

---

