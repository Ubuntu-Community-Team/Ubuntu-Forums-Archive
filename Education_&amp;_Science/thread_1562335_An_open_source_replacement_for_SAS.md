---
title: "An open source replacement for SAS"
date: 2010-08-27
forum: Education &amp; Science
---

### Post by beew on 2010-08-27
Hi, I am wondering if there is an open source program that can replace SAS in handling data cleaning, database updates and functions like that. So far we are only using SAS base. I know R can be used in place of SAS as a statistical package but I am not sure if R is as capable in handling database and manipulations involving multiple data files ( about a few hundred thousands rows for some of them) I also use a lot of macros for these purposes and to my best knowledge R has no macro facility, there may be other ways to implement similar functionality but I haven't looked into it yet.

Thanks.

P.S. It has to have a windows version  since we use windows at work.

---

### Post by gunksta on 2010-08-27
> **beew said:**
> Hi, I am wondering if there is an open source program that can replace SAS in handling data cleaning, database updates and functions like that. So far we are only using SAS base. I know R can be used in place of SAS as a statistical package but I am not sure if R is as capable in handling database and manipulations involving multiple data files ( about a few hundred thousands rows for some of them) I also use a lot of macros for these purposes and to my best knowledge R has no macro facility, there may be other ways to implement similar functionality but I haven't looked into it yet.

Thanks.

P.S. It has to have a windows version  since we use windows at work.

Whether or not R is an adequate replacement or not for what you want to do is probably a fairly complicated question, but I'll throw out a few comments.


[LIST=1]
[*]R runs on Windows, Mac and Linux and a few others.
[*]R is a scripting language designed for statistical analysis. To say that it does not have "macro" facilities is simply incorrect. It is a programming language. Macros are the easy part.
[*]It is capable of connecting to any database you want. Postgres, MySQL, SQLite, MS SQL Server, etc. There are direct systems for MySQL, Postgres and SQLite and can connect to the others via ODBC or JDBC. Unlike SAS, database functionality is not built in. This is a Unix style decision. In Unix we usually combine smaller tools which are good at "one thing" to build complex systems. Windows programs tend to be "the whole kitchen sink in one executable". Neither approach is necessarily "wrong" but they are different. FYI - SAS uses Firebird as an embedded database, which is an open-source project.  :-)  See, you've been using OSS for years already!
[/LIST]

---

### Post by PGScooter on 2010-08-29
I think you have valid concerns as far as if R can handle very large databases. Revolution Analytics is software which is based on R and can handle large databases. The enterprise version does cost money, but comes with support and a few extras:
[http://www.revolutionanalytics.com/](http://www.revolutionanalytics.com/)

As for macros, what exactly do you mean by a macro? It can mean a lot of different things. I would be very surprised if R cannot do whatever you mean by macro, but let's be sure.

---

### Post by Naomi99 on 2010-08-31
The free replacement for SAS is called DAP. [http://www.gnu.org/software/dap](http://www.gnu.org/software/dap)

Compared to other free stats replacement progs it has a long way to go. However it's a start and can read most SAS files.  Hopefully it will get further developed so as to completely replace SAS, just like PSPP does for SPSS.
:D

---

### Post by maggoteer on 2010-09-02
Given that R is (mainly) a gui-less, command line driven, interpreted statistical programming language, the question of whether it can run "macros" is odd, perhaps nonsensical. AFAIK, R will not run you SAS "macros" as is - you will have to rewrite them in R. But it IS a full blown statistical programming language and thus fantastic for automating (and documenting, especially via Sweave!) complete statistical analysis.

In addition to the "main" R program, you will want to look at the vast collection of packages written in R located here, where you might well find well written code that does exactly what you want/need:
[http://cran.r-project.org/](http://cran.r-project.org/)

It is fully capable of interacting with the underlying operating system, eg opening files and reading in data, etc.

Not having used the feature, I cannot comment on the ease with which it interacts with databases - but people I know and trust are quite happy with it's abilities.

---

### Post by gunksta on 2010-09-03
> **Naomi99 said:**
> The free replacement for SAS is called DAP. [http://www.gnu.org/software/dap](http://www.gnu.org/software/dap)

Compared to other free stats replacement progs it has a long way to go. However it's a start and can read most SAS files.  Hopefully it will get further developed so as to completely replace SAS, just like PSPP does for SPSS.
:D

Just as a head's up, PSPP is not a drop-in replacement for SPSS, unless your needs are really basic. It can read SPSS files and do some basic stats, but the output is decidedly less flexible that SPSS (and I don't like SPSS' output either) and more complex analysis is not always possible (yet).

That said, I wish the developers of both tools good fortunes, because I would love to have access to a drop-in replacement for SPSS when the client doesn't want me to use R.

---

### Post by myotis on 2010-09-06
> **gunksta said:**
> That said, I wish the developers of both tools good fortunes, because I would love to have access to a drop-in replacement for SPSS when the client doesn't want me to use R.

I'm intrigued, why would a client not want you to use R?

Graham

---

### Post by gunksta on 2010-09-06
> **myotis said:**
> I'm intrigued, why would a client not want you to use R?

Graham

In a nutshell -- I consider myself a social worker / social scientist and my business card claims I am a policy analyst; but at the end of the day, I work for a consulting firm. We specialize in human services such as child welfare, elder care, etc. As a consultant, I sometimes (often)  have to do what I am told to do, rather than what I want to do. In the context of this discussion, it is important to remember that SPSS (now PASW) is the 800 pound gorilla among social scientists and government researchers (at least in the US). I should also note that they like to use Access (dear god) and SQL Server (hey, it's better than Access).

I am the only analyst in the company comfortable using R for anything more difficult than a glorified calculator. Many of my co-workers prefer the annoying point-and-click goodness that comes attached to SPSS. There are a couple of people I can give my scripts to and they can use them, but for most of my co-workers, R lacks the vanilla-sugary frosting necessary for me to be comfortable telling them to:

[LIST=1]
[*]Install it,
[*]Run a prepared script.
[/LIST]
Thus -- If a co-worker or the client must be able to run what I write, I usually have to write it for SPSS. This is especially true when my "end user" is a client. I can cajole or bully my way into getting a co-worker to install R. The fact that I am also our IT guy helps here. But, I can't ask a government client to install and use a program he/she is not familiar with. And I just checked -- This is a bad time to be out of a job. 

Fortunately for me, most of these "analyses" are relatively trivial and PSPP is advancing rapidly enough that I can do more and more of what I need to through PSPP. The big stuff usually requires context / written analysis / accompaniment so I just use R and save myself the headache of trying to do anything even remotely complicated in SPSS/PSPP. All that being said, I just upgraded my home machine (the one I am on right now) to 10.10 and noticed that PSPP/psppire is still 0.6.2. I thought they had released 0.7.x.

Rats,  I was hoping to avoid compiling that one by hand.

---

### Post by myotis on 2010-09-07
> **gunksta said:**
> In a nutshell -- 



Thanks for the useful response. I fully understand  the position.

Graham

---

### Post by PGScooter on 2010-09-09
> **gunksta said:**
> In a nutshell -- I consider myself a social worker / social scientist and my business card claims I am a policy analyst; but at the end of the day, I work for a consulting firm. We specialize in human services such as child welfare, elder care, etc. As a consultant, I sometimes (often)  have to do what I am told to do, rather than what I want to do. In the context of this discussion, it is important to remember that SPSS (now PASW) is the 800 pound gorilla among social scientists and government researchers (at least in the US). I should also note that they like to use Access (dear god) and SQL Server (hey, it's better than Access).

I am the only analyst in the company comfortable using R for anything more difficult than a glorified calculator. Many of my co-workers prefer the annoying point-and-click goodness that comes attached to SPSS. There are a couple of people I can give my scripts to and they can use them, but for most of my co-workers, R lacks the vanilla-sugary frosting necessary for me to be comfortable telling them to:

[LIST=1]
[*]Install it,
[*]Run a prepared script.
[/LIST]
Thus -- If a co-worker or the client must be able to run what I write, I usually have to write it for SPSS. This is especially true when my "end user" is a client. I can cajole or bully my way into getting a co-worker to install R. The fact that I am also our IT guy helps here. But, I can't ask a government client to install and use a program he/she is not familiar with. And I just checked -- This is a bad time to be out of a job. 

Fortunately for me, most of these "analyses" are relatively trivial and PSPP is advancing rapidly enough that I can do more and more of what I need to through PSPP. The big stuff usually requires context / written analysis / accompaniment so I just use R and save myself the headache of trying to do anything even remotely complicated in SPSS/PSPP. All that being said, I just upgraded my home machine (the one I am on right now) to 10.10 and noticed that PSPP/psppire is still 0.6.2. I thought they had released 0.7.x.

Rats,  I was hoping to avoid compiling that one by hand.

Great explanation, thanks for sharing. I wonder if this will change in the future or not. Whether the change will come from people becoming more tech savy nd more friendly with programming and not clicking or perhaps R will develop a better GUI (via Revolutions?). It will be interesting to see.

---

