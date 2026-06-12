---
title: "How I installed R and RStudio in Linux Mint Maya (Ubuntu 12.04)"
date: 2013-03-19
forum: Education &amp; Science
---

### Post by rewyllys on 2013-03-19
The purpose of this note is to provide, in the Ubuntu Forums, a concise outline of how to install R and RStudio.

Feeling a need to refresh and update myself in the mathematical programming language R, I just purchased an excellent, relatively new book, *R for Dummies* by Andrie de Vries and Joris Meys (Chichester, UK: John Wiley & Sons, 2012).  Also, I decided to make a fresh installation of R and RStudio on my desktop.  On this machine I run Linux Mint Maya (which is based on Ubuntu 12.04).  The procedures I outline below should also work for Linux Mint Nadia and Ubuntu 12.10.  

**Installing R**
To begin, I installed R using the Synaptic Package Manager; depending on your system, this may involve searching in the SPM for "R", "r", or "r-base". Using the SPM is the simplest and easiest way I know of to get the basic components of R installed, using the version of R that is currently in the Ubuntu repositories.

Next, in order to use the latest updates to R, I added to the SPM a repository for such updates.  To do this, I opened the Terminal and entered the following:

```
sudo add-apt-repository "deb http://cran.stat.ucla.edu/bin/linux/ubuntu precise/"
```

I gratefully acknowledge that I obtained the above command, and some others herein, from the following URL:

[https://livesoncoffee.wordpress.com/2012/12/09/installing-r-on-ubuntu-12-04/](https://livesoncoffee.wordpress.com/2012/12/09/installing-r-on-ubuntu-12-04/)

I used the University of California, Los Angeles mirror of the CRAN project because, having spent several semesters there as a graduate math student, I know that they have an active Department of Statistics, and, hence, I believe that they can be trusted to keep their CRAN mirror up-to-date.  Also, this mirror is reasonably close to my location.  If you want to locate a mirror closer to you, you can go to the following URL:

[http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html)

If you have selected a mirror that you would prefer to use, you should enter its identifying data in the

```
"deb http://<your-preferred-mirror>/bin/linux/ubuntu precise/"
```

portion of the **sudo add-apt-repository** command shown above.  If you are using Ubuntu 12.10, you would, of course, enter "quantal" in place of "precise".  

 The LivesOnCoffee URL that I cited above recommends that for added security, you should "get the key and add it to your keyring (NOTE: the CRAN website says that some people are having issues with this step — if the commands here do not work for you, check there for latest information)".  To obtain and add the key, enter these commands in the Terminal:

```
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9 
gpg -a --export E084DAB9 | sudo apt-key add -
```

Next, to obtain and install the latest updates, enter these commands in the Terminal:

```
sudo apt-get update
sudo apt-get install r-base
```

The dependency checking that gdebi performs will ensure that the second line obtains the latest versions of the portions of R installed by the SPN.

**Adding RStudio**
In using R, I like to take advantage of the convenience of using the GUI provided by RStudio.  To add RStudio to  your R installation, go to

[http://www.rstudio.com/ide/download/](http://www.rstudio.com/ide/download/)

and click on either "Download RStudio Desktop" or "Download RStudio Server".  In the resulting page, choose the Debian version that corresponds to your machine (i.e., select the 32-bit or 64-bit version).  Download the chosen version to your machine.  Then, in the Terminal, use the "cd" command to move to the directory in which your downloads are saved, and issue this command:

```
sudo gdebi <name of downloaded rstudio file ending in .deb>
```

If everything has worked as expected, you will be able to find RStudio listed among the programs available to you.

---

### Post by rewyllys on 2013-04-12
I'm happy to report that, in line with the procedures I outlined in my previous post in this thread, I have just successfully installed R and RStudio in Linux Mint Nadia, which is based on Ubuntu 12.10.  The installation proceeded without a hitch.

---

### Post by theryangreen on 2014-02-05
I am happy to report that, in line with the procedures you outlined in your above post, I have just successfully installed R and RStudio in Linux Mint Petra.  I only changed precise to saucy in the mirror repository.

Thank you for taking the time to do this walk-through.  

Cheers!

---

### Post by belkinsa on 2014-02-05
Would this be worth it to create a Community Help Wiki page for this?

---

### Post by rewyllys on 2014-02-07
Excellent suggestion.  I'll look into it.

Thank you.

---

### Post by monkeybrain20122 on 2014-02-07
Just add this ppa for the latest versions [https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter) (the R-Cran packages are from his ppa and therefore older)
As for Rstudio, not sure why "sudo gedbi..." the whole point of gdebi is to install with one click. if you are going to use the terminal you don't need gdebi. :)

---

### Post by belkinsa on 2014-02-07
> **rewyllys said:**
> Excellent suggestion.  I'll look into it.

Thank you.

Er, I misread the title of the thread.  I think it would fit better in the Mint's wiki, if they have one.

---

### Post by eldafani on 2014-04-25
Thank you, it works in Maya. Can you share the instructions for Linux Petra? It does not work for me.
Daniel



> **rewyllys said:**
> The purpose of this note is to provide, in the Ubuntu Forums, a concise outline of how to install R and RStudio.

Feeling a need to refresh and update myself in the mathematical programming language R, I just purchased an excellent, relatively new book, *R for Dummies* by Andrie de Vries and Joris Meys (Chichester, UK: John Wiley & Sons, 2012).  Also, I decided to make a fresh installation of R and RStudio on my desktop.  On this machine I run Linux Mint Maya (which is based on Ubuntu 12.04).  The procedures I outline below should also work for Linux Mint Nadia and Ubuntu 12.10.  

**Installing R**
To begin, I installed R using the Synaptic Package Manager; depending on your system, this may involve searching in the SPM for "R", "r", or "r-base". Using the SPM is the simplest and easiest way I know of to get the basic components of R installed, using the version of R that is currently in the Ubuntu repositories.

Next, in order to use the latest updates to R, I added to the SPM a repository for such updates.  To do this, I opened the Terminal and entered the following:

```
sudo add-apt-repository "deb http://cran.stat.ucla.edu/bin/linux/ubuntu precise/"
```

I gratefully acknowledge that I obtained the above command, and some others herein, from the following URL:

[https://livesoncoffee.wordpress.com/2012/12/09/installing-r-on-ubuntu-12-04/](https://livesoncoffee.wordpress.com/2012/12/09/installing-r-on-ubuntu-12-04/)

I used the University of California, Los Angeles mirror of the CRAN project because, having spent several semesters there as a graduate math student, I know that they have an active Department of Statistics, and, hence, I believe that they can be trusted to keep their CRAN mirror up-to-date.  Also, this mirror is reasonably close to my location.  If you want to locate a mirror closer to you, you can go to the following URL:

[http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html)

If you have selected a mirror that you would prefer to use, you should enter its identifying data in the

```
"deb http://<your-preferred-mirror>/bin/linux/ubuntu precise/"
```

portion of the **sudo add-apt-repository** command shown above.  If you are using Ubuntu 12.10, you would, of course, enter "quantal" in place of "precise".  

 The LivesOnCoffee URL that I cited above recommends that for added security, you should "get the key and add it to your keyring (NOTE: the CRAN website says that some people are having issues with this step — if the commands here do not work for you, check there for latest information)".  To obtain and add the key, enter these commands in the Terminal:

```
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9 
gpg -a --export E084DAB9 | sudo apt-key add -
```

Next, to obtain and install the latest updates, enter these commands in the Terminal:

```
sudo apt-get update
sudo apt-get install r-base
```

The dependency checking that gdebi performs will ensure that the second line obtains the latest versions of the portions of R installed by the SPN.

**Adding RStudio**
In using R, I like to take advantage of the convenience of using the GUI provided by RStudio.  To add RStudio to  your R installation, go to

[http://www.rstudio.com/ide/download/](http://www.rstudio.com/ide/download/)

and click on either "Download RStudio Desktop" or "Download RStudio Server".  In the resulting page, choose the Debian version that corresponds to your machine (i.e., select the 32-bit or 64-bit version).  Download the chosen version to your machine.  Then, in the Terminal, use the "cd" command to move to the directory in which your downloads are saved, and issue this command:

```
sudo gdebi <name of downloaded rstudio file ending in .deb>
```

If everything has worked as expected, you will be able to find RStudio listed among the programs available to you.

---

