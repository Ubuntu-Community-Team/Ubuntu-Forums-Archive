---
title: "Project Template for R"
date: 2010-11-24
forum: Education &amp; Science
---

### Post by gunksta on 2010-11-24
Unlike languages like C or Python; R is a niche language. I would not use R to write a front-end to apt-get or to power a complex website. I use R to analyze stuff. That's basically it. Because my needs are narrow, I think it should be possible to write a useful template system for R (or at least my use of R). Writing a template for Python would be harder because there are so many things you can do with Python and they tend to have different needs.

I am apparently not the only person who thinks this way. Using the Ruby On Rails framework as inspiration, one developer has created [ProjectTemplate]("https://gith*******/johnmyleswhite/ProjectTemplate"). His effort is inspired by how Rails helps programmers get their projects done quickly and consistently. Ruby on Rails is similar to R in that it is a niche development framework (developing websites). Ruby is a general purpose language, but Rails is definitely a niche framework, thus many of the needs/structures can more or less be predicted.

Although I would never use R to write a complex website, it is similar in that my workflow and needs are predictable (more or less). Here's a quick outline of what I think an "average" R analysis project looks:

[LIST=1]
[*]Obtain a data-set from ________ (varies).
[*]Clean/structure the data. (Sed, Awk, Perl, etc.)
[*]Import the data into a database OR R.
[*]Write functions to do something to the data (plyr, etc.).
[*]Develop/Assess relationships, models, draw graphs, etc. (Not necessarily in that precise order.)
[*]Use Sweave, brew, odfWeave, etc. to create a report.
[*]Exit. Eat.
[/LIST]
Somewhere in there you should probably write a unit test or two.

Steps 4 and 5 are where we all (hopefully) spend the vast majority of our time. But, we usually have to do this other stuff too. For example - the other day someone sent me a stata file and I had no idea how to import it. I found my documentation for foreign() and figured it out. Now I have a code snippet tucked away to help me import those annoying (and rare) Stata files that I get once or twice a decade. This is where a template system would be ideal. This template could contain useful code snippets, like how to best use libraries like foreign to get work done. You use what you need and delete the rest. It could also include a sample LaTeX file and a template for odfWeave. New users find these things hard to do, but most of this stuff isn't that hard to do, it's just a little tricky to learn. Once you see how to do it, it's actually quite simple (especially brew).

I downloaded ProjectTemplate and played around with it and I think it has a lot of really good ideas and some solid code. But, I find it limiting and it is clearly aimed at programmers. The primary developer is clearly a competent programmer and likes the file structure we are all familiar with from Linux. These work well for Linux/Unix fans, but I could see this as confusing for someone coming from a Windows background. I also tend to collaborate with people who don't consider themselves programmers and I think the ProjectTemplate structure could feel overwhelming for these folks. I also don't like how it is designed to be very automated. For example, it is set up to find a data file in the data directory and immediately import it into R. This seems like a good idea at first blush, but I rarely do this. I tend to import PART of the data set and because of the way the data import routines are written, they are not conducive to someone going in and just yanking out the parts they don't want and putting more into it as appropriate. You can do this, but it's clearly meant to be more or less left alone. ProjectTemplate doesn't contain much sample syntax. It contains some automation, but not much to help you remember how to use useful libraries or what not.

To boil my criticism down to a single sentence: ProjectTemplate helps you develop a program. In contrast - I want something to help me develop a process AND to help me document what I do. These are different goals. 

I have a couple of ideas ideas, and I'm curious what a few of you think. 

**Idea # 1** - Develop a simplified ProjectTemplate which includes more sample syntax that can be easily adapted for each project. It would use a somewhat simplified directory structure (lib/ would be changed to functions/ for example) and it would include templates for tools like sed, awk, etc. It could also include sample code in functions to help people do things that they often do. For example - I often make tables with both numbers (counts) and percents. I would include the function that I wrote to make this easier and lets me skip over the usual steps required to do this.

**Idea # 2 -** Confession - I like Emacs - Scrap the complex directory structure of ProjectTemplate entirely. While this sort of structure makes a lot of sense for larger programs, for most R projects, it's over-kill. Instead, use org-mode to develop a layered template file, with lots of example syntax for things like how to import an excel sheet, etc. Let end-users keep what they want and delete the rest. There would still be a data directory and some example sed/awk stuff in there, but it would simplify things to just a handful of files, as opposed to a complex set of files and folders. But, it would only really be usable with org-mode, which is a definite disadvantage.

**Idea #3 -** It's more work but the sample syntax, etc. would likely be the same between ideas 1 and 2. It wouldn't be that hard to just do both and try to keep them in sync.

**Idea #4** - OK. I don't really have a fourth idea. Maybe you do.

---

### Post by gunksta on 2010-11-24
Two other thoughts. I will probably put together a more formal outline/example over the holidays and stick it up on GitHub.

It will tend to follow the [Google R Guidelines]("http://google-styleguide.googlecode.com/svn/trunk/google-r-style.html").

---

### Post by gunksta on 2010-11-27
Quick Update. I decided to use Emacs org-mode for the template. This was chosen for a couple of reasons.

[LIST=1]
[*]Using org-mode allows me to create a template that will encourage (force) the user to use something that at least resembles a literate programming style. For research/analytic work, this is especially important since often the WHY is as important as the HOW/WHAT.
[*]The org-mode function org-babel-tangle allows the user to EASILY create a set of scripts, separate from the org file. Thus, the resulting template will be usable by Emacs users and non-Emacs users alike. There is no need to maintain a separate non-Emacs version of the template. It can be generated automatically at any point.
[*]Distributing the template as a file, rather than a package, is interesting.
[*]Using org-mode makes it possible to create a flexible system that rivals TemplateProject in power and complexity, but is distributable as a single, well documented file.
[/LIST]

Project Name - template-r (Pronounced templater. I chose the name in case I later decide to fork it and produce template-python.)
Location - GitHub (I will provide the URL when I post this thing on-line.)

---

### Post by spinoza666 on 2010-11-27
Sounds very interesting Gunksta:)

I'm not familiar with a lot of the software you mentioned, so didn't quite get what you're up to, but have dabbled a bit with Emacs. Not a bad choice, but maybe not if you don't use R constantly. I use R heavily for a month or three, and then I might have a long break, which is quite typical for folks within research. I tend to forget how Emacs works in between :), and prefer something simpler, although it is very powerful. So maybe it would be better to use a simpler 'base' for your project? 

You mentioned code snippets. Is what you're planning perhaps a bit like SciViews-R? If so this sounds like a very goode idea as I like what SciViews-R is trying to do, but find it a bit underdeveloped. 

Anyway, excellent plan, and keep us posted!

---

### Post by earlycj5 on 2010-11-27
Watching with interest as I've been using ProjectTemplate recently.

---

### Post by gunksta on 2010-11-29
I stumbled onto a small problem/limitation in org-mode. I'm trying to see if there is a way to work around this or if I need to make a feature request to org-mode.

My idea for an analysis template would include lots of stub code that I use from time to time. Sort of like YaSnippet, but organized within the org-mode file. For example, I'd like to have code blocks called data-import-csv, data-import-sqlite, etc. Obviously, you will probably only use one of these in your analysis. For example, if your data is in a CSV file, you would use the first code block / function and the code block to help you with SQLite would remain untouched. It would also be fundamentally broken code and there is no reason to waste your time evaluating broken/unused code. Obviously, you could just delete the parts you don't want to use, but that makes the template harder to use and less flexible later. I would prefer to find a way where the user simply identifies which source blocks to use and which source blocks to ignore when doing a org-babel-execute-buffer command.

I would love to be able to do this with tags, like you can with EXPORT or do it with headers like you can with the tangle header. Not sure. I started a [StackOverflow]("http://stackoverflow.com/questions/4305497/using-org-mode-to-structure-an-analysis") thread. 

If anyone has any thoughts, post here or on SO.

---

### Post by gunksta on 2010-12-02
**Announcing --** **[TemplateR]("https://github.com/Choens/TemplateR") --**

It's currently at 0.01 or 0.02, depending on which tag you choose to believe.  :p  (I'm learning git as I do this, sorry.)  

Like I said in my OP - I am working on a template for R. The goal is to provide additional structure for analysis projects. Let's face it. We all have to import data, clean it up, do some stuff, and then export reports/plots/what-ever.

The basic workflow is completely predictable for most projects. [Project Template]("http://github.com/johnmyleswhite/ProjectTemplate"), which predates my attempt, is a separate attempt to solve the same problem. In fact, I fully intend to steal a few ideas from this project, especially in the area of designing unit tests. 

TemplateR is different in a number of ways:

[LIST=1]
[*]Users of TemplateR will be all but forced to organize their project as a Literate Program. The principles of Literate Programming and Reproducible Research are important to me.
[*]TemplateR is based on org-mode. I chose org-mode because it is the tool that I use the most when programming. It has a steep learning curve but, I promise _it_ _is_ _worth_ _it_.
[*]Project Template automates many things  such as data import. Rather than automate things by developing complex functions, TemplateR will provide users with chunks of tested code which can be easily re-worked/tuned. IMHO, this is a more flexible solution and will provide me with significant time savings by allowing me to skip the process of reinventing the wheel every time I want to do basic data processing.
[/LIST]
More details can be found in the TODO and README files @ github. If you use Emacs and R, feel free to download this and kick the tires. At this point, it is a proof of concept. It is not the greatest things since sliced bread, yet. It provides two simple functions to get you up and running.

[LIST=1]
[*]It can create a set of useful directories (data, plots, reports).
[*]It can test your existing installation to see if you have the necessary packages installed. Note - TemplateR doesn't actually need these packages, I just stuck them into the table for testing purposes. :D
[/LIST]
I am interested in any feedback. I am especially interested in feedback related to the over-all (limited) structure. Is it logical to you? What functionality would make it more useful? For example - I may implement a way for someone to maintain a canonical version of TemplateR, managed by Git or by manually downloading updates (uggh). I think it would be nice for this template to be able to create a new project folder and copy itself to the new folder and create useful sub-folders (data, plots, reports). This way you could maintain a copy of the system in one folder and "branch" it at will for new projects.

I'm getting ready to chase after the all-mighty PhD and I hope this decision gives me the flexibility to use R for more of my work (as opposed to the 'evil' that is SPSS). I would like to have a really strong product to use by next September. In fact - I am more or less going to arbitrarily set the 1.0 release date on the day I go back to school, unless there is a good reason to not do so.

---

### Post by gunksta on 2010-12-09
Changed the name from TemplateR to [LiterateR]("http://github.com/Choens/LiterateR"). The master branch still refers to TemplateR but the dev branch reflects the change. I changed the name to better reflect the project emphasis. I want a template system but I also want a Literate Programming Tool.

If anyone is interested, take a look at the dev branch. There's a little more in there. As I go forward, I am afraid that putting too many source blocks into the template will make it hard to use. I would like to provide example code for common tasks, i.e., import from .csv and .SAV files  - but there will be many such code blocks. Of course, on any given project the user won't use most of these and they will just sit there idle.

I'd like to get some feedback - would it be better to have example code in the template file or keep the template file simple and provide the example code in a separate file.

Suggestions? Comments?

---

### Post by akniss on 2010-12-10
> **gunksta said:**
> I'd like to get some feedback - would it be better to have example code in the template file or keep the template file simple and provide the example code in a separate file.

Suggestions? Comments?

It seems like this decision will depend on your target audience. My opinion is the people most likely to use this sort of thing will be people who are already somewhat familiar with R, and who will know the basics of doing what they need to do with their data (earlycj5 and me for example). For this crowd, it seems like it would be best to have the example code in a separate file. Personally, I get annoyed with myself when I've got too much commented out code in a file, because when I go back a year later, its more difficult to figure out exactly what I've done.

On the other hand, as the project progresses, and the target audience perhaps becomes more broad, the idea of having a larger amount of example code blocks in the template file makes more sense.

Just my 2 cents.

---

### Post by gunksta on 2010-12-10
I've been thinking more or less the same thing.

Added benefit - this makes it much easier to get to a usable release.  :D

It won't take more than an hour or so to clean up the current dev branch. Last night I played around with the idea of adding a few files.

README.org -- Basic intro to the analysis, etc.
Analysis.org -- This would be a simplified version of the TemplateR/LiterateR file.
Report.org -- Basic structure, which imports Analysis, capable of serving as a template for a basic report. This would be a very simple file and would really only include the header information necessary to force org-mode to import Analysis.org.

The folder structure would stay the same. Data will be stored in data and reports (PDF, Excel, etc.) would be stored in reports/.

---

### Post by earlycj5 on 2010-12-10
> **gunksta said:**
> I've been thinking more or less the same thing.

Added benefit - this makes it much easier to get to a usable release.  :D

It won't take more than an hour or so to clean up the current dev branch. Last night I played around with the idea of adding a few files.

README.org -- Basic intro to the analysis, etc.
Analysis.org -- This would be a simplified version of the TemplateR/LiterateR file.
Report.org -- Basic structure, which imports Analysis, capable of serving as a template for a basic report. This would be a very simple file and would really only include the header information necessary to force org-mode to import Analysis.org.

The folder structure would stay the same. Data will be stored in data and reports (PDF, Excel, etc.) would be stored in reports/.

It sounds like an interesting approach.  However, since I'm not an emacs user I'm left out. Not complaining, just saying. :)

I'm watching ProjectTemplate right now as John is implementing some changes in the next release of it.

Currently both of you are headed in the direction I need to go, but I've been modifying ProjectTemplate superficially to suit my needs.

I might dig into the source code and make my own changes to suit my needs.

That's the beauty of opensource!

---

### Post by gunksta on 2010-12-10
Doh! Not trying to leave anyone out but yeah, if you don't use Emacs, my approach is essentially useless to you.

I've jumped back and forth between Vim and Emacs more times than I can count. That's why I maintain config files for both on Github.  :-)

In the end, I'm an Emacs user because of org-mode. It's just too darned useful. I've noticed that there is an effort to re-implement org-mode for Vim, but I suspect it will take years for them to catch up with the Literate Programming aspects of org-mode. If they do. I can see Vim users arguing that NoWeb, SWeave make it redundant. Which it is.  :P

---

### Post by earlycj5 on 2010-12-11
I've been making good use of Sweave this week at work.

---

### Post by Br_Andy on 2011-10-25
Hi all,

  Are either of these projects - ProjectTemplate or LiterateR - still alive?  They both seem to provide some value and I've used ProjectTemplate on and off in the past few months but wonder if they will make it past their first birthdays as development seems to be minimal.  That said, I'd love for these to become really usable stable tools as I struggle with standardization a lot in R.

  If any of the authors are around I'd love to know if there's any planning or development going on.

Thanks!

---

### Post by gunksta on 2011-10-26
To answer this question we must first carefully define "alive". I gave up on use org-mode for a template system. It was too complicated and using it was a complete PITA. I think it is fair to say it is dead. My original project is still around, although I haven't worked on it in quite a while. I still use bits and pieces of it though.

[ProjectTemplate]("https://github.com/johnmyleswhite/ProjectTemplate") is still under active development and may be the most mature / complete option. My reservations regarding ProjectTemplate are that it is relatively complex and because it is an R package there I could imagine a scenario where backwards compatibility becomes an issue. 

But, it is an actively developed project which is more than I can say for my efforts.

If you have some ideas regarding an R template, I'm interested.

---

