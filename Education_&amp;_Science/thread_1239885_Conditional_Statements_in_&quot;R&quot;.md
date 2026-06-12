---
title: "Conditional Statements in &quot;R&quot;"
date: 2009-08-14
forum: Education &amp; Science
---

### Post by chino cochino on 2009-08-14
Can someone tell me how to execute this SAS statement in "R"?
> 
if team="Texas" then team="TEX";

I tried:

> if (team=="Texas") {team <- "TEX"}

but apparently that only works for numeric values.

---

### Post by sdbrogan on 2009-08-14
That should work fine.  What error do you get ?

---

### Post by mali2297 on 2009-08-14
It works fine for me.
```

> team <- "Texas"
> team
[1] "Texas"
> if (team=="Texas") {team <- "TEX"} 
> team
[1] "TEX"

```

---

### Post by gunksta on 2009-08-14
WARNING: The following comments are written by someone who does NOT know SAS.

It depends on what you are trying to do. I know SPSS tends to handle variables in a manner very different from R. You can have a variable such as:

```
team <- "Texas"
```Here, team is a simple variable. With a basic variable, if() will work.

```
if(team=="Texas") team <- "TEX"
```But, if team looks like this:

```
team <- c("Texas", "Georgia", "Alabama")
```Now team is a vector. If you try to run if against it, it will fail.
```

Warning message:
In if (team == "Texas") team <- "TEX" :
  the condition has length > 1 and only the first element will be used
```Now my vector variable, team, which used to have three values, only has one. In this case it is "TEX" since my if() statement evaluated as True, because "Texas" was the first item in the vector. But, that's probably NOT what you are trying to do. I suspect you may be trying to replace ALL values of "Texas" with "TEX" in a vector, not a variable. To do this, we need to vectorize.

```
team[team=="Texas"]<-"TEX"
```This will replace the value of "Texas" with "TEX" in the vector team. This would be the "best" way to do this in R. You could also do this:

```
team<-ifelse(team=="Texas","TEX", team)
```Essentially, these are saying the exact same thing. If you spend some time lurking on the R-users mailing list you will see that the first solution is the preferred methodology by experienced R programmers. It is slightly more compact and is easy to understand, if you understand how R uses vector logic. If you are coming to R from a "traditional" programming languge (don't know if SAS works this way or not) then this whole vector things will seem a little weird to you for a while. It is WELL worth your time to read something like "An Introduction to R" or simpleR to get a basic understanding of how R operates.

---

### Post by chino cochino on 2009-08-14
> **gunksta said:**
> But, if team looks like this:

```
team <- c("Texas", "Georgia", "Alabama")
```Now team is a vector. If you try to run if against it, it will fail.
```

Warning message:
In if (team == "Texas") team <- "TEX" :
  the condition has length > 1 and only the first element will be used
```



This is the message that I got. Team is a vector.

> 
Now my vector variable, team, which used to have three values, only has one. In this case it is "TEX" since my if() statement evaluated as True, because "Texas" was the first item in the vector. But, that's probably NOT what you are trying to do. I suspect you may be trying to replace ALL values of "Texas" with "TEX" in a vector, not a variable. To do this, we need to vectorize.

```
team[team=="Texas"]<-"TEX"
```This will replace the value of "Texas" with "TEX" in the vector team. This would be the "best" way to do this in R. 

I tried this, and I got:
```
Warning message:
In `[<-.factor`(`*tmp*`, Team == "Texas", value = "TEX") :
  invalid factor level, NAs generated
```

> 
```
team<-ifelse(team=="Texas","TEX", team)
```Essentially, these are saying the exact same thing. If you spend some time lurking on the R-users mailing list you will see that the first solution is the preferred methodology by experienced R programmers. It is slightly more compact and is easy to understand, if you understand how R uses vector logic. If you are coming to R from a "traditional" programming languge (don't know if SAS works this way or not) then this whole vector things will seem a little weird to you for a while. It is WELL worth your time to read something like "An Introduction to R" or simpleR to get a basic understanding of how R operates.

Maybe I should do some studying on vectors, because I'm a little unclear. Thanks much for all you guys's help!

---

### Post by akniss on 2009-08-14
I will make one more assumption: that you are not simply dealing with a vector, but with a data frame. 
```

team<-rep(c("Texas","Nebraska","Oklahoma"),4)
awesomeness<-rep(c("sucks","greatest","losers"),4)
data.frame(team,awesomeness)->team.dat

```

In this scenario, gunksta's preferred method will give you an error (although I agree it is the best method for dealing with vectors).  However, the ifelse statement will still work if slightly modified:
```

team.dat # before 
team.dat$team<-ifelse(team=="Texas","TEX",team.dat$team)
team.dat$team<-ifelse(team=="Nebraska","NEB",team.dat$team)
team.dat$team<-ifelse(team=="Oklahoma","OKL",team.dat$team)
team.dat # after

```

---

### Post by gunksta on 2009-08-14
akniss - good point.

chino cochino - Could you post the syntax you are using to create team? I played around with a couple of ideas, but couldn't find a way to get the same error you are. If we knew for sure how you were creating the variable/vector/data.frame/whatever called team, it would help.

---

### Post by ahmatti on 2009-08-15
chino cochino,
You get the error because your datatype is factor and not string. The easiest way to recode a vector of factors is to use the factor command and specify new labels. See ?factor, I'd look for the syntax for you, but don't have access to R right now.

---

### Post by chino cochino on 2009-08-15
> **gunksta said:**
> akniss - good point.

chino cochino - Could you post the syntax you are using to create team? I played around with a couple of ideas, but couldn't find a way to get the same error you are. If we knew for sure how you were creating the variable/vector/data.frame/whatever called team, it would help.

OK, this is what I did. I pretty much imported it from a CSV file:

```

runs <-read.csv("c:/baseball09/runs.csv")
> runs
            Team  W  L  G AEQR AEQRA    EQRPG   EQRAPG
1         Tampa Bay 52 44 96  542   429 5.645833 4.468750
2  New York Yankees 58 37 95  540   453 5.684211 4.768421
3               LAA 56 38 94  531   483 5.648936 5.138298
4               BOS 55 39 94  500   426 5.319149 4.531915
5               CLE 38 58 96  482   535 5.020833 5.572917
6               TOR 47 49 96  473   442 4.927083 4.604167
7               MIN 48 48 96  473   449 4.927083 4.677083
8               PHI 54 39 93  472   449 5.075269 4.827957
9             Texas 52 41 93  469   442 5.043011 4.752688
10         Colorado 52 43 95  467   424 4.915789 4.463158
11              LAD 61 34 95  464   368 4.884211 3.873684
12              BAL 41 53 94  445   490 4.734043 5.212766
13              MIL 48 47 95  443   480 4.663158 5.052632
14              CHW 50 45 95  442   438 4.652632 4.610526
15              ARZ 41 55 96  439   460 4.572917 4.791667
16       Washington 28 67 95  430   493 4.526316 5.189474
17              DET 49 44 93  412   424 4.430108 4.559140
18              ATL 49 47 96  408   382 4.250000 3.979167
19              OAK 40 54 94  407   429 4.329787 4.563830
20              HOU 49 46 95  404   442 4.252632 4.652632
21              STL 52 46 98  402   389 4.102041 3.969388
22              SEA 51 44 95  401   377 4.221053 3.968421
23              FLA 49 47 96  394   421 4.104167 4.385417
24              NYM 44 50 94  393   412 4.180851 4.382979
25              PIT 42 53 95  389   442 4.094737 4.652632
26              CHC 48 45 93  378   388 4.064516 4.172043
27               KC 37 57 94  376   429 4.000000 4.563830
28               SD 37 59 96  369   461 3.843750 4.802083
29       Cincinnati 44 50 94  362   428 3.851064 4.553191
30               SF 51 44 95  351   374 3.694737 3.936842

> attach(runs)
> if (Team=="Texas") {Team<-"TEX"}
Warning message:
In if (Team == "Texas") { :
  the condition has length > 1 and only the first element will be used
```I'm still stuck in my SAS way of thinking.

---

### Post by gunksta on 2009-08-16
I should have asked for your syntax upfront. Would have saved a lot of time. The attached .r file shows two different ways to change "Texas" to "TEX". For consistency, I created a data file from chino cochino's posted syntax. On my computer, the syntax in this .r file works find. YMMV.

The attached syntax is documented, but there are a couple of things I should point out. attach() is a tricky command to use. I tend to avoid it. It seems nice at first, but many consider it to be a pain in the tail.

Finally, I should mention that R is a funky little language. It is _very_ good at somethings, and less so at others. R is perfectly good at doing this, but it's not necessarily the first tool I would reach for. I avoid doing complex data munging and data manipulation in R itself. There are times where some of R's structures and conveniences get in the way when doing data munging (in my opinion). For example, this task could be easily done with sed rather than with R since the data already exists as a text file.

Here's my "typical" work-flow: I usually start with some kind of .csv or .txt file (tab-delimited). When life sucks, I'll start with an Access Database. From there I will do any basic alterations to the data, such as change "Texas" to "TEX" while the data is still in a plain text format. Once this is done, I import the data into PostgreSQL.  Postgre does a terrific job managing the data. This is an unnecessary step with small data sets, but most of my data sets are quite a bit larger than this. R is easy to connect to Postgres and I will only import the data into R that I want to analyze. The rest of it can stay in Postgres. This works especially well since I have a separate Postgres server at work and I just run R on my aging laptop. It all works faster when I can throw multiple processors at the problem.

Let me know if this works syntax works for you. 

Note: The syntax and the .csv are in the tar.gz attachment.

---

### Post by ahmatti on 2009-08-18
Nice work Gunksta,
I think though you should use "gsub" instead of "sub", because "gsub" replaces all occurrences and "sub" only the first one. Using substitution is a better way than setting new factor labels, as I suggested before, when you have this many levels and most of them are already in correct format. 

Also I would use runs2.df$Team, rather than runs2.df[,"Team"], but thats just a matter of taste of course.  

I do most of my data handling in R, because I tend work with a lot of files with similar format and in that way I can also easily redistribute the whole analysis with the original data file even for Windows users. Most of the time I just need to do some regular expressions to reformat the data and R is perfectly capable of doing that. 

**@chino cochino**
In case you didn't realize why Gunksta's first suggestions fails I'm going to repeat what I said earlier : you were trying to modify a vector of factors which is (sometimes) different from working with strings. You can find out what the type of your variable with the class command. So using Gunkstas data and second example:

```

runs <- read.csv('runs.csv')
#See the class
class(runs$Team)
[1] "factor"
#Change the type to character (=string)
runs$Team <- as.character(runs$Team)
class(runs$Team)
[1] "character"

```

After the conversion the following should work:

```

 runs$Team[runs$Team=="Texas"] <- "TEX"

```

Actually most a lot of my problems that I used to have when I started using R were related to having the "wrong" variable type. Often doing a simple check using "class" gives you a hint on where the problem is. It is not uncommon for R to read in numeric variables as factors when using read.table either, which can also cause some hassle if you don't notice it.

---

### Post by euler_fan on 2009-08-18
Suggest you look at the ifelse construction. It was designed to perform logical operations on elements of a vector. Although there are a number of excellent methods appropriate to your case, it is a nice tool to understand.

---

### Post by gunksta on 2009-08-18
> **ahmatti said:**
> 
I think though you should use "gsub" instead of "sub", because "gsub" replaces all occurrences and "sub" only the first one. 

I tend to be very cautious with commands/tools like gsub. Perhaps overly so. I've been bitten in the tail more than once working with large data sets after applying a global substitution.

> **ahmatti said:**
> 
I do most of my data handling in R, because I tend work with a lot of files with similar format and in that way I can also easily redistribute the whole analysis with the original data file even for Windows users. Most of the time I just need to do some regular expressions to reformat the data and R is perfectly capable of doing that. 

That is an excellent point. Using an external database isn't as portable and in many environments it is important to support legacy systems. :P

---

### Post by ahmatti on 2009-08-19
> **gunksta said:**
> I tend to be very cautious with commands/tools like gsub. Perhaps overly so. I've been bitten in the tail more than once working with large data sets after applying a global substitution.

That is an excellent point. Using an external database isn't as portable and in many environments it is important to support legacy systems. :P

I made a mistake, sorry! I thought that sub only replaces the first occurrence in the vector, but it actually replaces the first occurrence in each element of the vector, so its perfectly fine here and safer than gsub. I agree that its very easy to get unwanted behavior with substitutions...

---

### Post by chino cochino on 2009-08-19
> **gunksta said:**
> I should have asked for your syntax upfront. Would have saved a lot of time. The attached .r file shows two different ways to change "Texas" to "TEX". For consistency, I created a data file from chino cochino's posted syntax. On my computer, the syntax in this .r file works find. YMMV.

The attached syntax is documented, but there are a couple of things I should point out. attach() is a tricky command to use. I tend to avoid it. It seems nice at first, but many consider it to be a pain in the tail.

Finally, I should mention that R is a funky little language. It is _very_ good at somethings, and less so at others. R is perfectly good at doing this, but it's not necessarily the first tool I would reach for. I avoid doing complex data munging and data manipulation in R itself. There are times where some of R's structures and conveniences get in the way when doing data munging (in my opinion). For example, this task could be easily done with sed rather than with R since the data already exists as a text file.

Here's my "typical" work-flow: I usually start with some kind of .csv or .txt file (tab-delimited). When life sucks, I'll start with an Access Database. From there I will do any basic alterations to the data, such as change "Texas" to "TEX" while the data is still in a plain text format. Once this is done, I import the data into PostgreSQL.  Postgre does a terrific job managing the data. This is an unnecessary step with small data sets, but most of my data sets are quite a bit larger than this. R is easy to connect to Postgres and I will only import the data into R that I want to analyze. The rest of it can stay in Postgres. This works especially well since I have a separate Postgres server at work and I just run R on my aging laptop. It all works faster when I can throw multiple processors at the problem.

Let me know if this works syntax works for you. 

Note: The syntax and the .csv are in the tar.gz attachment.

Gunksta,
I tried to open up the winzip file but after R loaded nothing came up. Sorry for sounding so elementary, but is there syntax required to open the file?

---

### Post by unutbu on 2009-08-19
chino cochino, the runs.tar.gz file can be opened double-clicking on it using your file browser. This will create a directory called runs. Inside the runs directory you will find the .r file. 

If you'd like to open the tar.gz file from the terminal, the command is 
```

tar xvzf runs.tar.gz
```

Or, perhaps better, you can save this in your ~/.bashrc file:

```
# Extract files from any archive
# Usage: op <archive_name>
# Thanks to rezza at Arch Linux 
# You may need to install some of these archiving formats. 
op () {
     if [ -f $1 ] ; then
        case $1 in
                *.tar.bz2)   tar xvjf $1 ;;
                *.tar.gz)    tar xvzf $1 ;;
                *.bz2)       bunzip2 $1 ;;
                *.rar)       unrar x $1 ;;
                *.gz)        gunzip $1 ;;
                *.tar)       tar xvf $1 ;;
                *.tbz2)      tar xvjf $1 ;;
                *.tgz)       tar xvzf $1 ;;
                *.zip)       unzip $1 ;;
                *.Z)         uncompress $1 ;;
                *.7z)        7z x $1 ;;
                *)           xdg-open $1 ;;
        esac
     else
        echo "'$1' is not a valid file"
     fi
}
```

Then open a new terminal (so the change to .bashrc becomes effective) and then you can open just about anything with the short and sweet command
```

op runs.tar.gz
```

---

### Post by PGScooter on 2009-08-20
cool function unutbu, thanks.

---

### Post by chino cochino on 2009-08-20
> **ahmatti said:**
> Nice work Gunksta,


**@chino cochino**
In case you didn't realize why Gunksta's first suggestions fails I'm going to repeat what I said earlier : you were trying to modify a vector of factors which is (sometimes) different from working with strings. You can find out what the type of your variable with the class command. So using Gunkstas data and second example:

```

runs <- read.csv('runs.csv')
#See the class
class(runs$Team)
[1] "factor"
#Change the type to character (=string)
runs$Team <- as.character(runs$Team)
class(runs$Team)
[1] "character"

```After the conversion the following should work:

```

 runs$Team[runs$Team=="Texas"] <- "TEX"

```Actually most a lot of my problems that I used to have when I started using R were related to having the "wrong" variable type. Often doing a simple check using "class" gives you a hint on where the problem is. It is not uncommon for R to read in numeric variables as factors when using read.table either, which can also cause some hassle if you don't notice it.
thanks, I'll try that.

---

### Post by gunksta on 2009-08-26
I was asked to post the syntax from my previous entry in this thread. When I looked at it, it is clear that something went terribly awry when I made the tar.gz file. (Ark in KDE 4.2 has been a little flakey). Here's the syntax:

```
# Clean everything up.
rm(list=ls())

#############################################################
# This is one way to do it.

# Import the data.
# R converted the column, "Team" to a factor which made 
# things more difficult when changing the values.
# as.is="Team" tells R to not convert these values to 
# factors, which makes our lives easier.
runs.df<-read.csv("runs.csv", as.is="Team")

# Which rows are equal to "Texas"
change<-which(runs.df[,"Team"]=="Texas")

#Assign "TEX" to those rows equal to "Texas"
runs.df[change,"Team"]<-"TEX"

# It's worth noting that factors are a useful feature in R.
# If I was going to do much to my data, I would definitely
# convert Team to a factor variable once I was done 
# Changing things up . . . . OR . . . . . 


##########################################################
# This is an anothe way to do the same thing.
# It's shorter and easier to read.

# Import the data.
runs2.df <- read.csv("runs.csv")

# Replace "Texas" with "TEX"
# Note that I did not bother with as.is="Team" here.
# This works on a factor, string, whatever.
runs2.df[,"Team"] <- sub("Texas","TEX",runs2.df[,"Team"])

# The second syntax is really easier to use and is what
# I should have recommended the first time.

```

If you'd like to run this syntax, you'll need a runs.csv file, which you can create with this:

"Team","W","L","G","AEQR","AEQRA","EQRPG","EQRAPG"
"Tampa Bay",52,44,96,542,429,5.65,4.47
"New York Yankees",58,37,95,540,453,5.68,4.77
"LAA",56,38,94,531,483,5.65,5.14
"BOS",55,39,94,500,426,5.32,4.53
"CLE",38,58,96,482,535,5.02,5.57
"TOR",47,49,96,473,442,4.93,4.6
"MIN",48,48,96,473,449,4.93,4.68
"PHI",54,39,93,472,449,5.08,4.83
"Texas",52,41,93,469,442,5.04,4.75
"Colorado",52,43,95,467,424,4.92,4.46
"LAD",61,34,95,464,368,4.88,3.87
"BAL",41,53,94,445,490,4.73,5.21
"MIL",48,47,95,443,480,4.66,5.05
"CHW",50,45,95,442,438,4.65,4.61
"ARZ",41,55,96,439,460,4.57,4.79
"Washington",28,67,95,430,493,4.53,5.19
"DET",49,44,93,412,424,4.43,4.56
"ATL",49,47,96,408,382,4.25,3.98
"OAK",40,54,94,407,429,4.33,4.56
"HOU",49,46,95,404,442,4.25,4.65
"STL",52,46,98,402,389,4.1,3.97
"SEA",51,44,95,401,377,4.22,3.97
"FLA",49,47,96,394,421,4.1,4.39
"NYM",44,50,94,393,412,4.18,4.38
"PIT",42,53,95,389,442,4.09,4.65
"CHC",48,45,93,378,388,4.06,4.17
"KC",37,57,94,376,429,4,4.56
"SD",37,59,96,369,461,3.84,4.8
"Cincinnati",44,50,94,362,428,3.85,4.55
"SF",51,44,95,351,374,3.69,3.94

I hope this helps.

---

