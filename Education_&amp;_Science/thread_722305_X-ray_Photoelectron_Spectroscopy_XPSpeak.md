---
title: "X-ray Photoelectron Spectroscopy: XPSpeak"
date: 2008-03-12
forum: Education &amp; Science
---

### Post by Lateralis on 2008-03-12
Hello all.

This is a bit of a long shot, but what the hell.  

I'm a condensed matter research physicist and use x-ray photoelectron spectroscopy (XPS) a fair amount.  There's a programme for Windows called XPSpeak which allows me to fit semi-Voigt functions (convolved Gaussian-Lorentzian lineshapes) to experimental spectra, as well as doing background subtractions.  I've yet to find anything similar in Linux, and am hoping that someone on here might know of something I could use?  (XPSpeak is the only Windows programme that I *need* to use... getting an open source programme to do these bits would mean I can do everything in Ubuntu... hurray!)

The other problem I have with XPS data is I'm going to be using some theoretical calculations (some of my own, some in collaboration with Cambridge university) of the valence band electron density-of-states to compare with experimental XPS data.  In order to do this I will need to convolve the calculated data with Gaussians and Lorentzians.  Does anyone have any suggestions how to do that?  I was thinking about writing something in Scilab, but if anyone has any programme that can do that for me, I'd be hugely appreciative.  :)

---

### Post by slaanco on 2008-03-13
well i dont know that program of urs :(, but i think its should be feasible to use it with wine.

Installation of wine is straightforward:
sudo apr-get install wine

and then just:

wine [B]XPSpeak.exe

[/B]to the second problem have u tried program called *fityk*?

---

### Post by Lateralis on 2008-03-13
I did try using Wine, without any success.  To be honest though, I'm still quite new when it comes to Linux and Wine does confuse me a little.  I have been able to open up Winamp using Wine, but Winamp does nothing other than sit there looking pretty.  If Winamp is supposed to work in Wine then it surely means I'm doing something wrong and should have a look at it again more closely.  

As for fityk, I'll give it a shot.  If it works, it will surely beat having to write my own Scilab/Matlab code!

---

### Post by slaanco on 2008-03-14
well according to wine app db winamp shsould work more or less quite well, so i think there might be something wrong with ur installation or settings of wine.

try to reinstall.

btw does XPSpeak use some special libraries?

---

### Post by Lateralis on 2008-03-14
Yeah I think XPSpeak does use some special libraries that are not normally found in Windows.

I just tried Wine through the command line.  I get the following:

```
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\XPSPEAK41.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\XPSPEAK41.exe" failed, status c0000135
```


Just uninstalled and reinstalled through the command line but I get the same error. =(

---

### Post by mips on 2008-03-14
[http://www.uksaf.org/software.html](http://www.uksaf.org/software.html)
[http://www.nist.gov/srd/nist100.htm](http://www.nist.gov/srd/nist100.htm)
[http://www.spectroscopynow.com/coi/cda/list.cda?catId=1665&type=Product&sort=az&chId=0](http://www.spectroscopynow.com/coi/cda/list.cda?catId=1665&type=Product&sort=az&chId=0)
[http://webscripts.softpedia.com/script/Scientific-Engineering-Ruby/Statistics-and-Probability/Multivariate-analysis-and-preprocessing-spectral-35595.html](http://webscripts.softpedia.com/script/Scientific-Engineering-Ruby/Statistics-and-Probability/Multivariate-analysis-and-preprocessing-spectral-35595.html)
[http://www.mf.mpg.de/en/abteilungen/dosch/software/software_en.shtml](http://www.mf.mpg.de/en/abteilungen/dosch/software/software_en.shtml)
[http://www.boutell.com/lsm/lsmsubject.html](http://www.boutell.com/lsm/lsmsubject.html)
[http://ces.iisc.ernet.in/hpg/envis/mapdoc1712.html](http://ces.iisc.ernet.in/hpg/envis/mapdoc1712.html)
[http://www.programs4all.net/software/spect.htm](http://www.programs4all.net/software/spect.htm)

There might be something of use to you in the above links.

---

### Post by WW on 2008-03-14
It looks like you can get MSVBVM60.DLL from Microsoft [here](http://support.microsoft.com/kb/823746).

---

### Post by Lateralis on 2008-03-20
Thanks for the replies people.  Sorry it's taken a while to get back to you - was in Amsterdam between Sunday and yesterday, then at work again today.  

Some of those links looks promising, and I'll see about getting the DLL, but that in itself seems rather kookie - XPSpeak works fine in Windows without any issues.  Why is Linux having issues finding DLLs?  

Anyway, thanks again for the replies.  Much appreciated as always. :)

---

### Post by mips on 2008-03-20
> **Lateralis said:**
> Why is Linux having issues finding DLLs?  


DLLs are not native to linux at all, it is something native to MS Windows.

And if you ask me it is probaly illegal to copy them anyway for use in Wine unless you don't have them originally lincensed via a purchase.

---

### Post by PeterP24 on 2008-03-22
If it doesn't work with wine you should try with Vmware server. You can install windows xp in your virtual machine and then use your program. 

Peter

---

### Post by Tharmas on 2008-04-30
There is an excellent peak fitting program in the repositories: **[fityk]("http://www.unipress.waw.pl/fityk/")**
I used it to deconvolute infrared spectra.

And qtiplot (a plotting program similar to origin) also has a peak fitting facility.

---

### Post by Lateralis on 2008-05-01
Thanks for your reply, Tharmas!  

Just had a look at fityk and it does have an option to fit pseudo-Voigt functions to XPS data.  Not yet played around with it as I'm off to teach presently, but this looks very promising indeed.  Not sure if it will give me the freedom to manually fit peaks that XPSpeak gives me.  If it doesn't, I'll try going down the VM route.  

Thanks again.

---

### Post by LittleAngel on 2008-05-08
I'm also a user of XPSpeak,
and I have to stick with this program coz my collegues share the fitted data with XPSpeak.

Just found out that XPSpeak is a freeware,
Guys good at programming could request the source code:
> 
General Information (from R. Kwok)
This version of the program was written in Visual Basic 6.0 and uses 32 bit processes. This is freeware. You may ask for the source program if you really want to. I hope this program will be useful for people without modern XPS software. I also hope that the new features in this program can be adopted by the XPS manufacturers in the later versions of their software. 
If you have any questions/suggestions, please send an email to me.
	Raymund W.M. Kwok
	Department of Chemistry
	The Chinese University of Hong Kong
	Shatin, Hong Kong
	Tel: (852)-2609-6261
	Fax:(852)-2603-5057
	email: [email]rmkwok@cuhk.edu.hk[/email]

I would like to thank the comments and suggestions from many people. For the completion of Version 4.0, I would like to think Dr. Bernard J. Flinn for the routine of reading Leybold ascii format, Prof. Igor Bello and Kelvin Dickinson for providing me the VAMAS files VG systems, and my graduate students for testing the program. I hope I will add other features into the program in the near future.

R Kwok.


However it's written in VB...so may be difficult to port to Linux?

---

### Post by juggies on 2008-09-17
I know the Collaborative Computational Project CCP had one on xps peak fitting and one of them was for linux... here is the link

[http://www.ccp5.ac.uk/](http://www.ccp5.ac.uk/)

You might want to check with all the CCP projects there are like 12 or 13 of them :)


> **Lateralis said:**
> Hello all.

This is a bit of a long shot, but what the hell.  

I'm a condensed matter research physicist and use x-ray photoelectron spectroscopy (XPS) a fair amount.  There's a programme for Windows called XPSpeak which allows me to fit semi-Voigt functions (convolved Gaussian-Lorentzian lineshapes) to experimental spectra, as well as doing background subtractions.  I've yet to find anything similar in Linux, and am hoping that someone on here might know of something I could use?  (XPSpeak is the only Windows programme that I *need* to use... getting an open source programme to do these bits would mean I can do everything in Ubuntu... hurray!)

The other problem I have with XPS data is I'm going to be using some theoretical calculations (some of my own, some in collaboration with Cambridge university) of the valence band electron density-of-states to compare with experimental XPS data.  In order to do this I will need to convolve the calculated data with Gaussians and Lorentzians.  Does anyone have any suggestions how to do that?  I was thinking about writing something in Scilab, but if anyone has any programme that can do that for me, I'd be hugely appreciative.  :)

---

### Post by juggies on 2008-09-17
As far as using pseudo-Voigt function for your fitting thats a bit odd unless ofcourse you are using non-monochromatic x-ray.. anyway I had used a program called x-fit which is meant to fitting standard X-ray diffraction peak where usually the K-beta part gives rise to kind of doublet peak. X-fit does bothpseudo-Voigt and also Pearson 7 function. Unfortunately I did not try the shirley baseline corrections.. you might want to give it a try. X-fit was developed by the CCP project

:)

   
> **Lateralis said:**
> Thanks for your reply, Tharmas!  

Just had a look at fityk and it does have an option to fit pseudo-Voigt functions to XPS data.  Not yet played around with it as I'm off to teach presently, but this looks very promising indeed.  Not sure if it will give me the freedom to manually fit peaks that XPSpeak gives me.  If it doesn't, I'll try going down the VM route.  

Thanks again.

---

### Post by kaspar_silas on 2008-09-23
Such a deja vu moment as I had whilst reading this. A few years ago I was after exactly the same tools you mentioned. (I was doing X-ray spectroscopy at the time.)

I decided to write some programs for fitting and background removal. I don't actually have them at present but I can contact my old work to try and get them. 

But first, do you know c++? This is what I wrote the program in and the codes have no interface so you have to alter the code itself. On the plus side this was my first c++ project so it's not exactly high level code thou it does use some numerical recipe code for the fitting. 

As to the convolving of theoretical results. What are you planning to view the spectra with? Even in excel you can do convolution on the fly. Or am I missing something here?

---

### Post by Lateralis on 2008-09-24
Thank you to all who have replied since my last message.  I have been keeping an eye on the thread, but I've not a lot to report at the moment.  

fityk looks pretty usual with some very nice tools, but is unsuited to the stuff that I'm doing.  It can fit pseudo-Voigt functions, but it is quite cack-handed to use.  I also did try to get hold of Kowk at Hong Kong University, but his e-mail address wasn't working.  

I've not done C++ programing before, but I can program in Fortran.  What I could do with though is a graphical interface when fitting the data - there are many subtle effects that influence the shape of XPS features which are impossible to code into an automatic fitting program and necessitates a trial and error approach by hand.  The background in XPS data isn't as simple as a linear background either, but is a slightly more complicated "Shirley" background, although if Kwok can implement that then it shouldn't be too much of an issue. 

As for the psudo-Voigt fitting itself, the biggest source of a Gaussian lineshape in XPS comes from the x-ray source.  The Daresbury Laboratory XPS machine uses a high intensity, highly monochromated Al K-alpha x-ray source, but other instrumental factors also contribute a Gaussian lineshape to the data.  As such, you invariably have to accept that no matter how good the source, the data will always have Lorentzian (from the lifetimes of excited states) and Gaussian components.  

As for the convolution of theoretical spectra, I've never done anything like that in Excel before, but I wouldn't trust Excel to do it properly either.  Moreover, I'm looking for a program that is open source and can run on Linux!  :P  I think the easiest thing to do is probably to use Scilab/Matlab, but if anyone knows of any program that has a handy "Convolve this data with a Gaussian/Lorentzian!" button, then let me know!

With regards to CCP5, I was rather excited!  However, I didn't see any downloadable program and it would appear as though I need to be a member of the group (which costs).  Is that the case, Juggies?

---

### Post by kaspar_silas on 2008-09-24
Sorry, I should have been clearer, I didn't mean to automate the whole procedure. I meant to alter the code to give you an interface. But it seems you have other options now anyway.

O Incidentally the background fit I did was far from a simple linear fit. It fitted any function. You simply coded the equation you wanted to fit, the range to fit over, some parameter estimates and it did non linear fitting. It sounds impressive but like I said I used numerical recipe code for all the hard stuff. 

I am a bit confused by the line "there are subtle effects that influence the shape of XPS features which are impossible to code into an automatic fitting program". Are you fitting by hand? Otherwise surely you take away a background, form an equation you think is applicable for your data then do whatever fitting you want. I can't think of any subtle effects that are outside this method but let me know if I am wrong. 

Lastly I didn't mean you to use excel, I hate excel. For one it added about a month to my PhD. I was just pointing out that absolutely anything, that can multiply and add, can do convolution. I would totally trust excel to do convolution. In fact much more than any button because it would be me entering the equations. Admittedly I could look up the button's action if it was an open source program in a language I knew (but I probably wouldn't).

---

### Post by robertp999 on 2008-09-25
On my setup, it looks like Xpspeak installs and runs fine (Ubuntu 8.04 / Inspiron 8600). I downloaded Xpspeak 4.1 from [http://www.phy.cuhk.edu.hk/~surface/XPSPEAK/](http://www.phy.cuhk.edu.hk/~surface/XPSPEAK/).

After unzipping the archive in its own folder, I ran "wine setup.exe", and it installed normally.

The wine version I'm using is wine-1.0, with default settings of "Windows XP" in winecfg.

Hope this helps.

---

### Post by juggies on 2008-10-28
I know that all the CCP work were free but I think many of their work are vanishing... Xfit is for analyzing X-ray diffraction but I made it work for XPS too. It was a little frustrating using it in the beginning but once you get used to it... it was fun. On a different note I came across this site which might be of help

[http://escalab.snu.ac.kr/~berd/Fitt/fitt.html](http://escalab.snu.ac.kr/~berd/Fitt/fitt.html)

Let me know how it is :)

 

> **Lateralis said:**
> Thank you to all who have replied since my last message.  I have been keeping an eye on the thread, but I've not a lot to report at the moment.  

fityk looks pretty usual with some very nice tools, but is unsuited to the stuff that I'm doing.  It can fit pseudo-Voigt functions, but it is quite cack-handed to use.  I also did try to get hold of Kowk at Hong Kong University, but his e-mail address wasn't working.  

I've not done C++ programing before, but I can program in Fortran.  What I could do with though is a graphical interface when fitting the data - there are many subtle effects that influence the shape of XPS features which are impossible to code into an automatic fitting program and necessitates a trial and error approach by hand.  The background in XPS data isn't as simple as a linear background either, but is a slightly more complicated "Shirley" background, although if Kwok can implement that then it shouldn't be too much of an issue. 

As for the psudo-Voigt fitting itself, the biggest source of a Gaussian lineshape in XPS comes from the x-ray source.  The Daresbury Laboratory XPS machine uses a high intensity, highly monochromated Al K-alpha x-ray source, but other instrumental factors also contribute a Gaussian lineshape to the data.  As such, you invariably have to accept that no matter how good the source, the data will always have Lorentzian (from the lifetimes of excited states) and Gaussian components.  

As for the convolution of theoretical spectra, I've never done anything like that in Excel before, but I wouldn't trust Excel to do it properly either.  Moreover, I'm looking for a program that is open source and can run on Linux!  :P  I think the easiest thing to do is probably to use Scilab/Matlab, but if anyone knows of any program that has a handy "Convolve this data with a Gaussian/Lorentzian!" button, then let me know!

With regards to CCP5, I was rather excited!  However, I didn't see any downloadable program and it would appear as though I need to be a member of the group (which costs).  Is that the case, Juggies?

---

### Post by juggies on 2008-10-28
One more thing I forgot... here is the link to xfit

[http://www.ccp14.ac.uk/tutorial/xfit-95/xfit.htm](http://www.ccp14.ac.uk/tutorial/xfit-95/xfit.htm)

again this is a windows s/w but gives you a good handle interms of fitting with psuedo vogit or pearson VII function. The background it tricky since you are making a s/w meant to XRD do a shirley correction but play around the function a bit.

---

### Post by 080801jk on 2008-10-30
&#22240;book type&#30340;&#21306;&#21035;&#32780;&#23548;&#33268;&#20860;&#23481;&#24615;&#30340;&#24046;&#24322; &#21051;&#24405;&#25968;&#25454;&#26102;&#23558;&#20250;&#21051;&#24405;&#34920;&#31034;&#20809;&#30424;&#31181;&#31867;&#30340;book type&#12290;[**&#20809;&#30424;&#21046;&#20316;**](http://www.itd9.com)&#25773;&#25918;&#35774;&#22791;&#21033;&#29992;&#36825;&#37096;&#20998;&#20449;&#24687;&#21028;&#26029;&#26159;&#21542;&#20026;&#21487;&#25773;&#25918;&#20809;&#30424; &#12288;&#12288;&#26377;&#30340;&#25773;&#25918;&#35774;&#22791;&#21482;&#23545;book type&#21069;&#30340;&#20809;&#30424;&#29305;&#24615;&#36827;&#34892;&#26816;&#27979;&#65292;[**&#20809;&#30424;&#21046;&#20316;**](http://www.itd9.com/index.asp)&#26377;&#26102;&#23601;&#20250;&#21028;&#26029;&#8220;&#26080;&#27861;&#25773;&#25918;&#8221;&#12290;[**&#20809;&#30424;&#21051;.2**](http://www.itd9.com/gpkl.asp)&#25152;&#20570;&#30340;&#26816;&#27979;&#37117;&#26159;&#24456;&#22522;&#26412;&#30340;&#19996;&#35199;&#65292;&#20027;&#35201;&#26159;&#30475;&#30475;&#8220;&#26159;&#21487;&#21051;&#24405;&#36824;&#26159;&#25773;&#25918;&#19987;&#29992;&#65311;&#8221;[**&#20809;&#30424;&#25171;&#21360;**](http://www.itd9.com/gpdy.asp)&#12289;&#8220;&#21333;&#38754;&#36824;&#26159;&#21452;&#38754;&#65311;&#8221;&#12289;&#8220;&#21333;&#23618;&#36824;&#26159;&#21452;&#23618;&#65311;&#8221;[**&#20809;&#30424;&#21360;&#21047;**](http://www.itd9.com/ys.asp)&#12290;&#32780;&#20316;&#20026;DVD+R DL&#29305;&#24615;&#30340;&#21333;&#38754;&#21452;&#23618;&#35760;&#24405;&#20809;&#30424;&#21017;&#34987;&#35270;&#20026;&#8220;&#19981;&#23384;&#22312;&#27492;&#31867;&#20809;&#30424;

---

### Post by Lateralis on 2008-11-24
Thanks again to everyone that has replied in this thread with various suggestions, links and tips.  You may all be pleased to know that I have actually got to know Crossover and have used that to install working copies of both Origin and XPSpeak.  My world is now complete!  

By the way Juggies... I just had a quick look at the Fitt programme you linked to in a previous post... I've not installed or used it, but it does look rather dandy and about what I was after.  If I find that XPSpeak isn't working properly with Crossover, then I will give that a shot.  

Thanks again to everyone.  Your posts were very much appreciated.  :)

---

