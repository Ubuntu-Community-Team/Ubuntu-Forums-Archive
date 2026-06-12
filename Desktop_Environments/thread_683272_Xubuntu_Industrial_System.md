---
title: "Xubuntu Industrial System"
date: 2008-01-30
forum: Desktop Environments
---

### Post by themusicwave on 2008-01-30
Hey everyone,

I've been given a project at work that I need to do on the cheap.  I need to keep costs down and am thinking of using a really tiny computer and Xubuntu to pull it off.

I am slowly moving my employer away from Microsoft and toward open source and they love it thus far.  I saved them thousands of dollars this year by using open source software.

A little background on me, I'm a recent college graduate with a B.S. in software engineering.  I work for a company that manufactures manufacturing equipment(recursion?) and I make supervisory and industrial PC systems.

Here is what I need to do.  I need to control a peice of equipment from as cheap a PC as we can afford.  I found one that has 256mb RAM, 5GB HDD and a 500mhz processor.  Basic video as well.  The plan is to attach it to a touch screen and have it run my application on bootup essentially turning the PC into a dedicated control.

Here is what it needs to do:

1) communicate over Ethernet with exactly one piece of equipment updating up to 150 values every 2-10 seconds.

2) Run a database for logging the data for about a month.

3) Run some sort of web server to allow remote access from somewhere else in the plant via firefox, and Internet Explorer.  Up to 4 concurrent sessions.

4) Generate reports, preferably to .xls format(excel)

5) Be very low cos with no license fees.

My plan is to use the above mentioned machine running a paired down Xubuntu install.  Basically the only apps I need are open office, apache HTTP,  Java JRE, python, and Apache Derby/Java DB.

I chose Java because well I am good at it I only have a month to pull this off(if that) and I know Java pretty well.  I also have all the communications and database code already written from a pprevious project.  My boss also wants it to be able to run on Linux and windows.

Since I chose Java, I also chose derby/Java DB because it has a very small footprint bt is unlimited in size.  It should fit my needs.

Then there is Apache for a webserver, I am not sure if this is the bes one for the task but I am familiar with it.  Some guidance here would be good.  I would like to do server side code in python with some AJAX for refresh.  I know python, but not AJAX.  This is the area where I am currently weakest.  I need  a web app that updates in real time.  Ideas welcome...

For reporting I am planning on using the Open Office API/SDK to generate .xls(excel) reports.  I have no experience here either so I have no idea what goes into it.  I did write an application in C# that output excel reports using the Microsoft Interop API for Excel. 

So am I crazy?  Do I have any hope of success and what suggestions do you have?  I'm open to anything although I am resistant to drop Java because I know it well, have limited time and have half the code done for the portion.  The web page part has me worried the most...

I am also pressing to get some of the profits donated to various open source projects.  Ex: 1 dollar per project per sale.  It is possible we could sell hundreds or thousands of systems.

Thanks,

Jon

---

### Post by sola on 2008-02-01
I don't see anything strange in this setup, it should work.

Although, I suggest using only one programming language and a more consistent set of technologies: Java & Javascript

I would leave out C# and Python because the tasks you mentioned are perfectly solvable with Java tools. It makes your project easier if you have to work only with one programming environment.

For web pages: JSP/Tomcat on the server with Javascript on the client. I would leave out AJAX if a very dynamic web page is not absolutely necessary because it complicates things.

A simple GUI-less servlet running under Tomcat could read the data from the equipment and store it into the database.

For reporting, I would use Jasper Reports (can produce PDF or Excel output). You can run it from within JSP web pages (which run in Tomcat and shown in the browser).

With Tomcat you don't need Apache because it can run standalone too. If you need HTTPS or wire-compression, you can integrate Tomcat with Apache by a connector so Apache does the actual HTTP communication but Tomcat serves the requests.

---

### Post by themusicwave on 2008-02-01
Thanks for your input.

I do have some experience with JSP, very minor stuff.  I used it in a class for exactly 1 project and forget most of what I learned.

I prefer open or Java alternatives to Microsoft ones for sure due to vendor lock in and portability( and a general disadain for Microsoft).

I am not planning on using any of the C# code I mentioned, I was just mentioning it to show I had experience with such software.

I did manage to get a basic reporting class written in Java usiong OpenOffice.  Their API and documents are great!  I can now easily generate ODS and XLS reports.  So that is taken care of pretty much.  Write now I can write to cells and rows, write formulas and format cells and rows(font, bold, etc).  I next need to tackle charting perhaps.

Does Jasper reports work with J2SE?  I am not familiar with it.  The higher ups want .Xsl(Excel) format because they are typical corporate Microsoft rocks guys and because all our customers use excel.  So I need to stick with Excel.

Also I have almost all the drivers to run on the device itself.  I have all my communications and my database system working great.

I still need to write some Java code to do real time trend graphs on data points, but I think I can handle that pretty easily.  I've written decently sophisticated paint programs with gradient, transparent and double buffering and all that.  So I think I can handle it.

The only part worrying me is the Web parts.  I need to use something dynamic because it has to be dynamically updating the state of the equipment as you view it.  I guess I could use an Applet, but I didn't think they were very widely used anymore.  I can do the Server Side part no sweat, I have dabbled in PHP, but I prefer python.  I haven't done python online yet but I do know how to write scripts and apps in it.  I also did a bit of JSP, but how does that combine with AJAX?  I know PHP + AJAX is popular and python + AJAX seems logical too. I have no AJAX or JavaScript experience, but could always learn.

One thing that will be rather hard is that I have to make real time trend graphs in the browser.  I was thinking applet for this reason, but what else could I do?

Thanks for the help,

Jon

---

### Post by tgalati4 on 2008-02-01
How often do you have to update the graphs to consider them real time?  With some clever html programming, you can simply display a graph of your parameters taken from a text-based data file that gets updated by your monitoring application.  Just choose a sensible update interval so that you are not overloading the machine.  There's a lot of info on home-grown weather stations that display current temperature and temperature history.  I would look at how those are coded and see if  you can reuse them.

Someone gave me an old, serial port weather station that I would like to set up on an old pc with linux, so I'm trying to do something similar.

---

### Post by themusicwave on 2008-02-01
That is an interesting idea.

For real time I would save this data needs to be updated every 10 seconds.

Also, they need to be able to scroll "back in time" to see previous values.

I am leaning more and more towards a Java applet.  It maybe slower, but it seems like it would be much more powerful and easier.

Anyone know of any compelling reasons to not go with an applet?

---

### Post by tgalati4 on 2008-02-03
With some simple html and css you can program up a static html page (say my_process_that_I_am_monitoring.html) and have that page display (in table and graph format) the needed data.  Share this directory on your local network.  Anyone with a browser (Windows included) can point to that html file and it will refresh with the latest data every time you hit refresh or you can set the page to autorefresh with some time interval.

To serve the page outside of your network, you would need to set up an apache2 server and open a specific port (say 62000, anything above 10K) and serve up the data over the web: 999.999.999.999:62000/my_process_that_I_am_monitoring.html

Java is powerful, but not needed unless you need to interact with the data in a way more involved than just scrolling through a list of values.

---

### Post by themusicwave on 2008-02-03
As I said, it does need to be a dynamically updating page.

I need to show realtime(updated every 10 seconds) trend graphs. I also need all the data points in the equipment to update as they change in real time.

The user will also be able to write to the device through this web page program, which means either a socket connection or a database connection.  

I do understand using static HTML is simple, but it just does not meet my goals.  Neither does PHP or python alone.  I definitely need something client side.

I am still leaning towards the applet.

---

