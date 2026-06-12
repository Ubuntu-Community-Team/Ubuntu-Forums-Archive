---
title: "matlab / scilab / octave"
date: 2006-08-30
forum: Education &amp; Science
---

### Post by ubuntu_demon on 2006-08-30
Hi,

I haven't tried scilab nor octave yet. I have a couple of questions :

* If someone (for example a teacher) requires matlab code. Can I produce code using octave/scilab which will fully work (guaranteed) on matlab ?

* Is it easy/feasible to work together on code with people who might insist on using matlab (when I use scilab/octave) ?

* Is there some tutorial for working together with matlab ?

thanks guys

---

### Post by Miguel on 2006-08-30
Hi,

I personally can't answer your questions. I've never really used Matlab, though I have an engineer colleage that uses it daily for his job so I suppose I could ask him. 

What I really wanted to tell you is not to install the version of scilab in multiverse. It was buggy for me (fonts basically) and it is pretty outdated (over 1 year old). The binaries work OK, and compiling it isn't difficult at all. You will probably have to chmod $USER:$USER ~/.scilab, though

---

### Post by ubuntu_demon on 2006-08-30
> **Miguel said:**
> Hi,

I personally can't answer your questions. I've never really used Matlab, though I have an engineer colleage that uses it daily for his job so I suppose I could ask him. 


Please ask him :)
Is he using octave/scilab at home and matlab at work ? Is that easily possible and productive ?

> **Miguel said:**
> 
What I really wanted to tell you is not to install the version of scilab in multiverse. It was buggy for me (fonts basically) and it is pretty outdated (over 1 year old). The binaries work OK, and compiling it isn't difficult at all. You will probably have to chmod $USER:$USER ~/.scilab, though

thanks

---

### Post by hesee on 2006-08-30
I think that basic syntax is pretty much the same. But, there is probably quite lot functions in matlab which won't work in scilab, for example. I did one quite big project with matlab, and tried to run it in linux/scilab, but that caused too much trouble. I had used matlab-specific complicated functions which weren't available in scilab.

---

### Post by Miguel on 2006-08-30
> **ubuntu_demon said:**
> Please ask him :)
Is he using octave/scilab at home and matlab at work ? Is that easily possible and productive ?

thanks

I've just sent him an e-mail. He answers pretty fast, though he will probably be having his lunch now. 

However, I fear I haven't explained myself. He uses Matlab exclusively (or so I thought), however he has quite a decent knowledge of it so I hope he or someone around him has some experience and can enlight us.

---

### Post by sylvestre on 2006-08-30
> **ubuntu_demon said:**
> 
* If someone (for example a teacher) requires matlab code. Can I produce code using octave/scilab which will fully work (guaranteed) on matlab ?

No, the scilab code is different from Matlab. There is an assistant translator Matlab => Scilab (not the other way). I don't know for Octave.
You should ask to your teacher if you can use Scilab (which is free and opensource) instead of matlab.

> **ubuntu_demon said:**
> 
* Is it easy/feasible to work together on code with people who might insist on using matlab (when I use scilab/octave) ?

It should be OK.

> **ubuntu_demon said:**
> 
* Is there some tutorial for working together with matlab ?

It is not exactly what you are looking for but it might help you :
[http://www.scilab.org/doc/demos_html/node265.html](http://www.scilab.org/doc/demos_html/node265.html)

---

### Post by monktbd on 2006-08-30
i am quite sure you already stumbled across this:
[http://www.scilab.org/faqV1.2/faq1.2013.html](http://www.scilab.org/faqV1.2/faq1.2013.html)

i tried to convert a few matlab scripts to scilab scripts and it didnt work well at all. it was basically reading some files and then doing some filtering and fft on it.

if you can manage to do just some basic matrix manipulation i think it works well together, everything beyond that might be quite tricky.

my knowlege in scilab is still quite limited but the differences are obvious and make it difficult to share scripts but the general syntax and even quite a big bunch of commands are the same.

---

### Post by slimdog360 on 2006-08-30
I suppose it depends on what you want to do with the code. Most of the code for octave is the same in matlab (note I said **most** code). So I suppose it cant be guaranteed. Some of the plotting is different but for what Ive done it works the same in both.

I use Koctave and mousepad to do all my octave/matlab programming, for some reason I dont like the text editor in koctave. If you want a matlab replacement you should use octave.

---

### Post by hizaguchi on 2006-08-30
I don't know anything at all about Scilab, but I'm a mechanical engineering student and I use Octave exclusively for my "Matlab" assignments.  I've never had any problems doing this, and I've even used it in group projects where other members of the team ran my code in Matlab without any trouble.  I'm sure there are some things that aren't 100% compatible, but as long as you stick to basic operations and stay away from Matlab's proprietary functions (like ode45), you should be fine.

And I have no idea why any college would suggest using Matlab when there is an open source (therefore free, free, and peer reviewed) alternative.  And I'm especially confused by college students who would rather spend $100 on a temporary license than download Octave for free, even after being shown the website, and even though there is now a pre-packaged Windows version.  Must have more money than me.

---

### Post by hizaguchi on 2006-08-30
> **slimdog360 said:**
> I use Koctave and mousepad to do all my octave/matlab programming, for some reason I dont like the text editor in koctave. If you want a matlab replacement you should use octave.
Mousepad?  Blasphemy!  Kate, with the embeded Konsole, is your friend. :)

---

### Post by paulmilliken on 2006-09-26
I have used Matlab, Scilab and Octave extensively.  Octave is almost identical to the core Matlab, however, there are a few small differences.  One of the main differences is the "plot" command and related commands to save figures etc.  Matlab has its own plotting functions but Octave uses Gnuplot.  I find Gnuplot a little awkward to use.

The Syntax of Scilab is a little different to Matlab and Octave but it doesn't take long to learn.  Also, I have found Scilab to be a bit more polished than Octave and I like the syntax now that I have gotten used to it.

In summary, all 3 programs are very good but overall Scilab is my favorite.

BTW, the version of Scilab in the repos seems to use Tamil fonts by default so I compiled the latest version from source.  If you choose to compile from source you will need to install a few *-dev packages from Synaptic (./configure will complain each time it can't find something).

Paul

---

### Post by roderikk on 2006-10-07
Hi,

I have been working a lot with GNU/Octave recently. I find it is quite compatible with matlab. Sometimes I write an if statement in the (for matlab) incorrect syntax, and I find it very annoying that i++; doesn't work in Matlab but other than that it is fine.
I am also in the process of learning a bit more about GNUplot. I think it can really create some beautiful output, when you know all the options at least (and let it output to ps or eps).
Now I just have to master LaTeX and I will be set for a completely open source master thesis...

I've also seen that in edgy octave 2.9 is in the repos. Does anyone know the differences with the 2.1 branch?

Good luck!

---

### Post by punchy on 2006-10-07
Hello,

I see all this talk about matlab/octave/scilab.

I have used them all before, and they are not bad.

But you should really have a look at python, and its modules pylab and scipy. 

Its for free, and, in my opinion, much more powerful than Octave.

Cheers,
Punchy

---

### Post by roderikk on 2006-10-08
> **punchy said:**
> Hello,

I see all this talk about matlab/octave/scilab.

I have used them all before, and they are not bad.

But you should really have a look at python, and its modules pylab and scipy. 

Its for free, and, in my opinion, much more powerful than Octave.

Cheers,
Punchy
Hm, I have never been introduced to that. Can you do everything with it in a 'fairly' straightforward way, as in Octave? Is it a steep learning curve? Would you happen to know some good (introductory) tutorials?

---

### Post by arkangel on 2006-10-15
Octave  is the closest to Matlab ,you can write script for one and use in the other ,   unfortunately matlab is much faster

---

### Post by rebbo on 2006-10-24
* If someone (for example a teacher) requires matlab code. Can I produce code using octave/scilab which will fully work (guaranteed) on matlab ?

NO not all the octave codes will run on MATLAB, its library is big and many functions are different

* Is it easy/feasible to work together on code with people who might insist on using matlab (when I use scilab/octave) ?

Most of the matlab files can run on octave but its not always true in reverse. Matlab is a buisness and Octave a open source.

* Is there some tutorial for working together with matlab ?
you may be able to find some material on mathworks or [www.kluid.com](www.kluid.com) but not much.

Note: If you know some one who is a student you can buy a student version of matlab for around 100$ ... it can do most of the common tasks.

Rebbo

---

### Post by acegolfer on 2006-10-25
I have used matlab for 7 years in windows. I tried octave the last 2 months and gave up.

From my experience, matlab and octave are 95% compatible. Basic functions are okay. But matlab toolbox functions don't work in Octave. Even some basic functions are not the same. No wonder the same program gave me different results. After realizing this which took roughly 1 month, I stopped using Octave. I installed matlab in Ubuntu 6.0.6 (search it, it was really easy) and now I'm a happy camper.

---

### Post by boz on 2006-10-26
Pardon my hasty and mindless contribution to this thread, but I've only been using Octave for a short period of time and it *@*#&$* rules. :twisted:  I haven't tried Scilab.

---

### Post by J77 on 2006-10-26
I use Matlab - but my research grant pays for it 8) 

If I were a student, I'd defintely invest in the student edition - it's cheap and the mathworks support is excellent.

For tutorials, I'd look to: [http://www.ma.man.ac.uk/~higham/mg/](http://www.ma.man.ac.uk/~higham/mg/)

---

### Post by joneberger on 2006-11-02
so i use matlab and i have octave installed on my computer.  i'd love to see the world go octave...but it won't happen.   if you're using octave for a basic coding class where yuo do most of the work yourself and can keep the matlab/octave differences straight, you're fine.  if you're relying on built-in functions (any of the ODE solvers/optimization routines) matlab is the way to go.  i'm sure counterparts exist in octave, but no one is going to use it when they're already using matlab on their local workstation.  

so i say you can use it well...depending on how matlab is used in your curriculum.

---

### Post by Qtea on 2007-01-27
> **hizaguchi said:**
> I don't know anything at all about Scilab, but I'm a mechanical engineering student and I use Octave exclusively for my "Matlab" assignments.I've been doing the same with Scilab and never had any complainments. I guess the most important thing still is to show that you've understood the theory and can do some practical computing based on it. 

> **hizaguchi said:**
> And I have no idea why any college would suggest using Matlab when there is an open source (therefore free, free, and peer reviewed) alternative.  And I'm especially confused by college students who would rather spend $100 on a temporary license than download Octave for free, even after being shown the website, and even though there is now a pre-packaged Windows version. Must have more money than me.Matlab is probably the most used program for numerical computing in the industry and the colleges are thus very interested in making the students fluent in Matlab, because they think that to be the industry's need.

 [quote=J77]I use Matlab - but my research grant pays for it

If I were a student, I'd defintely invest in the student edition - it's cheap and the mathworks support is excellent.[/quote]Hmm, how cheap it really is? The basic version is about $100 and the toolboxes are $60 each. If you begin with buying the basic version at the first year of your studies and later when you take advanced cources in eg. statistics, signal processing or system control, you're forced to complicate your Matlab with the toolboxes. You'll end up buying all their software, piece by piece and soon your system will cost far over $1000 - and that's still the student version.

---

### Post by WebDrake on 2007-01-27
> **ubuntu_demon said:**
> Hi,

I haven't tried scilab nor octave yet. I have a couple of questions :

* If someone (for example a teacher) requires matlab code. Can I produce code using octave/scilab which will fully work (guaranteed) on matlab ?

* Is it easy/feasible to work together on code with people who might insist on using matlab (when I use scilab/octave) ?

* Is there some tutorial for working together with matlab ?

thanks guys
I don't know SciLab at all well, however, I do make use of Octave and have used MATLAB quite a lot in the past.

As other people have noted Octave is very close to MATLAB, with near-identical syntax and a great overlap of commands.  For simple code I think you will find it easy to coexist.  However, there are some key features which MATLAB has which Octave lacks, notably graphical functions.  Octave plotting commands are quite limited in their possibility compared to MATLAB, although this will hopefully be changed in a big way in the forthcoming 3.0 release.  Since Octave uses gnuplot as its plotting engine, it is possible to make use of direct gnuplot commands to produce a lot of what you may want, but obviously this is not MATLAB-compatible.

It's possible, with MATLAB, to produce quite attractive GUIs for data analysis environments (I worked in a lab which had produced a marvellous package to analyse neural data read from multielectrode arrays), but you couldn't do the equivalent with Octave at present.

For general purposes (not your MATLAB assignments) you might also want to take a look at R, which is most definitely *not* MATLAB-compatible, but has a whole bunch of useful data analysis possibilities.

Have a look at [http://www.gnu.org/software/octave/FAQ.html#SEC24](http://www.gnu.org/software/octave/FAQ.html#SEC24) for a brief note on some of the issues.

---

### Post by skywatcher on 2007-02-25
Hi everyone

If I may chip in at this stage, I share hizaguchi's sentiments:

> **hizaguchi said:**
> And I have no idea why any college would suggest using Matlab when there is an open source (therefore free, free, and peer reviewed) alternative.  And I'm especially confused by college students who would rather spend $100 on a temporary license than download Octave for free, even after being shown the website, and even though there is now a pre-packaged Windows version.  Must have more money than me.

I have been using Matlab since 1989, and I must admit that one gets hooked on all the GUI features and toolboxes of the newer releases. But I must also admit that the cost of the software is prohibitive -- I'm lucky because my employer pays for it!

As a newcomer to Linux I installed octave a few days ago, and I plan to do some comparisons and look at compatibility etc. Hopefully I'll be able to answer some questions on this forum in future.

---

### Post by vikasmk on 2007-11-13
hi, i installed octave on my pc, but i could not plot any graphs bcos gnu plot wasnt there. but i could not download it from the package manager . it said there was some error and kept asking for the gutsy 7.10 cd rom . help me.......:confused:

---

### Post by iml on 2007-11-15
> **vikasmk said:**
> hi, i installed octave on my pc, but i could not plot any graphs bcos gnu plot wasnt there. but i could not download it from the package manager . it said there was some error and kept asking for the gutsy 7.10 cd rom . help me.......:confused:
Open Synaptic and Settings -> Repositories. Uncheck 'Cdrom with Ubuntu' and make sure main and universe are checked. Reload then try installing gnuplot.

---

