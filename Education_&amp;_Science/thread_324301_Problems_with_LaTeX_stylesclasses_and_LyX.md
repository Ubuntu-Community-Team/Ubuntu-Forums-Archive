---
title: "Problems with LaTeX styles/classes and LyX"
date: 2006-12-23
forum: Education &amp; Science
---

### Post by Mr Al on 2006-12-23
Hello all,

I've been trying to get to grips with LyX (looks awesome!), but I've come across a few problems. It only seems to recognise some of the LaTeX styles on my machine. Under Document > Settings > Document Class, there are a lot of entries like this:

Unavailable: AGU Article (SGML)

Also, I haven't been able to successfully install any new styles, either. When I try, the style appears to be unavailable just like the others.

Here's how I've been trying to install new styles:

cd /usr/share/texmf/tex/latex/lyx
cp ~/<style file> .
mktexlsr

Then I reconfigure LyX using Tools > Reconfigure.

I've also tried it with a corresponding LyX layout file in ~/.lyx/layouts

I'm using Edgy. Any help anyone can offer would be great!

Cheers,

Allan

---

### Post by kleeman on 2006-12-23
The unavailable stuff is not installed in your latex (not lyx) distribution. There are detailed instructions for installing new style files in lyx in the Customization guide for lyx Chapter 5. To access it open lyx and got to Help---> Customization

---

### Post by Mr Al on 2006-12-24
Thanks kleeman!

That's the one bit of documentation that I'd missed... doh!

I've figured out how to install some LaTeX styles now*, but I still can't get many of them to be recognised. I'm new to LaTeX... are there any differences between styles that I ought to be aware of?!

* Here's how I've been doing it:
1. Drop the style file into /usr/share/texmf/tex/latex/
2. Run texhash (as sudo)
3. Reconfigure LyX (Tools > Reconfigure)
4. Restart LyX

---

### Post by kleeman on 2006-12-24
That sounds basically correct. Which styles are you installing? I always had problems with the sgml styles (I think you need another package installed). The regular agu styles (jgr etc) installed fine using the method you outlined.

---

### Post by Mr Al on 2006-12-26
Glad I'm on the right track at least!

The only style I've had any luck with is an ieee one. I've tried loads of others from Cambridge University Press, MIT Press, NTG and memoir. None of these even turn up in LyX as unavailable. JGR from AGU does appear as available within LyX, but when I try and view a document using it I got the following error:

	> Class aguplus Error: No valid ACUTeX package given as an option.

Underneath that I get this:

	  >   \stop}{}
                
	Valid AGUTeX package names are:
	agums, agupp, jgrga, grlga, radga, rtjga, tecga, paleo

I'm clearly missing something fairly fundamental, it's just that I don't have any idea what that might be!

Any suggestions?!

---

### Post by kleeman on 2006-12-26
> **Mr Al said:**
> Glad I'm on the right track at least!

The only style I've had any luck with is an ieee one. I've tried loads of others from Cambridge University Press, MIT Press, NTG and memoir. None of these even turn up in LyX as unavailable. JGR from AGU does appear as available within LyX, but when I try and view a document using it I got the following error:

	
Underneath that I get this:

	  
I'm clearly missing something fairly fundamental, it's just that I don't have any idea what that might be!

Any suggestions?!
Yeah I get that too. That style requires you specify one of agums, agupp, jgrga, grlga, radga, rtjga, tecga, paleo (the many different agu doc styles) as an option. The box to do this is just below where you specified the AGU (JGR++) document style.

---

### Post by Mr Al on 2006-12-26
Ah....! Eureka! That gives me enough styles to get me going, at least.

It is a little disappointing that I'm not able to use any of the other styles that I've found (with ease, anyway), but all in all, LyX looks amazing to me. I can't wait to be able to format some of my own material with it.

Thanks again, kleeman!

---

### Post by harishg on 2006-12-30
Many of the journals do not have a layout file for lyx.With some trouble you can make a layout file from the cls file.It will have a lot of ERT though

---

### Post by kleeman on 2006-12-30
> **harishg said:**
> Many of the journals do not have a layout file for lyx.With some trouble you can make a layout file from the cls file.It will have a lot of ERT though
What I do is to write the paper using lyx and then export it to latex. A lot of journals will give you the latex style files which you can install. I then edit the latex file manually and compile using latex. Works well.

---

### Post by Mr Al on 2007-01-02
Hmm... not sure if I'm prepared to learn LaTeX just yet!

Am I right in assuming that I would have more luck with the LaTeX styles I've been trying to use with LyX if I exported my document as a LaTeX file and then used LaTeX on it 'straight' (as opposed to invoking LaTeX via LyX)?

---

### Post by kleeman on 2007-01-02
A lot of journals offer a latex template and once you export from lyx to latex it is pretty obvious which text you need to plonk into the template. I have had better luck with latex getting specialised style files recognized. latex isn't that hard but I prefer lyx for the initial writing because you don't have to remember any latex symbols (like say /alpha or whatever)

---

### Post by gnomesrule123 on 2008-06-01
Hi i was just having lots of trouble with my version of lyx 1.5.5-2
it didn't seem to read any of the preset layout files included in the lyx package i installed so therefore i couldn't convert them to pdf (my usual means of printing) i was wondering if anyone had had the same problem and if there were any fixes (by the way i am a complete newbie in the world of lyx and latex so it may take me a while to catch on to what anyone says

---

### Post by kleeman on 2008-06-02
The style files are latex files not lyx files per se. Latex is installed via the texlive package so it may be that some of your texlive packages are missing. Fire up synaptic and search for texlive. Install as many as possible. Then go into lyx and

Tools-----> Reconfigure

logout and in again....

---

### Post by o_rendon on 2011-07-14
You will have to install the latex packages that have the layouts or classes that you need, for example to have a&a (aa.cls) in lyx  I installed:
sudo apt-get install jlatex209-base latex209-base texworks 
ran reconfigure , restarted lyx ... and the aa template worked!!!

---

