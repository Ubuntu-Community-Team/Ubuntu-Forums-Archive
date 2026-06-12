---
title: "R help"
date: 2010-08-13
forum: Education &amp; Science
---

### Post by beew on 2010-08-13
Hi, 

I have used R in Windows and just have it set up in Ubuntu. Now this is a really stupid question. How do I access the manuals? In the windows version there is a drop down menu under help, click it and a nice PDF manual appears. In the Linux version there is no drop down menu. I was trying various help() related commands with no avail. In the R-cran's site they tell you there are a bunch of manuals that come from the installation but they don't tell you how to access them! 

Help, please.

---

### Post by Tart on 2010-08-13
you can use help.start(). It will start HTML help, manuals are available there.

---

### Post by beew on 2010-08-13
> **Tart said:**
> you can use help.start(). It will start HTML help, manuals are available there.

I know, I can also download it from their website or read it on Windows with R's windows version. But that is not my point. If there is a manual in the installation I should be able to find it without having to go through a lot of troubles.

---

### Post by akniss on 2010-08-13
> **beew said:**
> I know, I can also download it from their website or read it on Windows with R's windows version. But that is not my point. If there is a manual in the installation I should be able to find it without having to go through a lot of troubles.
I don't mean to sound snide, but perhaps R is not a good software choice for you if typing "help.start()" is "a lot of troubles." R is really more of a language rather than a traditional statistics program (like Minitab or SPSS) and therefore to get to most of the information, it requires typing words rather than clicking menus. Its not better or worse, just different and it will take some getting used to.


If you are looking for information on a particular function, you can type the function preceded by a question mark:
```
?help.start
?lm
?resid
```

And if you don't know the name of a function, but you know some keywords about what you're looking for, you can use help.search():
```
help.search("anova")
help.search("AIC")
help.search("t-test")
```

Good luck.

---

### Post by Tart on 2010-08-13
> **beew said:**
> I know, I can also download it from their website or read it on Windows with R's windows version. But that is not my point. If there is a manual in the installation I should be able to find it without having to go through a lot of troubles.

help.start() uses local installation files (links to PDFs if installed), so you can see where they are stored.

---

### Post by gunksta on 2010-08-13
It is possible to get the PDF files on a Linux version of R, but I agree that the html version of the help is (to me) more convenient.

```
sudo apt-get install r-doc-pdf
```Look in:

/usr/share/doc/r-doc-pdf/manual

 for the actual files.

Because the default Linux interface . . . . sucks for less experienced users . . . . there is no drop-down accessible access to these PDF files AND new users should be forgiven for:

[LIST=1]
[*]Not knowing how to install these PDF files. They don't appear to be installed by default.
[*]Even if they install them - Good luck finding them. How many new users know that /usr/share/doc is a good place to find the documentation? Many of us know this because we've been knocking heads with Linux for $X years, but this ain't exactly obvious.
[/LIST]
If you would like, you can copy these to your home folder structure somewhere and then remove the package OR you can bookmark the directory in Nautilus. I usually have the docs directory bookmarked in Nautilus and I have my own dired command to open up this directory but not for R.

For R users, the HTML interface is potentially more useful because it is more or less searchable and I personally find the ? command to be invaluable. The other nice trick that helps remembering all of the commands -- ESS mode in EMACS. If you can't remember the options for a command, ESS can tell you what they are. But whether or not ESS is the best front-end for R is not something that I feel like arguing about right now. It's just an option.

Unfortunately, there really isn't a nice, default GUI for R. This problem has been discussed here before (at length) and if you look through the archive of this sub-forum you'll find lots of opinions, rationales, etc. You will also find different options for GUIs (ESS mode is not a GUI). RKward is popular and nice, but it will take a few minutes to install if you don't already use KDE.

---

### Post by hubie on 2010-08-13
> **gunksta said:**
> The other nice trick that helps remembering all of the commands -- ESS mode in EMACS.

Yes, but what is the nice trick to remembering all those archaic EMACS keystrokes???  :D

Besides, we all know that vi is the true way to go .....    :P

---

### Post by gunksta on 2010-08-13
> **hubie said:**
> Yes, but what is the nice trick to remembering all those archaic EMACS keystrokes???  :D

Besides, we all know that vi is the true way to go .....    :P


The same trick I use to remember to hit escape before doing something in vi. Practice.     :popcorn:

Sorry. You left yourself open to that one. I think all outside observers agree that BOTH sides of the vi/emacs religious debate know too many archaic keystrokes.

Vi (actually I used Vim or Viper-Mode) is terrific and I have played around with the Vim+R system developed recently, but I always seem to wind up gravitating back to EMACS.

EMACS has one killer feature -- org-mode. There ain't nothing else like it.

---

### Post by beew on 2010-08-13
akniss


> I don't mean to sound snide, but perhaps R is not a good software choice for you if typing "help.start()" is "a lot of troubles." R is really more of a language rather than a traditional statistics program (like Minitab or SPSS) and therefore to get to most of the information, it requires typing words rather than clicking menus. Its not better or worse, just different and it will take some getting used to.Yes, you are sounding snide. I have been using SAS and R in windows without any problem for sometimes. My question is not about how to use R but  is related to its Linux documentation or rather, its absence.

I also know help.start thank you very much but it links you to the R web site rather than showing you the manuals. What if I don't have internet access at the moment? On the website they  tell you there are manuals in the implementations but don't tell you how to access them. Now you can download the manuals from the website,--I also know that. But if the manuals are in the implementation already I shouldn't have to  download another copy. I can also get a copy from my windows installation too but that is not the point.

I also know all the help commands and ??? you posted. But help("manuals") is not legit command.

(Yes, I have downloaded the manuals as gunskta said. I just couldn't find it.)

---

### Post by beew on 2010-08-13
gunskta

Big thanks for the informative post and the non condescending  attitude towards us Linux newbies. I will try your suggestion when I go home.

I have rkward installed and also tried Rcmdr. But the terminal is actually fine by me. Even its windows interface is not really a GUI (but the menus are helpful). I am ok with that as long as I know where things are. :)

---

### Post by gunksta on 2010-08-13
I am going to avoid getting myself into the middle of most of this, 

[SIZE=2](I left my flame proof pants at home and I've already managed to get sucked into a discussion of EMACS v Vim in this thread.) [/SIZE]

but I should not that help.start() is a local function. It does not (on my Linux box) reach out to R on the interwebs. It will work just fine locally. I show it as being located at:

[http://127.0.0.1:15801/doc/html/index.html](http://127.0.0.1:15801/doc/html/index.html)

IIRC, Newish versions of R include an embedded web-server. I don't know which web-server and it only starts if you do the help.start(), AFAIK.

---

### Post by hubie on 2010-08-13
> **gunksta said:**
> (I left my flame proof pants at home and I've already managed to get sucked into a discussion of EMACS v Vim in this thread.)

Sorry, I just couldn't help myself.  :)  I've been teasing EMACS users for 20+ years now.  :D

What I've appreciated from this thread is that out of ignorance I never bothered to look up the local R documentation, so I've learned something new.  Long ago I had downloaded several PDFs and I have basically used them and the "?" command (mostly the "?" command, really).  I didn't even know about help.start().

---

### Post by gunksta on 2010-08-13
Yeah - well if it makes you feel any better, I tend to do the exact same thing -- read the PDF files that I have stored on my computer and use ?, and I knew about help.start(). For some reason, I never got into the habit of using it.

---

### Post by earlycj5 on 2010-08-14
This is one of the big reasons that I use rkward, the access to the HTML help files is so direct and easy.

---

### Post by memilanuk on 2010-08-14
One of the help feature that is included in R for OS X that for some reason isn't done the same way on R for Windows (sorry, don't have it installed on my latest install of Ubuntu yet for comparison) is the 'Vignettes' under the Help menu in the R gui.  Basically it opens up a menu window with a series of short pdfs on various topics - and you can get others from CRAN, such as HSAUR (Handbook of Statistical Analysis Under R), for example.  You can preview each one in a small viewer window, or open them fully in Adobe Acrobat or whatever your preferred PDF viewer is.  I was really disappointed to find this particular aspect of the R gui didn't make it over to the Windows port - from what I've heard, its a Mac-only thing for some reason.

---

### Post by gunksta on 2010-08-14
I did not know about HSAUR -- THANKS!

R is an enigmatic tool. There should be a sticky full of tricks and tips.

---

### Post by PGScooter on 2010-08-15
> **gunksta said:**
> I did not know about HSAUR -- THANKS!

R is an enigmatic tool. There should be a sticky full of tricks and tips.

gunksta,

I agree. I really like this page:
[http://pj.freefaculty.org/R/Rtips.html](http://pj.freefaculty.org/R/Rtips.html)
It doesn't give much intuition or structured teaching. But sometimes tips and trick are good enough by themselves!

---

