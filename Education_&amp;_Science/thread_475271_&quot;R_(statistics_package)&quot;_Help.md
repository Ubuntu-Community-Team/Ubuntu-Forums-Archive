---
title: "&quot;R (statistics package)&quot; Help"
date: 2007-06-15
forum: Education &amp; Science
---

### Post by Shibby73 on 2007-06-15
Hello everyone.
I have a project I am in preparing to work on.  It involves looking at some data on blood pressure control among patients with diabetes.  I think I will be getting my data as an excel spread sheet.

I was going to use SAS, but I am unable to get a working copy at this time and since I love the idea of open source and using linux, I figured I'd give R a try.

Looks like a powerful program!  Unfortunately, I was trained to use SAS and basically cheat with SAS commands by using prior written code with my notes attached to accomplish my tasks.

I was hoping there was some help on importing data into R from an excel file.  I am not very Linux savvy to know where to put (and where I have put) any excel files to try out importing data.

Then I need to do some If/then type of data manipulations to create some categorical variables in the data set (like IF systolic bp > 129 OR diastolic bp > 79 then BP=1 else BP=0) so I can sort out my data.

Can anyone point me in the right direction to find the code I will need to type into the CLI for R.

Also note I am using "R (statistics package)" as my thread title after realizing that the search feature on the forums doesn't handle just "R" very well due to the lack of 3 letters - I find a lot of irrelevant posts.

Thank you,

Steve

---

### Post by meatpan on 2007-06-16
I'm not very familiar with importing data directly from excel.  However, R has some great facilities for reading 'csv' (comma separated value) text data.  In excel, you can save a file as csv using a pull-down menu  at the bottom of the the typical 'save-as' screen.  It's usually a pretty painless operation once you get used to it.  

Once you have a csv file.  Load up R and use the 'read.table' command.  I usually just do something like:

```

dIN <- read.table("file.csv", header=TRUE, sep=",");
summary(dIN);

```

The first line creates a variable that refers to your data set, which was imported via the read.table function.  The header and sep arguments are optional, but frequently useful.  The second command displays a few basic summary statistics about each column in the new dataset.  This is a good way to verify the first step worked as expected.

If you want to see all the options about reading a file using this technique, check out:
[http://rweb.stat.umn.edu/R/library/base/html/read.table.html](http://rweb.stat.umn.edu/R/library/base/html/read.table.html), or run '?data.frame' from within R.

R has some typical conditional statements, such as 'if' and 'else'.  Try something like
```

if ( val > 100 ) {
   ... execute ..
}

```

A good way to practice this stuff is to open an interpreter in one window, and a text editor with your script in the other.  You can immediately test your commands in the interpreter as you are developing your script.  

I'm not exactly sure how to answer your file saving and referencing question.  The unix filesystem is very logical and well-designed, but takes time and practice to learn.  I recommend learning some unix commands such as 'ls', 'cp', 'mv', and 'cd'.  Also, linux has a few file-manager applications that have the look & feel of the windows explorer.   Nautilas is one of these programs that comes to mind.  I've never used one of these apps, so you might ask someone for advice.

---

### Post by fsando on 2007-06-16
Hi Shibby73
First off - there is a bit of a learning curve to start using R but I'll see if I can be of some help to you.

There are several versions of read.table - the differences are related to which delimiters and decimal separator etc. You can get help on 'read.table by issuing the ?-command:
```
?read.table
```
you return to the R-console by pressing 'q'.

I've created a small example that may fit your case: (let's assume your csv-file is called  'blood.csv')
```
data <- read.table('<path-to-folder>/blood.csv')
```
To see the names of all variables in 'data':
```
names(data)
```

Let's assume the names of the blood pressure variables are 'sbp' and 'dbp'. To see these variables:
```
data$sbp
data$dbp
```
And
```
summary(data$sbp)
summary(data$dbp)

```
to recode according to what you wrote:
(like IF systolic bp > 129 OR diastolic bp > 79 then BP=1 else BP=0) 
```
data$bp <- (data$sbp>129 | data$dbp>79)*1
```
Explanation:
data$bp (create a new variable in the dataset 'data')
(data$sbp>129 | data$dbp>79) (this expression is TRUE when sbp>129 or dbp>79 otherwise FALSE)
Multiply with 1 - this is a hack to convert logical values (TRUE/FALSE) to numeric values (1/0)
To make a frequency table:
```
table(data$bp)
```
Let's assume another variable (e.g. number of days in hospital data$ndh) you want to test against the two groups with a t-test:
```
t.test(data$ndh ~ data$bp)
```

UPDATE:
To save a dataset (again, there are several ways to do this)
```
write.table(data,file="<path to folder>/data.csv")

```

Relevant link:
[http://cran.at.r-project.org/](http://cran.at.r-project.org/)
Click on 'manuals'

---

### Post by Shibby73 on 2007-06-17
Wow, thanks guys!!

I also learned I can copy and paste into R.
Meatpan's method worked for importing my data from a CSV file, I used the separator commands just as you outlined.

Fsando's methods for making a new variable also worked out well.

So now I have a dataset that I saved as a CSV, however when I opened the CSV I noticed the thing changed the data over under the wrong headers!  Something went wrong with Fsando's method of saving the file as .csv... perhaps with no separator or something?

I have my data in a table, many individuals came into the office multiple times over 6 months so I have multiple SBP and DBPs for them (hence multiple entries for the same person/PTID).

What I care about is whether the doctors seeing these patients are identifiying them as having elevated blood pressure or not, and whether they are on any medications or not when their blood pressures are >129/79, but I don't want to count the same persons multiple times when looking at the population. Some of the patients only came in one time.  So how do I rearrange this data from within R in say a frequency table, by PTID or something.  It is late here, I don't know if I am making any sense.
For example I want to know (not how many patient visits) but how many patients seen (56 patients were seen totalling up to 231 visits) so out of 56 patients how many of them have elevated blood pressure, don't have any medications and are not being identified as hypertensive (and I would like to know what their blood pressures were at each visit if necessary, or be able to average the bps).

Thank you for your help, R is AWESOME, I just don't know how to use it as well as I did SAS.
Also I am not sure I ever had to rearrange data like this before.

-Steve

---

### Post by Shibby73 on 2007-06-17
So I am thinking of rearranging the data (outside of R) but wish I could code some method of doing this:

PTID ... DOB .... VISIT1 SBP1 DBP1 VISIT2 SBP2 DBP3.... VISITn SBPn DBPn .... AVGSBP...AVGDBP ... HTN ... BP ... MEDS ... INCLUDE
Where PTID (patient ID), DOB (date of birth)
VISIT1 (date of first visit for that patient), etc.. up to n Visits (range 1-???)
SBP1...SBPn and DBP1...DBPn are the actual BP readings for each visit for that patient
AVGSBP (average of the SBPs over all n visits) and similarly AVGDBP
HTN is whether the physician(s) have any ICD-9 code of elevated BP or hypertension in the problem list/billing sheet
BP is the result of my test on the SBP and DBPs, really if there are 2 or more visits where a SBP is >130 or DBP is >80 then I want to call this value TRUE (meaning they HAVE an elevated BP)
can do another avgBP to see if the average SBP and DBP is >130/80  to test if averaging catches these patients.
MEDS is a yes/no variable from chart reviews to see if the patient is on ANY BP lowering medications
INCLUDE is a yes/no variable to help with my next dataset (to include only those patients who do not have any BP lowering meds, do not have HTN or elevated BP in their problem lists and have elevated BPs) this is for a computerized intervention I am trying to justify working on in our office for a research project.

Hope this explains what I am trying to do better.

Thanks for you help and interest.

Steve
Resident Physician

---

### Post by Shibby73 on 2007-06-17
Found a neat sounding package called RESHAPE ([http://had.co.nz/reshape/](http://had.co.nz/reshape/))... but I am running into a problem with installing and executing its functions.

I type:
install.package("reshape")
after finding a mirror near me (the first I tried was trying to install a missing older version) but the second I tried found the newest reshape_0.7.4 version.

Typing ?reshape finds a help file for the package.
But the commands I want (that come with the package appear to be missing).
?melt
?cast

both are not found?

Any help?

I wrote to the package developer and will see what he says as well.
Basically melt permits the data to be reorganized into just ID and Variables with Values then it can be
recast into any format desired for further analysis. I think this is exactly what I am looking for to try to automate my pending dataset with multiple observations on individuals over time and looking at changes in their categorization over time as a result of some office-based interventions.

Will keep you posted and look forward to comments, suggestions, and feedback.

Best regards,

Steve

---

### Post by fsando on 2007-06-17
I'm a little busy right now so I didn't read your post closely but the problem with saving csv should probably be solved by adjusting the write.table command. Issue this command to see the options:
```
?write.table
```
and pay attention to 'delimiter' and 'quote' and perhaps especially to 'row.names' and 'col.names' . 'write.table' will automatically add row numbers if you don't set row.names=FALSE. Do a few tests and see which is the correct.

And for future work with R. You can make R programs just like SAS programs. You  write the code in a normal text file (say 'rsource.R') then run this file from R with the command:
```
source('<path to folder>/rsource.R')
```
If you want a specific output from inside an R program you must use the 'print' command. To see the variable names of 'data' you would write
```
print(names(data))
```
in your file

UPDATE: I reread your post and this is not the answer to your problem (see below)
To rearrange variables in a dataset inside R - there are several options  - one way would be (say you want column 1,2,3,4,5 to be arranged in this order: 5,4,1,2,3)
you would do:
```
newdata <- data[c(5,4,1,2,3)]
```
Explanation:
data[] - square brackets indicates indices into an object, here we indicate which columns we want
c() - is a function that creates vectors - here it creates a vector which contains the numbers 5,4,1,2,3 in that order.
(Almost) any object in R can be accessed by several methods, one of which is by index, so if I want column 3 in a dataset  (in R called a data.frame) and its name dbp I could ask for data[3] or I could ask for data$dbp. 
If I want several columns I have to give those indices as a vector.

There are some caveats to this (for more advanced uses) - but in your case I think it will work well.

You can use the command 'str' to check the structure of an object (to see the structure of the objects 'data' and 'newdata') to do an error check of sorts:
```
str(data)
str(newdata)
```

UPDATE
DUPLICATE ROWS
Things to consider:
1) You must decide which of the duplicate rows you will retain (it's up to you)
2) You must identify duplicate rows on some criteria - here it would be the PTID
```
newdata <- data[!duplicated(data$PTID),]
```
Explanation:
data[<xx>,] - numbers to the left of the comma are indices to the rows you want, if it's empty to the right of the comma it means 'all columns' otherwise you can select certain columns like above
! - exclamation mark negate the following statement
duplicated(x) - tags first occurrence as not duplicated (ie. FALSE) and any subsequent occurrence as duplicated  (ie TRUE).
So this command returns a reduced version of the dataset with only non-duplicated rows (in this case all first occurrences).

You may wish to control which occurrence is first by sorting the data (say by date):
```
sortdata <- data[order(data$PTID,data$DATE),]
```
Explanation:
ordering first by id, then ordering by date within id

more on sorting here:
[http://wiki.r-project.org/rwiki/doku.php?id=tips:data-frames:sort](http://wiki.r-project.org/rwiki/doku.php?id=tips:data-frames:sort)

Also look at the function 'aggregate'

---

### Post by UbuWu on 2007-06-17
It is probably easiers using a gui like [RKWard]("http://rkward.sourceforge.net/")...

---

### Post by fsando on 2007-06-17
> **UbuWu said:**
> It is probably easiers using a gui like [RKWard]("http://rkward.sourceforge.net/")...
Hi UbuWu
Yes you are probably right - I haven't had such good experience with it though (tried it under Ubuntu 6.10 it was pretty unstable), but then I'm a code freak - prefer coding by hand, been coding various systems for years.

There is also John Fox's R commander. It may be the most accessible - it can be installed through synaptics ('r-cran-rcmdr'). It can then be started by the command
```
library(rcmdr)
```

Actually I find that the 'pmg' package is the most interesting - but it was a VERY arcane installation experience where I had to compile various components by hand.
> **Shibby73 said:**
> 
<snip>
Typing ?reshape finds a help file for the package.
But the commands I want (that come with the package appear to be missing).
?melt
?cast

both are not found?

Any help?
Steve

After you've installed a package you load it for current session by issuing the command. Only after it's loaded you can get help through the '?'-method
```
library(<package name>)
```

Actually it may be a very good idea to read through the manual from the r-cran page. The manual is very easy to understand an quick to go through. And it will give a good overview of R.

---

### Post by Shibby73 on 2007-06-18
Thank you for the continued help.  Yes the manual... I have read it but often can't find what I am looking for because I don't know what to call what I am trying to do.

Good idea with the PTID but then I lose the data for each subsequent entry.
What I would like to do is I guess aggregate, but having trouble because I don't know how to create a list, I sued as.list and it doesn't seem to stick... perhaps I need to experiment and read more.

In SAS I could easily just make a series of new datasets where all PTIDs were the same (all PTID=1) using a where command, and then I'd have a dataset for each individual patients observations to work on how I would come up with some summary statistics on them (like determining elevated BP based on certain levels, certain numbers of times elevated, and what the trend in BPs were).  Then I would export those summary stats for that individual in a merged/concatenated table with all of the Patients (each by PTID with only one entry per patient). Of course with SAS I could also do PROCFREQ on the whole data set and use a by or where command to do it by patient (PTNO/ID).  Is there a link to where I can find SAS commands and their counterparts in R?

Thank you, bit late here, heading to bed.

Best regards,

Steve
PS. I definitely prefer command line, great pointer to write the scripts in a text editor for later reference!

---

### Post by Shibby73 on 2007-06-18
I did figure out the library issue with reshape (and Melt/Cast) it doesn't do exactly what I want to do... as stated above, SAS commands were more straightforward (but I am just not finding what I need in the manuals).

I will need to read up on the creating a LIST and see if aggregate fits the bill.  New to OOP so it is all difficult and foreign to me.

Thank you for your patience and teaching.

-Steve

---

### Post by fsando on 2007-06-18
> **Shibby73 said:**
> Thank you for the continued help.  Yes the manual... I have read it but often can't find what I am looking for because I don't know what to call what I am trying to do.
<snip>
Unfortunately you are pretty spot on regarding R. This is a problem that doesn't really go away. As much as I love R I'm still annoyed by the systematic inconsistency in naming conventions.
I have many times resorted to simply peruse through lists of hundreds of commands to see if there was anything useful or interesting. I'd say that in any other programming language I have been dealing with this has not been nearly as confusing. Though you may come to love this feeling or arcane academic irrationality ;)
Anyway your problem with aggragate:
First create a reduced dataset
```
newdata <- data[!duplicated(data$PTID),]
```
Then add the aggregated variable
```
newdata$bpmean <- aggregate(data$bp,list(ptid=data$PTID),mean)
```
Explanation
You want to add a variable to the reduced dataset based on the same variable you used to reduce with - they need to be of same length
aggregate will aggregate data$bp within levels of data$PTID - ie. one value for each PTID
the list command creates a list with one element named 'ptid' consisting of the vector data$PTID
The function to create aggregated values is 'mean'

---

### Post by euler_fan on 2007-06-18
This is a link to a document that as a SAS user you might find useful (if a bit more over the intermediate term)

It is an into to R for SAS and SPSS users.

[R for SAS and SPSS Users]("oit.utk.edu/scc/RforSAS&SPSSusers.pdf")

---

### Post by akniss on 2007-06-18
> **euler_fan said:**
> This is a link to a document that as a SAS user you might find useful (if a bit more over the intermediate term)

It is an into to R for SAS and SPSS users.

[R for SAS and SPSS Users]("oit.utk.edu/scc/RforSAS&SPSSusers.pdf")

That is an excellent reference!!! Thank you.  I wish I knew about that two years ago when I was transitioning from SAS to R...

---

### Post by euler_fan on 2007-06-18
> **akniss said:**
> That is an excellent reference!!! Thank you.  I wish I knew about that two years ago when I was transitioning from SAS to R...

You're welcome.

Good luck with your research efforts in R. It can be a bit daunting, but once you get a hang of it enough to write your own scripts (which are actually pretty easy, on net) it becomes a really powerful tool very quickly.

---

### Post by earlycj5 on 2007-06-20
> **fsando said:**
> Hi UbuWu
Yes you are probably right - I haven't had such good experience with it though (tried it under Ubuntu 6.10 it was pretty unstable), but then I'm a code freak - prefer coding by hand, been coding various systems for years.

Err, I use RKward myself but I don't understand what you're getting at here.  I do it "by hand" in RKward myself.  Syntax highlighting, tabs, easy to run a program with the click of a button, etc. are enough to convince me.

Never had any problems with stability either.

---

### Post by euler_fan on 2007-06-20
I prefer to use Cream (a VIM implementation with syntax highlighting for R) to write the commands and then copy/paste them over, or at this point, to write whole scripts and then use the source command to execute them into R. Usually I am running R from the terminal with the buffer set to something like 5000 lines.

I haven't tried RKWard, but it look interesting. Not sure without a script debugger how much use it would be for anyone doing much custom work (e.g. something not already implemented well in one or more existing packages or built into RKWard itself). I don't script continuously or I might try EMACS/ESS.

---

### Post by fsando on 2007-06-20
> **euler_fan said:**
> This is a link to a document that as a SAS user you might find useful (if a bit more over the intermediate term)

It is an into to R for SAS and SPSS users.

[R for SAS and SPSS Users]("oit.utk.edu/scc/RforSAS&SPSSusers.pdf")
Thanks for that link - nice source.

> **earlycj5 said:**
> Err, I use RKward myself but I don't understand what you're getting at here.  I do it "by hand" in RKward myself.  Syntax highlighting, tabs, easy to run a program with the click of a button, etc. are enough to convince me.

Never had any problems with stability either.
I've followed RKward (at a distance) for years and it was one of reasons I switched to linux recently. Naturally it was one of the first thing I tried out - so my experience may be due to my inexperience with linux. I'm sorry if I gave the impression it's not a good program. At the moment I use Eclipse with the StatET extension. 
I'm just taking a quick look at it RKward right now and it looks great so I may have been too hasty in disregarding it - though it just died on me - again ;)

Actually, Thanks for pointing RKward out to me - I think it's really great

---

### Post by TimMills on 2008-02-09
The Rcmdr (R Commander) package is a popular graphical interface in my department.  It has a simple menu interface, but you can see the R commands being spelled out in the background, so you can quickly bootstrap yourself up to just using the command line.

[http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/]("http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/")

Rcmdr has a package in the repositories

I haven't used other GUIs in R, so can't compare.

---

### Post by carpoll on 2008-02-12
Hello everyone,
I have been following your discussion and learning about it. Thanks.
I am not sure if I should start a new threat but since it is related to R here it goes. 
I am working on a project and I have one several categorical variables and one continuous variable. R is reading all of them as categorical. How could I specify that the variable with numeric values should be read as a continuous variable?
 Thanks

---

### Post by mali2297 on 2008-02-12
> **carpoll said:**
> Hello everyone,
I have been following your discussion and learning about it. Thanks.
I am not sure if I should start a new threat but since it is related to R here it goes. 
I am working on a project and I have one several categorical variables and one continuous variable. R is reading all of them as categorical. How could I specify that the variable with numeric values should be read as a continuous variable?
 Thanks

I don't fully understand your question, but see
```

?as.numeric

```

---

### Post by carpoll on 2008-02-14
Thanks for your help. It seems to work well.
Another question I am trying to do a Mixed Logit Model. All of my predictor variables are categorical as well as the dependent variable (Occurrence)i. My data looks something like this:

Subject   Item   Voicing   Stress  Placeart  Vowel Order  Occurrence
s1             1        vced       pre       coronal   a         btf      1
s1             2        vless      tonic     bilab       e          ftb      1
s2             1        vced      pre        coronal   a          btf      0 
s2             2        vless      tonic     bilab       e          ftb       1 
s3             1        vced       pre       coronal   a         btf       0
s3             2        vless      tonic     bilab       e          ftb      1

I am following Florian Jaeger's tuturial but I am having problems. R does not seems to recognize the variables that i am using. 
I am using 
<-lmer (Occurrence ~ Vocing + Stress)
Does any one have any experience with Mixed Logit Models?

Thanks,

---

