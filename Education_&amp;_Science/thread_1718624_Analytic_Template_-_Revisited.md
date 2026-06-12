---
title: "Analytic Template - Revisited"
date: 2011-03-31
forum: Education &amp; Science
---

### Post by gunksta on 2011-03-31
A couple of months ago, [I posted a thread]("http://ubuntuforums.org/showthread.php?t=1630031") about my interest in creating a template for doing analytic work. I was inspired by efforts like [ProjectTemplate]("http://github.com/johnmyleswhite/ProjectTemplate"). While I like the idea behind ProjectTemplate, I don't like the idea of turning the template into a R library. Plus, I realized that because I often use other languages; ProjectTemplate was limiting in that it provided a structure for R projects, but would not provide the same level of structure when using other languages.

As a fan of emacs and the all-in-one-wonder-tool org-mode, I used org-mode as a development platform for my first template attempt. After putting together an incomplete example, I tried to use it. In the end, I decided it was awful. Turns out that org-mode, is not a good choice for a template system.

[LIST]
[*]Limited support for multiple RDBMS. While org-mode rocks out with SQLite, it doesn't handle other databases as well. I often have to use other databases.
[*]Complexity - I wound up with too many buffers. Sadly, while org-mode does allow you to name a code segment, this name is not reflected in the buffer created to independently edit the code found in the embedded code segment. It was difficult to quickly shift from one code segment to another.
[*]Limited opportunity for collaboration. I like emacs and I like org-mode. But, using these tools as the basis of the template limits the number of people who will be interested in the template and it limits the number of potential contributors.
[/LIST]

I decided to retreat, regroup and come at this from another angle. Hopefully, a less oblique one. In rethinking my approach, I realized that, like ProjectTemplate, I was too focused on R. Most data analysts use a suite of tools to get the job done, not just R.

For example, last week a client sent me a 1200 MB text file. I used sed and awk to clean up the text file. Then I uploaded the table to a SQL Server running in Maine (I'm in NY). I then created some new views, using this new table and some pre-existing tables. Eventually, I used R to download a couple of the views and actually run my report. The new [XLConnect]("http://www.mirai-solutions.com/site/index.cfm?id_art=66328&actMenuItemID=30058&vsprache/EN/Mirai_Solutions___XLConnect.cfm") extension for R is absolutely brilliant. This project involved sed/awk, SQL, R and a Java tool (XLConnect). I could be wrong, but I suspect most data analysts wind up doing something similar in that they use a variety of tools to get the job done.

So, I am trying to wrap my head around how to create a "Analytic Template" that is designed and structured for data analysis. 

Why?

Well, I would like for my own project to be more consistent with one another. 

The idea is to provide a common structure for analysts using the template. By hosting it on GitHub, it should be easy for individuals and groups to take the outline and fork it to create more specialized tools.

**Goals / Ideas**

[LIST]
[*]Present the end-user with a consistent structure that helps the user integrate scripts and programs written in a variety of languages.
[*]Provide a limited set of built in tools, to help the user share the code with other users. For example, I would like to create some tests and functions that will make it easier to install needed R libraries, making it less likely that a distributed analysis will fail when run on another computer. I also have a simple R function that uses Ubuntu's notification framework to tell me when annoyingly long steps have completed.
[*]Provide a set of basic templates to help users write consistently structured code.
[/LIST]
**Questions**
I know from first hand experience that there are some very clever people on this forum. What would you want from a template? While I personally tend to use R the most, I'm interested in making something that is useful for people who use a other common languages. For example, I know bash, python and java are often used by data analysts.

[LIST]
[*]What would you like to see in a template system for data analysis?
[*]What languages should it support explicitly by providing default folders, templates, etc.? Obviously, other languages can be added by the end user.
[*]What functionality should be built into the tool? (This functionality will necessarily be connected to the language being used, since a R function would not automatically be useful for someone using Java)
[*]How would you structure such a template?
[*]Other thoughts / comments?
[/LIST]

**Basic Structure**
Right now, I have a few things laid out, but not something that is really worth giving to anyone else. In a nutshell, I am thinking of a structure along the following lines.

[LIST]
[*]AnalyticTemplate/  (Root Folder)
[LIST]
[*]*.Rprofile*
[*]*.RData*
[*]*README*
[*]*TODO*
[*]data/
[LIST]
[*]For storing actual data AND YAML definitions
[/LIST]
 
[*]doc/
[LIST]
[*]Project documentation, license, etc.
[/LIST]
 
[*]graphs/
[LIST]
[*]Graphs, pictures, flowers, etc.
[/LIST]
 
[*]python/
[LIST]
[*]Any necessary python libraries or functions and a selection of templates.
[/LIST]
 
[*]R/
[LIST]
[*]Any necessary R libs, functions and a selection of templates.
[/LIST]
 
[*]reports/  (self explanatory)
[*]SQL/
[LIST]
[*]Any .SQL files for queries executed directly on the database server and some basic templates.
[/LIST]
 
[*]tests/
[LIST]
[*]Any and all unit tests. You are using unit tests, right? There should probably be some templates here too.
[/LIST]
 
[/LIST]
 
[/LIST]
End users will be able to access the templates which should help with consistency. Everything else is up to the end user. 

Lately, I have placed my .R and .py files in the root folder and then source/load library files in R/ and python/ as needed. It keeps things relatively simple and uncluttered, without requiring me to go into a whole series of nested folders to find what I am looking for.

---

