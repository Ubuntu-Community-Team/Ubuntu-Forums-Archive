---
title: "Installing libglade for R Rattle package"
date: 2009-10-29
forum: Education &amp; Science
---

### Post by myotis on 2009-10-29
I  am trying to run the rattle package in R 

I have installed libglade2-dev through synaptic as required by the install instructions, but trying to run R gives an error

> rattle()
Error in rattle() : 
  The RGtk2 package did not find libglade installed. Please install it.

Can anyone suggest a solution.

Many thanks,

Ubuntu 9.04

Graham

---

### Post by gunksta on 2009-10-30
I've never installed or used rattle, so these are nothing more than educated guesses.

I assume you have downloaded and successfully installed rattle with install.packages(). If the installation process was not successful, any errors from that would be useful.

Assuming that the installation was successful, it seems fair to ask, do you have libglade installed on your system? If you are running kubuntu it is possible that you've never installed libglade.

```
sudo apt-get install libglade2-0
```

If you are running Ubuntu or have several GTK based applications on your computer, you do probably have libglade installed, but I figured it was worth looking at.

---

### Post by myotis on 2009-10-30
Thanks, I did check that libglade was installed and in fact re-installed it.

On advice from elsewhere, I am now in the process of updating to the latest version of R, rather than using the version in the Ubuntu repository.

Graham

---

### Post by gunksta on 2009-10-30
It is my understanding that using the R repository is often a better source for packages because the R-Project's update schedule is just not in sync with Ubuntu's.

---

### Post by myotis on 2009-10-31
> **gunksta said:**
> It is my understanding that using the R repository is often a better source for packages because the R-Project's update schedule is just not in sync with Ubuntu's.

Yes, so it seems, Rattle is now installed and luanches.

Thanks,

Graham

---

