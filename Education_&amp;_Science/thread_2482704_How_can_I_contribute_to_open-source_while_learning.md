---
title: "How can I contribute to open-source while learning CS?"
date: 2023-01-08
forum: Education &amp; Science
---

### Post by smith73 on 2023-01-08
I am teaching myself CS and in a couple or more months (though also basically now) I'd be searching for open-source projects to apply some programming skills (Python, C/C++ at least). I'd like to start with minor fixes or improvements to non-OS programs like Audacious or pdf readers etc. 
Is it possible to implement that? If yes, then what's the routine?

---

### Post by TheFu on 2023-01-09
> **smith73 said:**
> I am teaching myself CS and in a couple or more months (though also basically now) I'd be searching for open-source projects to apply some programming skills (Python, C/C++ at least). I'd like to start with minor fixes or improvements to non-OS programs like Audacious or pdf readers etc. 
Is it possible to implement that? If yes, then what's the routine?

Every project is a little different and does things slightly differently.  

* Find a project that interests you, these are on gitlab or github usually. There are other places, but those 2 are the biggies.  
* Watch their discord/email/IRC for a few months and get to know the players in the project team. 
* Read their FAQs.
* Go through their issues list, see if any issues are small enough and within your skillset.  
* Look over any documentation the project might have for coding standards and "contributing". Follow their layout, their indentation and coding style.  * Not all code is excepted, especially if it doesn't follow the project teams coding standards.  
* Make yourself useful.  That can mean helping with documentation, translating to another language, coding, writing a fresh install guide and/or opening issues for things in the existing project that seems wrong.  And when/if you do fix some code or answer questions in IRC, ensure that it doesn't break anything else or isn't incorrect.  
* If the project team thinks it is a good idea, you might create an IRC bot that answers the most common 50 questions for a specific project asked by noobs. I'd assume discord has something similar.  
* Many projects will include test cases with code changes, so you'd want to provide complete test coverage with your code as proof, using whatever testing method that specific project already uses.

Often, CS has very little to do with programming.  I've known people with PhDs in CS who couldn't code "Hello World" in any language. I'm 100% serious.   99% of coding doesn't require any fancy CS learned skills, unless the CS programs have massively changed.  In general, college/University level coding projects don't cover 90% of what a programmer needs to know to work in a team like we do in the real world.  Understanding DVCS (git) and how it works in a team environment is key.  Git isn't really a central repo. It is mostly a repo for individuals and it is purely a social agreement between humans for which people/persons "own" the primary, public, repo used by outsiders.  I suspect most F/LOSS projects use git and follow similar methods, but there are always strange methods based on the project team. As someone new, you'll not have sufficient experience to know what is "best practice" and what is a personal preference made by a project leader until you've seen how a few F/LOSS teams work.

If you need a primer for using git, I can recommend a Talk by Randal Schwartz on Git. [https://youtu.be/8dhZ9BXQgc4](https://youtu.be/8dhZ9BXQgc4) This explains the social agreement in a clear way, which is very different from the way non-DVCS systems work.  It is a bit scary to corporate types, since it feels like their corporate repo isn't really "the master" repo ... and it isn't, except that everyone on the team agrees to use it that way.  Git leverages normal ssh, ssh-keys, file and directory permissions, plus a nifty, fast, VCS that handles branching and merges really, really, well. If you never got to deal with SCCS, RCS, Visual SourceSafe, CVS, SVN, and 5 other version control systems, you don't know how lucky you are.  

Even when I'm programming by myself with nobody else ever going to see the code, I use a VCS.  There are some things that I love about git, but there are some things I don't like at all.  For example, I miss the RCS $Id$, which can show exactly which version of each file is used in a project regardless of language.  That is extremely useful to be able to pull from a deployed binary sometimes.  The git expansion of $Id$ into a SHA string just isn't as useful to a human.  Fortunately, rcs is still available and works fine, though it doesn't handle branches and merging nearly as nice.

---

### Post by johnisold on 2023-02-22
I want to learn javascript and css. What should I start with?

---

### Post by umangwah67 on 2024-02-06
heyy
it is possible,  To contribute to non-OS programs, you can start by checking their repositories on platforms like GitHub, then look for issues labeled as 'beginner-friendly' to find tasks suitable for beginners.

---

### Post by bijayalaxmi1808 on 2024-03-02
Showing interest to contribute to the FOSS community is the very first step and is really awesome.
If you are confident on contributing to the code base that's great otherwise you can also start with contributing to the documentation or help text for a command line app (if it is available that way).

I will suggest you to work with open source projects that you use on a daily basis. That will give you an idea of the app that you are using about the usage, if some bugs, you can search and try fixing it by yourself and submit the patch if successfully fixed.

There are not hundreds or thousands, probably millions of Open source projects live on GitHub, GitLab or other public repos.

Once you start, it's a looooong way to go.

---

### Post by grieda on 2024-06-20
[COLOR=#000000]Absolutely, you can definitely contribute to open-source while learning CS. Start by checking out the repositories of the projects you're interested in, like Audacious or pdf readers, on platforms like GitHub. Look for issues labeled "good first issue" or "beginner-friendly." These are perfect for newcomers.[/COLOR]
[COLOR=#000000]First, fork the repository and clone it to your local machine. Then, set up the development environment as per the project's documentation. Start by fixing minor bugs or adding small features. Don't hesitate to ask questions in the project's community or forums&#8212;they're usually very welcoming to new contributors.[/COLOR]
[COLOR=#000000]Also, check out resources like GitHub's "First Contributions" guide. It walks you through the process of making your first pull request step-by-step. [/COLOR]

---

### Post by coffeecat on 2024-06-22
Thread off-topic for this sub-forum, OP has not returned for over a year, and thread necromanced by a spammer a few months ago. Closed.

---

