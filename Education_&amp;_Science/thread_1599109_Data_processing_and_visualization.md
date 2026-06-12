---
title: "Data processing and visualization"
date: 2010-10-17
forum: Education &amp; Science
---

### Post by viandante on 2010-10-17
Hi people,

I am working on a project where I need to process lots of data. I would like to share with you some thoughts and ask for some help.

First the thoughts.
I find the mixture of python, R and Sqlite quite awesome. There is an amazing, yet not well known, python module which allows passing commands to R just as strings. The module is called pypeR, give it a shot. 
Then, Sqlite is just simple and powerful. The only complain is that there is no decent gui to view data and run queries on it (maybe someone is interested in writing with me a simple one in python??). However, this is just a small problem.

_Some thoughts on the closed software_
I also want to say that if I got some results these first 3 weeks of my project is for to those programs. Me and my colleague tried to use SPSS, but it could not import those data (that are not clean enough for SPSS ??). Excel (because data are provided in xls, so bad...) messes up everything and it is too basic in reading csv. In order to import a csv in acces we had to save it in xls from openoffice...

Some thoughts on output rendering
Finally, those days I have been looking at TiddlyWiki to render the output. 
Let's say that your script produces many graphs and statistics in text files. Then,you could use TiddlyWiki to see all those files without having to open them, just browsing them on Firefox!

_Some issues_
Well... the main issue is that I cannot find a community which is working in this kind of stuff. The point is also that I am a business/economics student and in my environment things are done either in excel or with fancy-looking gui programs (SPPS, Stata, etc.).
So, the advice I would like to ask is: do you know anyone or any community/forum where I can find some people like me (not too experienced, not to basic)? Maybe some people that use R, sqlite and python either?

Let me know!

---

### Post by gunksta on 2010-10-17
Community -- [Stack Overflow]("http://stackoverflow.com/questions/tagged/r?sort=newest&pagesize=15") (This link should take you to the R related posts.)

-- SQLite Tools --
[SQLiteman]("http://sqliteman.com/")
[SQLite Manager (]("https://addons.mozilla.org/en-US/firefox/addon/5817/")Works with FireFox and directly with XUL) 
[Squirrel]("http://squirrel-sql.sourceforge.net/") (Tends to be my personal favorite, mostly because it works so well with other databases that I have to work with.)

---

### Post by dnewkirk on 2010-10-20
Another thought is to venture into some of the bioinformatics-related lists. Python, R, and SQlite are very common tools for manipulating biological data these days, and while the problems aren't the same, many of the statistics and techniques for visualizing data can be relevant. If you go to the cran website, they have a number of list serves for R (get the daily digest though, unless you like to see your inbox overflow!). Heck, irc.freenode.org has channels for each, and I've picked up some good information from people in all three.

---

### Post by gunksta on 2010-10-21
A couple of other thoughts. Starting a new project, and choosing the right tool(s) can be a daunting task.

Have you ever heard of [SOFA Statistics]("http://www.sofastatistics.com/home.php")? It is a FOSS stats package, written in Python and uses SQLite to store your data. For data shaping/manipulation, you would use SQLite and you will want to use a separate tool for managing the database. In my very limited experience with SOFA, it's data management facilities are not real thorough. However, once you get the data shaped, SOFA offers you a reasonable set of useful tests and tries to help you understand which test(s) are appropriate for your data. Unlike R, SOFA Statistics is GUI oriented. As an added bonus, because you data is stored in a SQLite file, you can also use R if you later discover you need to run a test or do something NOT supported by SOFA. It is easy to connect R to SQLite files. (SQLite has become my preferred data management tool.) The graphical output produced by SOFA Statistics looks really nice and it produces all reports in HTML, simplifying integration with Tiddly.


Going back to R --
Not sure what you were thinking to do with TidllyWiki, but if you read through the documentation for R, there is a beautiful trick called Sweave, where you can have R run through a LaTeX document which includes embedded R syntax. R will replace the syntax with LaTeX/pictures, allowing you to automate reports.

I have done the same thing with odfWeave, which is the same idea, but works with OpenOffice.org files (.odt) rather than LaTeX files.

Very very powerful stuff. Since you mentioned a wiki, you can use Sweave to produce HTML, PDF, etc. It's an option. SOFA is probably easier to use but R is more powerful. Look through SOFA's documentation. If it supports the tests you need, it is probably a good option for you and I love that it doesn't lock you down into a unique or hard to use data file.

---

### Post by SeijiSensei on 2010-10-21
One other excellent, free package is GNU [**gretl**]("http://gretl.sourceforge.net/") available from the repositories.  It provides a wide array of estimation tools for regression and time-series analysis. Along with various least-squares algorithms are ones for binomial and multinomial probit and logit and other more arcane maximum-likelihood methods.  It also supports time-series estimation techniques like ARMA.

In an economics setting, I'd think gretl might be your best bet.  It imports directly from Excel and other formats like CSV and has an intuitive GUI.

---

