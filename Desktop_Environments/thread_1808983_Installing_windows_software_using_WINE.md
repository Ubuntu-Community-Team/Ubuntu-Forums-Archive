---
title: "Installing windows software using WINE"
date: 2011-07-21
forum: Desktop Environments
---

### Post by qaes on 2011-07-21
Hello Everyone

i have software for windows [installation exe file], and i need installed on Ubuntu 11.04, i am already install Q4Wine and wine windows program loader, when i start to run  my windows software using open with Q4Wine or wine windows program loader i get the error message as file attached:

Thank you
Qaes

---

### Post by MG&amp;TL on 2011-07-21
Oh dear. An uncaught exception usually means that the program found a problem, but there was nothing in the code to say what to do with the problem, so it performs the default "Uncaught exception" and terminates to prevent breaking something.

Short of editing the program files yourself, I don't see a solution. What program were you trying to use? Try re-installing wine. (you can get it from software centre.) 

:confused: Wine is still a work in progress, so there may be errors. Try  running something 'platinum-rated' on the wine app db.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

There's a list of practically all windows programs, with a rating.

---

### Post by Bucky Ball on 2011-07-21
Welcome. Some stuff works, some stuff doesn't. If you intend using mostly Windows programs I would stick with Windows. If you are looking to find Linux alternatives then go for it!

It is always best to check with WineHQ before attempting an install of Win software to check your chances (unless you are reporting your experiences with the untried and untested).

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Search there. Ubuntu is an alternative to Windows, it is *not* Windows and don't expect it to run every Windows program (I avoid Wine, myself). ;)

What is it exactly you are attempting to install?

---

### Post by qaes on 2011-07-21
Thanks MG&TL for ur kind reply

The software that am trying to install is a private application for my job

I will try ti re-install the wine 

Thank you
Qaes 
[COLOR=Black]_[]("http://ubuntuforums.org/member.php?u=1320682") _[/COLOR]

---

### Post by Bucky Ball on 2011-07-21
> **qaes said:**
> I will try ti re-install the wine 



Won't make any difference I wouldn't think. Re-read my post. ;)

---

### Post by qaes on 2011-07-21
Dear  Bucky Ball

I am really get sick from windows, everything working fine under Ubuntu except this application, i will try my best to switch to Ubuntu

Thank you
qaes
[]("http://ubuntuforums.org/member.php?u=504316")

---

### Post by Bucky Ball on 2011-07-21
What type of files are you expected to produce for work? You could possibly use a Linux program and save your work in the appropriate file format for employer requirements. They'd never know the difference, as long as your files will open in Windows. All the Open Office suite save to a Win compatible file format, for instance. 

I do all my stuff for uni on Linux and they'd never know the difference. ;)

---

### Post by MG&amp;TL on 2011-07-21
If the program is open-source, the likelihood is that it is already translated to linux. If it is open-source and does not have a linux option, you could always try downloading the windows source and compiling it using a linux compiler, and see what happens. I have never done this before, but one can always try. It works with the 'hello world' program I just ran on Windows and Linux, but yours is obviously considerably more complicated.

If it is not open source, then you have one easy and one hard option:

easy) find a linux alternative. May or may not be totally satisfying.

hard) See if you can find some instructions to modify the program, often there is basic instructions on the Wine app db. Depends really on the program. Is the program 'sensitive data' in some way, or have you just not told us yet? :P

---

