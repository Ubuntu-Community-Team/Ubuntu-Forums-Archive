---
title: "How I installed &quot;ggmap&quot; in R"
date: 2015-05-01
forum: Education &amp; Science
---

### Post by rewyllys on 2015-05-01
The purpose of this post is to record the steps I took in order to install the package "ggmap" in R, v. 3.1.3, running in Linux Mint 17.1 (which is based on Ubuntu 14.04), since my initial attempts to install this package ended in repeated failures.

As an initial step, I followed a recommendation in a Webpage entitled "UBUNTU PACKAGES FOR R", at [cran.r-project.org/bin/linux/ubuntu/README]("http://cran.r-project.org/bin/linux/ubuntu/README").  The recommendation was to use the Synaptic Package Manager to install "r-base-dev" if one needs to use the R command "install.packages()".

The major step I took was to go to the CRAN Webpage for "ggmap": [cran.r-project.org/web/packages/ggmap/index.html]("http://cran.r-project.org/web/packages/ggmap/index.html"). There one finds that ggmap: (1) depends on R (>= 2.14.0) and ggplot2 (>= 0.9.2); (2) imports the following packages: proto, scales, RgoogleMaps, png, plyr, reshape2, grid, rjson, mapproj, jpeg, geosphere, digest; and (3) suggests MASS and stringr.  The ggmap Webpage provides URLs for all of the aforementioned packages except "grid".  

To obtain grid, I used the SPM's Quick Filter to search on "grid" for packages that appeared plausibly linked with maps in R; I found two such packages, r-cran-gmaps and r-cran-misc3d, and used the SPM to install them.

I had already successfully installed ggplot2.  So, starting with "proto", I downloaded the tar.gz files for all the aforementioned packages (except grid) to my ~/Downloads folder.   Then I opened a terminal session and issued "gksudo nemo" to open a copy of nemo (which is LM's equivalent of Ubuntu's nautilus) with root powers.  Using nemo, I moved the tar.gz files from ~/Downloads to the usr/lib/R/site-library folder.  Still in nemo with root powers, I right-clicked on each of the tar.gz files and used the Archive Manager to extract its contents into the usr/lib/R/site-library folder.

I closed nemo and, in a terminal session, issued "sudo updatedb".  When updatedb finished, I used "sudo locate" to verify that the packages I had just installed were known to LM.

Next, I did a shutdown and restart of LM 17.1, following which I opened RStudio and issued "install.packages("ggmap", dependencies=TRUE).  This time, finally, I succeeded in installing ggmap in R.

---

### Post by monkeybrain20122 on 2015-05-05
??? Sounds very complicated. :) I just did install.packages('ggmap') in R, chose a mirror and it was done. It automatically fetched all the other packages needed for dependency. Took less than one minute.

I installed only R-base-core from [https://launchpad.net/~marutter/+archive/ubuntu/rrutter](https://launchpad.net/~marutter/+archive/ubuntu/rrutter) all additional packages are installed and updated from within R using install.packages() and update.packages().  I am currently on R 3.20.

---

### Post by rewyllys on 2015-05-05
It was more tedious than complicated.  

I wish I could understand why I have little or no trouble installing most packages, but occasionally have a lot of problems installing something.  In the last 6 weeks or so, caret and ggmap have been serious (or at least tedious) problems for me.

I'm hoping that the process of installing R packages on a given computer system approaches asymptotically a condition in which practically all the dependencies of the vast majority of packages will have already been installed on my system.

---

### Post by monkeybrain20122 on 2015-05-05
> **rewyllys said:**
> It was more tedious than complicated.  

I wish I could understand why I have little or no trouble installing most packages, but occasionally have a lot of problems installing something.  In the last 6 weeks or so, caret and ggmap have been serious (or at least tedious) problems for me.

I'm hoping that the process of installing R packages on a given computer system approaches asymptotically a condition in which practically all the dependencies of the vast majority of packages will have already been installed on my system.

I never have problem installing from cran. Like I said I only installed some bare bone packages from the repo (or ppa in my case) and do the rest within R. Just checked out 15.04, again installed a whole bunch of stuffs from cran without a hitch.

---

