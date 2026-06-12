---
title: "updating R"
date: 2008-11-05
forum: Education &amp; Science
---

### Post by bryncoles on 2008-11-05
i booted R with the command

```
 sudo R
```

and then tried to update the packages from R-crans mirror at 

```
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu intrepid/

```

and ran the command

```
update.packages(,dep=T)
```

most of the packages updated fine, but a few returned

> The downloaded packages are in
	/tmp/RtmpN0O9Dc/downloaded_packages
Warning messages:
1: In install.packages(update[instlib == l, "Package"], l, contriburl = contriburl,  :
  installation of package 'party' had non-zero exit status
2: In install.packages(update[instlib == l, "Package"], l, contriburl = contriburl,  :
  installation of package 'rgl' had non-zero exit status

any ideas what i need to do?

---

### Post by bryncoles on 2008-11-09
bump!

---

### Post by akniss on 2008-11-09
I guess my first question is: why do you need to update the packages?  Is there a specific feature you need that is not currently in one of the packages?  I've learned with R that for 99.9% of the functions I use, there are rarely any changes to the base package or any of the addons from release to release.  Consequently, I've been pretty happy to keep whatever version is easily installed with Synaptic or apt-get without having to change sources or repositories.

That said, have you changed repositories for CRAN in your sources.list?  If so, that may change the advice you may receive in trying to solve your problem.

---

### Post by bryncoles on 2008-11-10
ive got the repo's for cran set to intrepid, which is what im using. as for needing to keep R up to date, im attempting to use it for a science based PhD, with a mind towards utilising it in future career options. so a probably dont need it up to date as a top priority, but i can anticipate needing to know how to update it in the future...

so if you can help me figure out whats the issue, id be very grateful! and as an added bonus, it'd enhance my 'buntu knowledge!

---

### Post by akniss on 2008-11-10
> **bryncoles said:**
> ive got the repo's for cran set to intrepid, which is what im using. as for needing to keep R up to date, im attempting to use it for a science based PhD, with a mind towards utilising it in future career options. so a probably dont need it up to date as a top priority, but i can anticipate needing to know how to update it in the future...

so if you can help me figure out whats the issue, id be very grateful! and as an added bonus, it'd enhance my 'buntu knowledge!

I've had similar issues in the past when installing packages that are not on CRAN, with the non-zero exit status. You might try specifically installing the offending packages... for some reason I've been able to install a package by itself even though installing it as a dependency to something else did not work... in your case try:
```
sudo R
install.packages('party',dep=T)
install.packages('rgl', dep=T)
```
Maybe it will be able to install correctly that way.  If it doesn't work, try changing the CRAN repo and try again.  Sometimes a specific package may not get copied over to all the mirrors correctly.

Problems like this are the reason I just use the default r-cran packages in the Ubuntu repos.  I've run into problems on several occasions in the past trying to utilize the external CRAN mirrors.  There was a time when a package I used ('drc') required a more up to date version of R than was packaged with Ubuntu, and I had a great many troubles getting all my dependencies to work.  However, for about the last 2 years, I've not had any issues using the r-cran packages in the default Ubutnu repos.

---

### Post by gunksta on 2008-11-12
I don't know which packages you need, but all of the R packages I have needed (Hmisc, for example) are available via the Ubuntu repositories. I prefer to just use the Ubuntu repositories because when I upgrade Ubuntu, I know that R gets updated as well. Since Ubuntu updates every six months, my R installation doesn't get too old. I keep an eye on the R newsletter and if I see something specific that is new or fixed that I really want or need, I would be tempted to keep my R packages up to date by hand, but I think it's easier to just let the OS do the work.

---

### Post by bryncoles on 2008-11-12
you make a good point gunksta, but as long as you enable the r-repos then it updates along with the OS anyway (it seems). and it doesnt seem to break upgrading from one version of the OS to another (at least, i got no problems form hardy to ibex). 

now, aknis, i tried your manual update of packages and got the same errors - non-zero exit status. never mind, is there something else we can try?

---

