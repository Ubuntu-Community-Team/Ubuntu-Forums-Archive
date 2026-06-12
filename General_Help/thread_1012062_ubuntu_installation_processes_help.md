---
title: "ubuntu installation processes help"
date: 2008-12-15
forum: General Help
---

### Post by l0fls on 2008-12-15
Hi. I am a intermediate linux user (5 1/2 months August till present)
and I have a somewhat decent understhttp://www.sellingcr.com/costa-rica-blog/69-blogs/325-the-costa-rica-margayanding of ubuntu. one thing I get completely lost in is the installation of programs. to best address my lack of knowledge in this area Im just going to list some questions and I would really appreciate it if some really experienced users could lay down and answer for me and just explain it for me so I could understand because for me to learn I need to understand.

When you download source code and ./compile what packages are needed to do this because i get an error every time?!?


also when you sudo apt-get install Amarok is it the same thing as going to synamptic package manager and slecting it like that?!?!

also when i try to install progrsams and synamptic and the terminal cannot find it why is this.

also is their a completle list of software sources for synaptic

also if somone can explain how the entire system works so i can figure this all out

thanks in advance

ps i specifically asked for " expericned users" so if your kinda t3h n00b just kinda keep it to your self sorry :(

---

### Post by oaxacamatt1 on 2008-12-15
Hi 10fls,
I like your model of the week. ;}  Although I am not an 'expert' I have enough knowledge to chime in and I'm sure others will chime in later.

**When you download source code and ./compile what packages are needed to do this because i get an error every time?!?**
The basic set of software that you need to compile can be derived from the command line. eg '**sudo apt-get install build-essential**'  This is a set of commonly used programs tht can help you install/compile progs.  But this is not the ONLY software that you need.  You may find that you will need more.  Some funky software needs funky libraries, etc.  So when you start to compile look carefully at the error produced and then open up Synaptic and search for this additional software.  Or you can go to your command line and use '**sudo apt-get search (program name)**'  The program name can use wildcards like *,? eg '**sudo apt-get search libcs***'

**also when you sudo apt-get install Amarok is it the same thing as going to synamptic package manager and selecting it like that?!?! **
YES.

**also when i try to install programs and synaptic and the terminal cannot find it why is this.**
There could be several reasons why you can't find a program.  One is: you called it the wrong name OR you don't have synaptic set up to look in the right or all the repositories.  

**also is their a complete list of software sources for synaptic**
Is there a list of all the software in synaptic.  What you see is what you get.  This question/answer kind of goes back to the repositories (from above) that is chosen...

**also if someone can explain how the entire system works so i can figure this all out**
Ahhhh! Grasshopper, you want the answer to the biggest question ever.  ...Try and take this stone from hand...

Goodluck,
Matt

---

