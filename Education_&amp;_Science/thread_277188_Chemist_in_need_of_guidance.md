---
title: "Chemist in need of guidance"
date: 2006-10-14
forum: Education &amp; Science
---

### Post by hyby on 2006-10-14
Howdy,
I am currently writing my thesis and thought i might mix and match with different oses while writing it. I was wondering can somebody recommend Cambridgesoft's ChemDraw replacement. I would like something that porvide analysis data of molec. weights and predict proton and carbon shifts. 

I have tried to instal xdrawchem...however i can not instal libbabel0 with ubuntu's package. It will not give me the error, i have install gcc, libbabel02ca and the other required except this libabel0 package. How did many of you do it if you had the same problem?

---

### Post by [woodstock] on 2006-10-15
Hi!
As for sketching chemical structures I can recommend gchempaint or bkchem. (I am currently working on a deb package for bkchem. If you are interested, please send me an email. There is a slightly older package from Daniel Leidert for debian, too.)

I am sorry that I can't commit something useful concering your problem with xdrawchem. I took a look at this program a while ago and but it didn't fit my needs then.

Software for predicting H-shits and C-shifts is hard to find for linux, I know none of it, except that xdrawchem should be able to do this.

To spare you from switching from/to different OS you could try to run your software in wine. I have read that Chemsketch will do so in one of the newer wine releases. IIRC the commercial version of Chemsketch supports H- and C-shift prediction.

In case you don't already know this useful link:
[Linux4chemistry]("http:///www.redbrick.dcu.ie/~noel/linux4chemistry/")

---

### Post by LaserJock on 2006-10-15
xdrawchem should install fine. I think something weird must be going on with your installation. I installed it fine on my dapper machine. libabel0 is an older version (maybe Breezy even) of the babel library.

I've heard great things about BKChem (I almost got it into edgy but just didn't have time).

-LaserJock

---

### Post by hyby on 2006-10-16
Thanks guys, i have managed to squeeze libabel0 into dapper and managed to get Xdrawchem working. However, one thing i miss from chemdraw is the clean up function. Is there one? Thanks guys for the reply.

---

### Post by paulb75 on 2008-02-12
You can also run ChemDraw under Wine (or even Cedega!). I convert the drawings to EPS before I put them in OpenOffice documents. ^_^. No room for Windows in my life!!!

---

### Post by Tharmas on 2008-02-12
To resolve your XDrawChem problem, you could try to install openbabel first (from synaptic).

To handle your drawings, I recently started to use [Marvin Sketch]("http://www.chemaxon.com/product/msketch.html") and love it (despite being java and having to be installed manualy)

---

