---
title: "Using R with SQLite"
date: 2010-05-15
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2010-05-15
Hi there, I wondered if anyone could give me some advice regarding connecting a SQLite database with R using the RSQLite package, and lifting the data into R. I've managed to work it so far and can assign my table as an object in R using the following code:

**data <- dbGetQuery(con, "SELECT * FROM dust")** where "dust is the table in the database and "con" is the connection. 
Alternatively I can also do it with: **data <- dbReadTable(con, "dust")**

After this I can simply put attach(data) and be on my merry way and I've also been able to only one column of the database with: **data2 <- dbGetQuery(con, "SELECT acc FROM dust") **where "acc" is the coloumn name. 

But now I want to narrow the choice down even more by only selecting values from "acc" where in the same row on the table, the value of another coloumn "cleaner" has the letter d. [I](The background behind this being values of microbe counts from dust from bag vaccums and dysons). Hence I want only the acc values where the cleaner is d (or dyson)).

[/I]I've tried code such as **data3 <- dbGetQuery(con, "SELECT acc FROM dust WHERE cleaner = d") **but so far no luck. 

Also, as an additional question - do any of you know of a way of working with and analysing the data in a database without having to lift it and assign it to an object i.e. the "**data<- ..**." bit. Thus saving even more memory, as all these objects do take up quite a bit cumulatively.

Any help greatly appreciated, thanks in advance.:) (I'm using Ubuntu 10.04, if it makes any difference).

---

### Post by gunksta on 2010-05-16
> I've tried code such as data3 <- dbGetQuery(con, "SELECT acc FROM dust WHERE cleaner = d") but so far no luck. 

Your query isn't working because you haven't denoted "d" as a string, which it is.  Try this:

```
data3 <- dbGetQuery(con, "SELECT acc FROM dust WHERE cleaner = 'd'")
```


> After this I can simply put attach(data) and be on my merry way
I rarely recommend using attach(), because it can cause more problems than it solves. My general rule of thumb - if you don't understand R environments - stay away from attach().

> do any of you know of a way of working with and analysing the data in a database without having to lift it and assign it to an object i.e. the "data<- ..." bit. Thus saving even more memory, as all these objects do take up quite a bit cumulatively.

Depending on what you are trying to do, you may be able to do more of the processing within SQLite, but I would need to know more about what you are doing to be certain. On a reasonably modern machine - most users do not have memory issues.

Last year I managed to import 3 data sets from a SPSS project, organize them longitudinally and create graphical output. Each SPSS data file weighed in at around 30 megabytes. The computer only had 1 GB of RAM, but I was able to process all of this without R blowing up. When I ran the syntax, I tried to free up as much system memory as possible (no music players, web browsers, etc) but I ran it from my standard desktop and R never crashed. The largest bottleneck was importing the data from the SPSS files.

I run statewide/federal data sets on a regular basis in R and never need to do anything fancier than store/process the data in Postgres. This too is probably overkill but I like the flexibility it gives me in terms of accessing the data directly from other programs.

Honestly, unless you have a BUNCH of data, and I mean gigs of data; or you are using an ancient computer - you don't need to waste your time doing hat tricks to conserve RAM. In fact - depending on the size of your data set, I would question if using SQLite is truly necessary. It's a nice way to structure your workflow and I'm not criticizing your choice, but I'm not sure it's actually necessary. 

Yes, if you lurk on the R-users mailing list (not the friendliest list IMHO) you will see people ask about memory optimization from time to time, but I think using a database backend would solve the problems for most folks. Another simple solution for most memory problems is to run a database like Postgres or MySQL on one computer and run R on another computer. In our office we have a postgres instance running on the file server. Before getting my new laptop, I would often store the data set on the file server in Postgres. I only dealt with the limited part of the data I actually needed at that moment on my limited laptop. Doing this I was able to process some pretty huge datasets (over 1 gig) on my laptop and never even feel the pain. An old computer sitting in the corner could be the "server" you've been looking for.

If you have a computer with more than 1 GB of RAM, you are going to have to convince me that memory constraints are a problem for you.

---

### Post by Axolotl9250 on 2010-05-17
Hey, thanks, the SQL is working now. Yeah you were right my memory isn't too bad so using RSQlite is enough. With the attach() issue, I'm a Biology student and I've read about using R and I'd say I'm one of the better in the class at it (indeed one of the only that bothers, everyone else uses Minitab), so I've only been taught and have experience with attach(), what's the better way to operate in this regard?

---

### Post by BlueBob on 2010-05-18
I'm trying to install the RSQLite package but am unable to do so because my version of R is too old but Ubuntu thinks it's up-to-date, command used to install RSQLite:

$ sudo R CMD INSTALL RSQLite_0.9-0.tar.gz

Gives error:
* Installing to library ‘/home/mmaguire/R/i486-pc-linux-gnu-library/2.9’
ERROR: this R is version 2.9.2, package 'RSQLite' requires R >= 2.10.0

I've tried looking for an older version of RSQLite without success, any ideas anyone?

---

### Post by gunksta on 2010-05-18
> **Axolotl9250 said:**
> what's the better way to operate in this regard?

Like I mentioned earlier, I think attach() and detach() can cause problems. There are situations in which they can be useful, but not as many as people sometimes want to believe. Most R aficionados believe the data frame is one of **the **most useful aspects of R. Data frames are like matrices, but they can hold different types of data. The ability to hold data, in a tabular structure, with multiple variable types is reasonably unique to R and gives it much of it's power. Of course, SPSS can do this too, but it can only handle one such data structure at a time. R can handle multiple data frames simultaneously. And, there is no reason why a data frame must be ONLY two-dimensional. You can have more complicated structures if you need them. Depending on your needs these features may or may not be useful.

Here's an example of why attach() can cause problems. Let's create a data frame. Create an empty R session. To make sure it's empty, use ls() to make sure there's nothing there. Then,

```
animals <- data.frame(type=c("cat","dog","cat","dog","dog","dog","cat","dog","cat","cat"), age=c(1,3,2,4,2,3,1,5,8,7))
```This will create a data frame called animals. Now ls() should return "animals". Now, if we attach the data frame to our current environment, we can access our variables directly.

```
attach(animals)
```While this does give us direct access to our variables, they don't show in the environment. The output from ls() hasn't changed.

After doing this, we learn that the age for the third animal is 6, not 2. 

```
age
```As you can see, the third value is 2, not 6. Oops. Well, it's not too hard to fix it.

```
age[3]<-6
age
```Now we have fixed up our data set and we can continue on doing whatever analysis we wish to do. Perhaps we want to test to see if dogs age older than cats or something. I don't know. Analysis isn't the point here.  :)

Now, let's see why attach() could trip us up. Look at the values stored in "age". Now, detach animals.

```
detach(animals)
animals
```When you look at the values in animals, you should pay extra attention to the "age" column. Our change to the third value (2-->6) has been "lost". This isn't a bug, it's the way R is designed, but it can be a problem for new users. Read this for extra details:

```
?environment
```
Now that we have established that attach() isn't always a good approach. Indeed it is nearly impossible to use if you are trying to work simultaneously with two data frames with the same structure - like a longitudinal study might produce (if the data is poorly structured).

Let's go back and look at animals again. There are several ways we can access our columns. Are you familiar with accessing individual components of a vector? For example, age[3] gives us the third element of the vector age. In this way R and python are very similar. Fortunately, data frames can be accessed in a similar way. Look at the results when you:

```
animals[1,]
animals[,1]
animals[,2]
```The first command gives us the entire first row. The second command gives us the entire first column. The third command gives us the entire second column. You can even combine the two ideas:

```
animals[1,2]
```This will give you the contents of the first row, second column. R follows the standard x,y convention for accessing data frames AND matrices. But, this is a data frame. The above system is a little clunky. You can also, easily access your variables by name.

```
animals$type
animals$age
```The advantage here, is that it is extra easy to call on parts of variables. For example:

```
animals$type[animals$age>2]
```This returns the values of type where age is greater than 2.

There are other ways to twist these options around, but these are the methods that I find most useful. What resources have you read? I might be able to throw out a couple of useful websites that you should use/read.

---

### Post by gunksta on 2010-05-18
> **BlueBob said:**
> 
I've tried looking for an older version of RSQLite without success, any ideas anyone?

Technically - you should start your own thread for this, but here's the answer:

Idea #1 - upgrade to the newest version of Ubuntu.

Idea #2 - use the R project's version of R, not Ubuntu's. 

Ubuntu packages a number of useful tools from r-cran, but it can't possible bundle up everything. If you find that you often need to use R packages that aren't in the Ubuntu repositories, the easiest option is to install R from the people who make it. Fortunately, it's easy.

I don't know where you live, but if you would like to use the Berkely mirror, go here:

[http://cran.cnr.berkeley.edu/](http://cran.cnr.berkeley.edu/)

Otherwise, go here:

[http://www.r-project.org/](http://www.r-project.org/)

And go to download. Find the link for Linux and choose a mirror that is close to home. There will be a description for how to set up your computer to use their packages, rather than Ubuntu's.

Before you do any of this make sure you delete R and everything related to it from your computer.

If you need more specific help, tell me where you are (preferably in a new thread, just for practice's sake) and I can be more specific in my directions.

---

### Post by Axolotl9250 on 2010-05-18
The way I did it was to add a relevant mirror to my software sources and then perform the "sudo apt-get install r-base" command in the terminal. After that when the computer checks for updates it checks the mirror and updates R anyway.

---

### Post by BlueBob on 2010-05-18
thanks, Gungsta, I'm based in Cambridge, Enland

---

### Post by gunksta on 2010-05-18
This should work for you:

[http://www.stats.bris.ac.uk/R/](http://www.stats.bris.ac.uk/R/)

Don't use the Berkeley stuff. There's no reason to wait for everything to cross the continental US and the Altantic on it's way to your computer.

As was mentioned by Axolotl9250, you just want to add this repository to the list of repos your computer uses.

I hate to be pedantic, but I also don't want to see things get all confused. Make sure you have removed ANY and ALL R packages before doing this.

You can do this via the command-line, but I'll explain how to do this via the GUI tools. If you want to learn how to add repositories to your system via the command-line, just use google and throw in repositories, add or something and I'm sure you'll be able to find how to do it that way.

There is one step that is easier to do from the command-line. Open up gnome-terminal (Ubuntu) or konsole (Kubuntu) and enter the following code:

```
 
gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg -a --export E2A11821 | sudo apt-key add -


```Once that is done, you can close the terminal. We're going to be GUI from here on out.

Go to **System -> Administration -> Synaptic Package Manager**

After you enter your password, Synaptic will pop up. Go to Settings -> Repositories.

This will open a new dialog box for you. It has a set of tabs across the top. The second tab, "Other Software", is the one we want. 

You will need to know which version of Ubuntu you are running so you grab the right line. You need to copy a line that looks like:

  deb [http://www.stats.bris.ac.uk/R/bin/linux/ubuntu/](http://www.stats.bris.ac.uk/R/bin/linux/ubuntu/) karmic/

Into the dialog box. You'll need to hit the "Add" button.

I am guessing that you are running karmic. If not, replace karmic with the correct name. Options include:

karmic
jaunty
intrepid
hardy

If you aren't sure. **System -> About** Ubuntu should be able to tell you.

Once you are done adding the local R repository, Synaptic will want to update it's stored list of packages. Let it do so. Now you can install R and other packages as you want. AND - your earlier syntax should not install RSQLite correctly as you are now using an up-to-date version of R.

---

### Post by Axolotl9250 on 2010-05-18
I've only really read the sort of home written guides that my Lecturer had created, with t.test, Wilcoxon, simple regression, standard stuff really, but all of them don't work without the attach() command. Or rather I can't do it without the attach command and I've found no page yet telling me how to do it.

---

### Post by gunksta on 2010-05-19
If the directions are provided by your lecturer, it's probable that the directions avoid any attach() related problems. If you would like to learn how to access data in data frames directly, post some of the syntax you were given, preferably with the data set attached, and I can re-work it to show you how to do it without attach. But that's only if it interests you.

Although R has a steep learning curve, there are lots of well-written materials to guide you on your way. I attached a couple of the resources I have used. There are many other good sources out there, but after examining the copyright info on a few of these, it doesn't look like I am allowed to redistribute them.

I attached two files. One, written by the R-Core team is called R Intro. It's not the most exciting thing to read, but it is an excellent resource. I also attached a book called the R Inferno. It's loosely based on Dante's Inferno and is meant to help people learn how to use R. It's a hoot and very informative, but it's not for a novice R user. 

There are also some really good websites out there. Here are two that I think are very nice indeed.

[http://www.r-tutor.com/](http://www.r-tutor.com/)

[http://www.statmethods.net/index.html](http://www.statmethods.net/index.html)

Finally, use Google to find a file called "usingR.pdf" and "SimpleR.pdf". I read both when I was starting out, but the copyright info explicitly states that I don't have the right to redistribute, so you'll have to find these on your own.

---

