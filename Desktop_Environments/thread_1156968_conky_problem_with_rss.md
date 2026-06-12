---
title: "conky problem with rss"
date: 2009-05-12
forum: Desktop Environments
---

### Post by yuki86 on 2009-05-12
Hi im using this script for conky:

```
#!/usr/bin/perl -w

############################
# Creator: Jeff Israel
#
# Script:	./simple-rss-reader-v3.pl
# Version: 	3.001
#
# Coded for for Wikihowto http://howto.wikia.com
#
# Description: 	This code downloads an RSS feed, 
# 		extracts the <title> lines,
# 		cleans them up lines,
# 		prints the pretty lines
# 		exits on max-lines
# Usage:
# .conkyrc: ${execi [time] /path/to/script/simple-rss-reader-v3.pl}
#
# Usage Example
# ${execi 300 /path/to/script/simple-rss-reader-v3.pl}
#

use LWP::Simple;


############################
# Configs
#

#$rssPage = "http://www.mobilmania.cz/rss/sc-47/default.aspx";
$rssPage = "http://www.mobilmania.cz/rss/sc-47/default.aspx";
$numLines = 10;
$maxTitleLenght = 35;

###########################
# Code
#

# Downloading RSS feed
my $pageCont = get($rssPage);

# Spliting the page to lines
@pageLines = split(/\n/,$pageCont);

# Parse each line, strip no-fun data, exit on max-lines
$numLines--; #correcting count for loop
$x = 0;
foreach $line (@pageLines) {
	if($line =~ /\<title\>/){ # Is a good line?
		#print "- $line\n";
		$lineCat = $line;
		$lineCat =~ s/.*\<title\>//;
		$lineCat =~ s/\<\/title\>.*//;
		$lineCat =~ s/\[.{4,25}\]$//; # strip no-fun data ( [from blaaa] )
		$lineCat = substr($lineCat, 0, $maxTitleLenght);
		print "- $lineCat \n";
		$x++;
	}
	if($x > $numLines) {
		last; #exit on max-lines
	}
	
}

#print $page;
#print "\nBy Bye\n";
```

and i have problem that there is double title (see my picture) rss is [http://www.mobilmania.cz/rss/sc-47/default.aspx](http://www.mobilmania.cz/rss/sc-47/default.aspx)

[[IMG]http://img83.imageshack.us/img83/4285/conkyrss.th.png[/IMG]](http://img83.imageshack.us/my.php?image=conkyrss.png)

thanks a lot

---

### Post by yuki86 on 2009-05-14
bump

---

