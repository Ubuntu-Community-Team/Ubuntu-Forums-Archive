---
title: "Qualitative text analysis"
date: 2008-05-14
forum: Education &amp; Science
---

### Post by Mr Al on 2008-05-14
I'm about to embark on a long term data processing project, and I'm trying to make a decision about what software to use. I'm going to be dealing with a lot of text files. I'm experienced with Nvivo, but I really want something that runs on Ubuntu/Linux/UNIX. Has anyone got any suggestions or recommendations?

_What I need_

Essentials:

- text coding - Basic coding of text. Retrieval of coded text.
- categorisation and/or tagging of documents/files.
- text search.

Nice to have:

- embedded notes and memos
- some way to attach notes to codes/tags
- a nice way to browse and organise codes

More general requirements:

- stability - I need the solution to work in years to come.
- transparency - I need access to my data for a long time to come. I want to be able to get that data in and out. My preference would be for a transparent file format.

I've tried to install Weft QDA to no avail. Though I like the look of it, I'm a little hesitent to trust a project which (it appears) only has a single developer. I'm going to be putting a lot of my own time into this analysis, I don't want to find that I can no longer run the software which will enable me to access that work. My current installation problems with this software only reinforce this reservation.

I am wondering whether there is some kind of ad hoc solution which I could use - say, a combination of spreadsheets, file directories, desktop search, file tagging (maybe through Leaftag?). The only problem there would be with the actual text coding. For that I'm seriously considering coming up with my own solution through a combination of either a markup language or a database to record coding, along with some basic Python scripts (I have very rudimentary Python skills) for retreiving the text.

Scripting my own solution does seem a bit excessive, I know. Doing it this way would have its own advantages however - I'd have total control of the data and it would be a long term solution.

What do people think? Does anyone have any advice?

---

### Post by GSBoomer on 2008-05-14
Check out [http://tamsys.sourceforge.net/](http://tamsys.sourceforge.net/)

---

### Post by Mr Al on 2008-05-16
Thanks for the suggestion. I have tried TAMS in the past, but didn't really warm to it. The interface seems odd and markup a bit clunkey (that's just a first impression, mind!). I will have a more thorough look when I get chance.

If anyone has any experience of TAMS, I'd be keen to hear about it.

Am still increasingly thinking that my own solution could be the most effective. The first step will be to come up with an XML schema, then I'll write some Python scripts to retreive the coded data. It shouldn't be too hard, and it will be a neat, long lasting solution.

---

### Post by buffybot5 on 2009-03-18
Hey Mr Al-
Any luck since this post? I'm looking for an NVivo alternative myself for my dissertation research.

---

### Post by Mr Al on 2009-03-18
Yes, as a matter of fact! You can find the code and post bugs at the Launchpad page: [https://launchpad.net/labels](https://launchpad.net/labels). Just don't be too critical of my coding skills! ;)
 
The system works (I've used it successfully for analysis projects). It uses a command line interface though, so it's a bit labour intensive compared with gui applications. There's a bit of documentation in the README that might help, if you decide to give it a go.

---

### Post by JTtheGeek on 2010-10-26
I'm one of the developers on this, so please excuse me if this comes off as a pitch.  [Dedoose]("http://www.dedoose.com") is a web-based qualitative text analysis as well as a mixed method (qualitative and quantitative) research tool.  First month is free, and it's about $11/month after that.   Check out the intro video for a full idea.    It offers some ridiculously powerful data visualization, drill-down, and codification not found anywhere else.    Hope this helps someone.

---

### Post by cantillon on 2011-12-01
I finally found a functional qualitative analysis software for linux! It's called RQDA. It's very easy to use and it works as an R package. You can find more info here: [http://rqda.r-forge.r-project.org/]("http://rqda.r-forge.r-project.org/") and here: [http://rqda.r-forge.r-project.org/documentation_2.html#manual]("http://rqda.r-forge.r-project.org/documentation_2.html#manual").

I tried to use WeftQDA and TAMS Analyzer before, but I could never make them work. RQDA works without any problem. Here you can see how I installed it in Ubuntu 11.04: [http://linuxatuva.wordpress.com/software/]("http://linuxatuva.wordpress.com/software/")

---

