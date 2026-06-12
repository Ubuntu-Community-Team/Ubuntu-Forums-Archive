---
title: "Any Finance professionals using Ubuntu?"
date: 2008-05-06
forum: Education &amp; Science
---

### Post by Amurko on 2008-05-06
This includes any Accountants, Analysts, Traders, Fund Managers, etc. out here.

I actually switched from Windows to Ubuntu years before I considered a career in Finance.  However, it seems that VBA in Excel is very popular in the industry and Openoffice doesn't offer 100% compatible support with VBA.  

In one Finance class I'm enrolled at school, the prof. allows us to use his pre-approved Excel spreadsheets on laptops for his exams.  Unfortunately, Openoffice doesn't seem to like the VBA code and crashes upon loading the sheets.  I tried installing Excel 2003 in both Wine and Crossover Office; they load fine but won't run the spreadsheets either.  I'm resorting to running Excel and XP via VMWare for the moment which works fine but an awkward solution.

I'd hate to have to switch back to Windows because of this..

---

### Post by getabetterpic on 2008-05-06
I am in a similar situation.  I work in Finance in a corporate environment where M$ rules.  Because of this I have kept a Windows box at home.  I haven't really had the time to look much into open source alternatives to VBA.

So all that being said, if someone has been through this already, I'd be interested to hear about it as well.

---

### Post by tbrminsanity on 2008-05-06
Short of going to your prof and asking for a more cross platform spreadsheet, I think you may be out of luck.

The finance world has not welcomed the Linux community at all and 99% of their software is written for Windows (with the last 1% written for Mac).  The fact you have a VMware solution is awesome (kudos for that) but I think you may have to look at having a dual boot computer.  

Above all make it known to your prof that you don't run windows and that makes it a problem running his spreadsheet.  As a prof he should provide a more friendlier cross platform spreadsheet (I'm sure there are people with Macs that will have the same problem).  If you really wanted to be a jerk you can even take it up with the department (siting prejudices due to your choice of OS). ;)

---

### Post by whelanh on 2008-05-06
I am a quantitative equity portfolio manager in the US.  I actually use Kubuntu via VMware Player on my work computer for my finance work.  I find Linux to be an easier programming/developement environment.  Ultimately you will want to do your own numerical analysis (rather than rely on someone else's VB code).  For that I think you will find the R program ([www.r-project.org](www.r-project.org)) or something similar (e.g. Octave etc.) enormously helpful as there are a lot of contributed packages/software for finance, optimization, etc.(e.g., [http://www.rmetrics.org](http://www.rmetrics.org) or [http://www.quantmod.com](http://www.quantmod.com)).

I know this doesn't help your immediate need (translating Excel macros), but longer term you should certainly not think you will be limited to Windows if you pursue Finance.

Best,
Hugh Whelan

---

### Post by jonabyte on 2008-05-07
i used to do work for a mid-sized accounting firm and the biggest stumbling block to migrating the desktops to Linux was the auditing and tax preparation software all ran on Windows only. I tried contacting the vendors, but they were not interested in looking into providing for Linux.

---

### Post by stephenjbarr on 2008-05-07
> **whelanh said:**
> I am a quantitative equity portfolio manager in the US.  I actually use Kubuntu via VMware Player on my work computer for my finance work.  I find Linux to be an easier programming/developement environment.  Ultimately you will want to do your own numerical analysis (rather than rely on someone else's VB code).  For that I think you will find the R program ([www.r-project.org](www.r-project.org)) or something similar (e.g. Octave etc.) enormously helpful as there are a lot of contributed packages/software for finance, optimization, etc.(e.g., [http://www.rmetrics.org](http://www.rmetrics.org) or [http://www.quantmod.com](http://www.quantmod.com)).

I know this doesn't help your immediate need (translating Excel macros), but longer term you should certainly not think you will be limited to Windows if you pursue Finance.

Best,
Hugh Whelan

Totally agree with everything said. I am a student focusing on computational finance/simulations, and for those things you can use R. There is even an R gui call RKward. Matlab (or its open source companion, Octave) run on Linux. For now, I think the best bet is to use VMWare to run Windows to run office to run the VBA stuff. You have enough to worry about learning the technical parts of finance, so you shouldn't try to spend time getting VBA to work on linux. 

In an econometrics class I am taking, it was recommended that we use a windows-only program (EViews) to do some regression analysis. R will do regression just as well as anything else, so I have been using that.

good luck!

-steve

---

### Post by Amurko on 2008-05-29
I've finished the class but if anyone is curious, here are the spreadsheets:

[http://wps.aw.com/aw_mcdonald_derivmkt_2/](http://wps.aw.com/aw_mcdonald_derivmkt_2/)

Unfortunately, upgrading to 8.04 and OO 2.4 hasn't helped..

---

