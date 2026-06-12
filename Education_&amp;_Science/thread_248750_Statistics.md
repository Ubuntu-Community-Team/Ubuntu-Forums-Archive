---
title: "Statistics"
date: 2006-09-01
forum: Education &amp; Science
---

### Post by Eltern on 2006-09-01
I'm trying to find a replacement for Statistica or SPSS on Linux, and after several hours of scouring the net for such a program, I've found nothing. 

What I'm looking for something that has a GUI, spreadsheet capabilities, decent graphing, and a signficant amount of statistical analyses available with a few mouse clicks (namely repeated and multiple measures ANOVA). As I said, I'm basically looking for SPSS or Statistica ;) 

I've toyed around with R and R Commander, but that's still too rough of a GUI for me. It could be that I just didn't understand it sufficiently, but it seemed that I would have to do a lot of coding to accomplish what SPSS can do in three button clicks. Granted, if I were trying to do very complicated and/or unique analyses, I might like R's robustness. But that's not what I'm doing.

Is anyone else in the same position as me? What did you do? Is it possible to use a particular combination of packages with R, or some other program, to achieve this effect?

Thanks!

---

### Post by akniss on 2006-09-26
> **Eltern said:**
> I'm trying to find a replacement for Statistica or SPSS on Linux, and after several hours of scouring the net for such a program, I've found nothing. 

What I'm looking for something that has a GUI, spreadsheet capabilities, decent graphing, and a signficant amount of statistical analyses available with a few mouse clicks (namely repeated and multiple measures ANOVA). As I said, I'm basically looking for SPSS or Statistica ;) 

I've toyed around with R and R Commander, but that's still too rough of a GUI for me. It could be that I just didn't understand it sufficiently, but it seemed that I would have to do a lot of coding to accomplish what SPSS can do in three button clicks. Granted, if I were trying to do very complicated and/or unique analyses, I might like R's robustness. But that's not what I'm doing.

Is anyone else in the same position as me? What did you do? Is it possible to use a particular combination of packages with R, or some other program, to achieve this effect?

Thanks!

It seems in the free statistics software world, you either get to perform complex statistics properly, ***OR*** use a GUI... not both.  R has the most functionality, but can be a real pain in the @$$ to learn to use efficiently (although its worth the time in my opinion).  PSPP tries to mimic SPSS and has a GUI, but the statistical functionality is still pretty limited.  There are some promising projects to put a user-friendly face on top of R, most notably JGR (pronounced Jaguar) and RKward.  However, neither is in the Ubuntu repos at the current time, and I've not had success installing rkward (I haven't tried JGR).

---

### Post by gbutalid on 2006-10-09
Hey akniss, have you tried R in Dapper Drake? I'm using it in the command line, much like the RGui in Windows but I had trouble with the Graphics. I installed all the necessary x11 fonts. I also saw this problem in the R mailing list. But no one has posted a solution. I also used Octave in the command and there is no problem if I ask for a plot through Gnuplot.

The errors that I got when I try to make a histogram in R is posted below.

[COLOR="DarkGreen"]> hist(rnorm(100))
Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.
In addition: Warning messages:
1: locale not supported by Xlib: some X ops will operate in C locale
2: X cannot set locale modifiers
[/COLOR]

Thanks in advance.

---

### Post by akniss on 2006-10-10
> **gbutalid said:**
> Hey akniss, have you tried R in Dapper Drake? I'm using it in the command line, much like the RGui in Windows but I had trouble with the Graphics. I installed all the necessary x11 fonts. I also saw this problem in the R mailing list. But no one has posted a solution. I also used Octave in the command and there is no problem if I ask for a plot through Gnuplot.

The errors that I got when I try to make a histogram in R is posted below.

[COLOR="DarkGreen"]> hist(rnorm(100))
Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.
In addition: Warning messages:
1: locale not supported by Xlib: some X ops will operate in C locale
2: X cannot set locale modifiers
[/COLOR]

Thanks in advance.


Sorry to not be any help, but I've been using R successfully in Dapper since shortly after it was released... and I've not had any trouble with the graphics.  As a possible workaround... have you tried setting the fonts to something else with a call to par()?  I have no idea if it would help...

---

### Post by stevetxt on 2006-10-21
I get this error too when I try to use R in edgy.  So it is not possible to do any graphics in R.  There was no problem with R in dapper.

---

### Post by seelenhirt on 2006-10-25
i don't know the cause of this problem but setting LANG to something other than en_US.UTF-8 works for me.

$ LANG=en_US.ISO-8859-1 /usr/bin/R

hope this helps

m

---

### Post by stevetxt on 2006-10-26
Thanks Seelenhirt.  

I've similarly been using 
LANG=C R
as a temporary fix.  It seems to work fine, but I still wonder where the problem comes from, so a real fix is possible.  As I understand it, "LANG=C" tells R to use whatever font defaults are in the program and not try any language translation based on locale first.

---

### Post by gbutalid on 2006-10-27
Thanks!

I can now create charts. But I always start R in the commandline with this:
"$ LANG=en_US.ISO-8859-1 /usr/bin/R"

Is there a way to save this, because when I have to start R again in the terminal by typing "R" I still can't make plots--I have to type the said command again.

Thanks again for the big help.

---

### Post by gbutalid on 2006-10-27
And one more thing. When I was still using Windows and I plot something through R, I just right click on the plot and copy it as a bitmap or metafile, then paste it to a Word document. I tried it in Ubuntu, having R in the terminal, but it doesn't work. Does anyone know how I could copy a plot?  Thanks in advance.

---

### Post by akniss on 2006-10-27
> **gbutalid said:**
> Does anyone know how I could copy a plot?  Thanks in advance.

The best way I've found to get a plot on the linux side is to use the plotting functions in R to save them... rather than trying to copy them from the graphics device as in Windows.

```
png("filename.png")
 plot(x,y)
dev.off()

```

or similarly, using jpeg(), or postscript().

---

### Post by stevetxt on 2006-10-27
This whole thing of having to preface the command with "LANG=..." seems like a bug that should be fixed in Edgy.  But I don't know whether the problem is in xorg, edgy configuration, gnome, the new version of R, or elsewhere.  There was no problem like this in any of the previous versions of Ubuntu.

---

### Post by akniss on 2006-10-28
> **stevetxt said:**
> This whole thing of having to preface the command with "LANG=..." seems like a bug that should be fixed in Edgy.  But I don't know whether the problem is in xorg, edgy configuration, gnome, the new version of R, or elsewhere.  There was no problem like this in any of the previous versions of Ubuntu.

I did a search on the R mailing lists, and they are certain it is not an R issue.  Something to do with the fonts installed matching the locale chosen... not sure if that lies with the distribution or xorg.  There were some Suse users with the same problem.

---

### Post by anoir on 2006-10-29
I don't know much about this issue, but R on Edgy I just installed on vmware today (so clean installation & simple hardware) is working fine so far, including plots like hist(rnorm(100));.

My locale setting is en_US.UTF-8, the default setting. As for fonts, those associated with LyX, i.e., latex-xft-fonts, and several Japanese fonts are installed (should not be relevant).

A little comment to original post: 
If you don't care to use proprietary alternatives, then I recommend you to buy Stata for Linux. It runs on all the major platforms, including 64 bit OSes, and has a great reputation, at least, among social scientists.

---

### Post by stevetxt on 2006-10-29
I have fixed this problem in the following way, which I saw on a thread somewhere.  So now when I type R the graphics work.  No "LANG=" specification is needed.

In Edgy the xfonts are in /etc/share/fonts/X11.  But the automatic configuration of /etc/X11/xorg.conf has lines specifying the fontpaths as in /etc/share/X11/fonts .

I edited /etc/X11xorg.conf to change every instance of X11/fonts to fonts/X11.  

So now that section is

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


whereas the automatic configuration from my clean installation of Edgy was 
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

The new configuration takes effect after rebooting.

---

### Post by tharkban on 2006-10-31
> **gbutalid said:**
> And one more thing. When I was still using Windows and I plot something through R, I just right click on the plot and copy it as a bitmap or metafile, then paste it to a Word document. I tried it in Ubuntu, having R in the terminal, but it doesn't work. Does anyone know how I could copy a plot?  Thanks in advance.

dev2bitmap()

is the command to use (help('dev2bitmap') for usage info)  This is probably the command that the windows version has in the menu.

---

### Post by tharkban on 2006-10-31
changing the path in the xorg.conf file, worked for me.  Thanks!  Why is the default path in edgy broken?!

---

### Post by levin on 2006-11-16
> **stevetxt said:**
> I have fixed this problem in the following way, which I saw on a thread somewhere.  So now when I type R the graphics work.  No "LANG=" specification is needed.

In Edgy the xfonts are in /etc/share/fonts/X11.  But the automatic configuration of /etc/X11/xorg.conf has lines specifying the fontpaths as in /etc/share/X11/fonts .

I edited /etc/X11xorg.conf to change every instance of X11/fonts to fonts/X11.  


This is helpful. I found something similar [here]("http://www.mail-archive.com/r-help@stat.math.ethz.ch/msg74522.html") from R mailing list but I couldn't figure it out until you have explicitly pointed out where are those fonts folder. Thanks stevetxt.

---

### Post by Iurie on 2011-06-21
Undoubtedly, the best replasement for Statistica and SPSS is R! It's free and easy to install! Or just download a live CD with R preinstalled!
[How to install R and some grafical user interfaces for R (R, JGR and Deducer) in Ubuntu/Linux]("http://realshared.com/2011/how-to-install-r-jgr-and-deducer-in-ubuntu-10-04.htm").
[An Ubuntu/Linux live CD with R and some grafical user interfaces for R (R Commander, JGR, Deducer, Rattle, RKWard, RStudio) preinstalled]("http://realshared.com/2011/statistical-r-ubuntu-live-cd.htm").

---

