---
title: "Missing console in R"
date: 2010-11-18
forum: Education &amp; Science
---

### Post by ericstrom on 2010-11-18
Currently running Lucid and decided I wanted to start using R statistical software. I was able to load:

R version 2.12.0 (2010-10-15)
Copyright (C) 2010 The R Foundation for Statistical Computing
ISBN 3-900051-07-0
Platform: i486-pc-linux-gnu (32-bit)

I also loaded R Commander.

When I open the terminal and type in R to boot up, the program seems to work OK except I don't get the R console. I have to work in Ubuntu terminal. My understanding is when R boots up, it opens a console window with a specialized menu. For me, I can only stay in Ubuntu terminal and I don't have access to any specialized menus. 

Is this normal ? Most of the screen shots I've seen show a R console window. I don't really like working out of the Ubuntu terminal window because it's basically transparent (I can see right through it to my desktop icons) and also I don't have any R menu items at all.

Should I see a console window ? If yes, what should I try to geet the issue resolved ?

---

### Post by NikoC on 2010-11-19
Aren't you supposed to launch Rcommander from within the terminal window where you've started R?

I think this was the command: Library(Rcmdr)

Good luck, 

NikoC

ps. it might take a bit to launch the package

---

### Post by earlycj5 on 2010-11-19
> **ericstrom said:**
> Currently running Lucid and decided I wanted to start using R statistical software. I was able to load:

R version 2.12.0 (2010-10-15)
Copyright (C) 2010 The R Foundation for Statistical Computing
ISBN 3-900051-07-0
Platform: i486-pc-linux-gnu (32-bit)

I also loaded R Commander.

When I open the terminal and type in R to boot up, the program seems to work OK except I don't get the R console. I have to work in Ubuntu terminal. My understanding is when R boots up, it opens a console window with a specialized menu. For me, I can only stay in Ubuntu terminal and I don't have access to any specialized menus. 

Is this normal ? Most of the screen shots I've seen show a R console window. I don't really like working out of the Ubuntu terminal window because it's basically transparent (I can see right through it to my desktop icons) and also I don't have any R menu items at all.

Should I see a console window ? If yes, what should I try to geet the issue resolved ?

R from the console window is only a console window with a ">" prompt and no specialized menus.

To load Rcommander you would type:
```

login@computer-name:~$ R

R version 2.11.1 (2010-05-31)
Copyright (C) 2010 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

>
> library(Rcmdr)

```

That will launch Rcommander for you.

You can also edit the transparency of the profile you're currently using in your console window so that it's not transparent.

---

### Post by ericstrom on 2010-11-19
I can boot R Commander with no problem. But even after R Commander is running, I don't see a screen that says Console. Within R Commander I see a Script Window and a Output Window; but no Console window. The only thing else I see is the original Ubuntu terminal window open. 

Yes, R is running (with the > prompt) in the Ubuntu terminal window. But that window has the purple Ubuntu tint to it and is fairly transparent (i can see desktop icons through the Ubuntu terminal window)

So my question ...is that what I'm supposed see ? Should I have a separate console window; not just the Ubuntu terminal window ?

---

### Post by gunksta on 2010-11-19
You are seeing exactly what you are supposed to see. It may not be what you want to see, but it sounds perfectly normal.

On Windows and Apple - R comes with a fancy GUI by default. On our platform, we get a fancy terminal program by default.  :popcorn:

If you dig through the threads here, there are lots of options to improve/modify the interface. Most are third-party. Most folks here either use ESS (an EMACS major-mode) or the Vim R-Plugin which is developed by someone here in the forum. Emacs/ESS are in the repos. The Vim plugin is not but it is easily obtained and the developer is really friendly and willing to help you get it set up. Other options include tools such as JGR (not in the repos).

Finally, you could just activate R's default Tk interface. Rather than start R with the command 'R' try this: 'R -g Tk'. This will only work from the command-line and gives you a funky-ish screen with some really basic menus, but it basically disables the terminal interface, which is why most of us ignore it.

I always tweak my settings in my terminal application to eliminate the transparency. I have never been a fan of transparency in a terminal app. It's not usable. But, it's easy to make it just plain white on black or black on white or what have you.

---

### Post by earlycj5 on 2010-11-20
I know it's dirty since it's KDE and not GTK or something, but some of us here use RKward too because it just works...

---

### Post by gunksta on 2010-11-21
Working doesn't equal dirty. I think new users are probably well advised to use tools that are usable on multiple platforms, simply because there are more resources on how to use them and you are more likely to useful answers on forums, etc.

But if it works, it works. I personally really like KDE and kinda wish Ubuntu, et al were more interested in pursuing a KDE based future. But, Unity seems to be the new hotness. We shall see.

---

