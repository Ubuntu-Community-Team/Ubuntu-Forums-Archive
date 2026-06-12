---
title: "Better Generic Database Front-end"
date: 2011-02-22
forum: Education &amp; Science
---

### Post by gunksta on 2011-02-22
I need to find a good generic database front-end. Since this is more of a development question than a science question, I threw it out over on the developer's sub-forum [here]("http://ubuntuforums.org/showthread.php?p=10483402#post10483402"). So far, two different people have recommended that I use Access. I do actually use Access, but I would prefer to not use it as a generic database front-end.

In a nutshell - I connect to the client's database to access information. Since it is their database, it could be almost anything. I've had good luck using JDBC drivers from Linux to connect to different servers, but JDBC is not a requisite. ODBC would be equally acceptable as long as I can find the ODBC drivers I need. I want to use one tool (more or less) to connect to the clients' servers and develop my queries, views, stored procedures, etc.

Then, depending on the job, these queries will either be used to power a website or they may be run via R, to download the data for additional analysis.

I am using SquirrelSQL right now and while it works (more or less) it seems to have a fair amount of trouble with SQL Server connections and it's interface is bizarre and difficult to use, compared to other tools that I have seen. In raw frustration with Squirrel, I've lately been playing with sqsh,  which is fast and stable, but is only useful for connecting for SQL  Server and I often have to connect to other databases, thus something  that uses ODBC or JDBC would be preferable. I also tried Vim's dbext but failed to get it to actually  connect to anything. I tried Eclipse but quickly discovered that the  Emacs/Vim learning curve is quick and comparatively painless. 

I am looking for options/suggestions of generic SQL front-ends that other people have used successfully. I'm willing to continue looking at dbext/Eclipse if someone thinks they are worth my time. The only way I can easily run Access is in a VM and it seems silly to start a VM, just to write some SQL queries.

---

