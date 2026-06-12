---
title: "Problem plotting series"
date: 2008-09-18
forum: Education &amp; Science
---

### Post by gvanto on 2008-09-18
I use the following code to load a stock with some serie (from a csv file, attached as zip) into an data.frame
[I quite like this little function - feel free to steal it and provide some tips as to more stuff to do with stocks!]

Now, and column starting with
The problem is when I call the security.plot() method, the price-series (sec$close is plotted fine), but when it comes to plotting the indicator (any column whose name is starting with "i_") I get this error: (it used to work OK, but I must have changed something in the meantime but I have no idea what it was!)

> 
Warning messages:
1: In x[["y"]] : partial match of 'y' to 'year'
2: further partial match of 'y' to 'yday' 
3: In x[["y"]] : partial match of 'y' to 'year'
4: further partial match of 'y' to 'yday' 




```


###################
#security.R script
###################
security <- function(x, ...) {
	UseMethod("security");
	
}

security.get <- function(filename) {
	s = NULL
	l = system(paste("ls ", filename), intern=T);
	if(length(l) == 0) {
		cat("file does not exist");
	}
	else {
		s <- read.csv(filename);		
	}
	s$sec_name = filename
	s
}

#See page 76 of R-intro.pdf for options here
security.plot <- function(sec, plotname) { 
	par(las=2)
#par(lab=c(6, 10, 8), las=2)
	
	plot(as.POSIXlt(sec$date),sec$close,type="l", main=plotname);
	
	col_list = list("blue", "green", "grey"); #colour_list
	
#	add each indicator to plot:
	name_list = names(x);
	indic_list = list();
	for(i in 1:length(name_list)) {
		res = charmatch("i_", name_list[i], nomatch=-1);
		if( res > 0 ) { # i_ was found!
			indic_list <- append(indic_list, name_list[i]);
		}
	}
	
	if(length(indic_list) > 0) {
		for(i in 1:length(indic_list)) {
			lines(as.POSIXlt(sec$date),sec[[ indic_list[[i]] ]],type="l", col=col_list[[i]]);
		}
	}
	
}


```

help much appreciated!
Gerry
R-plotting newbie

---

### Post by hubie on 2008-09-20
It looks like your line
```
name_list = names(x)
```
should be
```
name_list = names(sec)
```

Another thing I noted, and you might not care about this because it works for you now, is that your [FONT="Fixedsys"]security.get[/FONT] routine is localized to linux, with the use of the [FONT="Fixedsys"]ls[/FONT] command.

A couple of alternatives you might want to use is the [FONT="Fixedsys"]file.exists[/FONT] procedure, or to wrap the csv read in a [FONT="Fixedsys"]try[/FONT].  For example:
```
security.get <- function(filename) {
	s = NULL
	if (file.exists(filename)) {
		s <- read.csv(filename)
	}
	s$sec_name = filename
	s
} 
```
or
```
security.get <- function(filename) {
	s = NULL
	try(s <- read.csv(filename), FALSE)

	s$sec_name = filename
	s
} 
```
The advantage of using [FONT="Fixedsys"]try[/FONT] is that it will kick back the error (if you want it to) as to why the file didn't open.

---

### Post by gvanto on 2008-09-21
Hi hubie,

Wow this was such a schoolboy error of mine, having x instead of sec !!
Thanks alot for the pointout and for the cool advice on the try file open (didn't know try existed for R).

I'm using RKward and was wondering if there's a way to break code and step through it (this would be such an awesome feature if it exists!).

Are you into trading Hubie? You wouldn't happen to know if there's like some library for plotting OpenHighLowCloseVolume data for stocks (say, fetched from yahoo or whatever) - any idea where one would start looking for this?

I'm really liking R but the code step-through would be REALLY great.

Best,
Gerry

---

### Post by hubie on 2008-09-22
Sorry, I can't help you with RKward.  I'm a crufty old fart who prefers to work on the command line. :)

R does have debugging capabilities.  [This page]("http://www.stats.uwo.ca/faculty/murdoch/software/debuggingR/") is devoted to debugging in R.  You can start with [FONT="Fixedsys"]help("debug")[/FONT], which is what you'd use to step through programs.

I'm not a big trading guy, but there does look to be lots of good stuff on [Sourceforge]("http://sourceforge.net/search/?type_of_search=soft&words=stock+market") and [Freshmeat]("http://freshmeat.net/search/?q=stock+market&section=projects&Go.x=0&Go.y=0").

---

### Post by gvanto on 2008-09-23
Cool thanks alot Hubie - some good resources there.

ACtually working from the command line isn't so bad - RkWard for example crashes alot when using external plotting libraries like iPlot

G

---

