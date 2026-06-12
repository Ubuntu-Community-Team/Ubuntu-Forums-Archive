---
title: "Second Life 1.23 on Ubuntu 8.04"
date: 2009-08-30
forum: Gaming &amp; Leisure
---

### Post by antoniocatalano on 2009-08-30
Hello,

I had to upgrade Secondlife from version 1.21.6.99587 to 1.23.4.123908 on an Aspire 5102WLMi, Ubuntu 8.04.
Everything was ok, it was working properly and fluently but the music streaming wasn't playing. So I apt-getted "esounds" but it blocked my computer, so I have to disinstall it in recovery mode. Once everything went back to normality, I entered again Second Life, and this time music was working (!) but it turned to be veeery laggy, basically impossible to move around.
Any suggestion?
thanks!
A:

---

### Post by LenWynne on 2009-08-31
I am still pretty new to Ubuntu but as a SL user I have faced similar issues.  I had problems with sound in 7.1 and got it working by playing with the main SL file.  If you open up the secondlife file in your text editor you will see this close to the top

## - Avoids using the FMOD ESD audio driver.
#export LL_BAD_FMOD_ESD=x
## - Avoids using the FMOD OSS audio driver.
#export LL_BAD_FMOD_OSS=x
## - Avoids using the FMOD ALSA audio driver.
#export LL_BAD_FMOD_ALSA=x

Try commenting out the ##export LL_Badxxxxxxx lines one at a time and try SL with each one.


Also, if you have not already done so, there is an Ubuntu Users Group in SL - it is free to join and lots of good advice there.

---

