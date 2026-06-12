---
title: "Compiz Fusion, ATI driver and Gutsy"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by DrQuincy on 2007-08-03
Am I right in saying that with Gutsy the newer ATI driver will be supported by default and Compiz Fusion will be available through the package manager?

---

### Post by UbuWu on 2007-08-03
Compiz Fusion will even be installed by default.

---

### Post by ozymo on 2007-08-11
I thought I might bump this one, just for fun  ;)

So, I have a Gateway Msomething or another...  with an ATI Radeon XPRESS M200 PCIe card built in.

I keep getting this error when trying to enable desktop effects:

nvidia hardware not available

I have enabled the restricted fglrx drivers, and have added a few thing (dri, vbe) to my xorg.conf, but still no go.  I try to force it, by issuing compiz.real --replace, and it complains that there is no composite.  OK.

I tried the old hat method of using XGL, but then I couldn't even get a desktop...  Funny thing.  I even went so far as to search through the forums for an hour or so before posting...  No luck.

So, all in all, what's up?  Is Ubuntu abandoning us ATI users here?

I have to say, though...  everything else works great! (except wireless and sound, but eh...)

Any info would be greatly appreciated!

/cs

---

### Post by n00bWillingToLearn on 2007-08-15
> **ozymo said:**
> I thought I might bump this one, just for fun  ;)

So, I have a Gateway Msomething or another...  with an ATI Radeon XPRESS M200 PCIe card built in.

I keep getting this error when trying to enable desktop effects:

nvidia hardware not available

I have enabled the restricted fglrx drivers, and have added a few thing (dri, vbe) to my xorg.conf, but still no go.  I try to force it, by issuing compiz.real --replace, and it complains that there is no composite.  OK.

I tried the old hat method of using XGL, but then I couldn't even get a desktop...  Funny thing.  I even went so far as to search through the forums for an hour or so before posting...  No luck.

So, all in all, what's up?  Is Ubuntu abandoning us ATI users here?

I have to say, though...  everything else works great! (except wireless and sound, but eh...)

Any info would be greatly appreciated!

/cs

I think it is more a matter of ATI abandoning Linux users, their driver ( fglrx ) *still* doesn't support the needed extensions for Compiz to run without XGL, and XGL is a hack ( IMHO ) and therefore cannot be officially supported, especially not by default. So until ATI fixes their drivers there isn't much of anything that the Ubuntu developers can do. As an ATI user that needs fglrx for 3D acceleration, I feel your pain :(

---

### Post by macaholic on 2007-08-15
I got compiz fusion to work with xgl, although the screen sometimes garbles on login that is usually resolved with a ctrl+alt+backspace (restart xserver). But I feel your pain as installing compiz correctly with xgl is WAY too difficult to do and shouldn't be neccesary.

---

### Post by maxrisc on 2007-08-16
I had this working with FGLRX and Xgl/ Compiz-Fusion a couple of days ago.  So I decided I would be cute and install ATI Binary 8.40.4 and now it's all busted.  So much for that.  I am rolling back to the 8.37.x drivers in the repo and just waiting.

ATI = All Text Interface

nVidia = Envy :0)

BTW You can get your Direct 3D accelerated apps to run with a hack to start the application on a separate xserver.  You will need to search "nonXgl" to learn how to do this.  The only change I had to make was display :0.   

I can play Urban Terror so so on a Mobility 9600 64MB.

HTH

---

