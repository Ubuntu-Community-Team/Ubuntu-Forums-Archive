---
title: "Ubuntu 8.10 - XAMPP 1.7. - R 2.8.1"
date: 2009-02-23
forum: Desktop Environments
---

### Post by I106402 on 2009-02-23
Hi forum,


Newbie to Ubuntu & even more to "geek" forum...so my apologies if it does not comply exactly with forum posting guideline, I will try to make it as concise as possible...

I developed an application in R 2.8.1. ([www.r-project.org](www.r-project.org)) under Ubuntu 8.10 that I run within VirtualBox on my Mac OSX 10.5 (Intel core 2 duo 2GHZ)

I want to develop a web-based GUI for this application and for this I installed XAMPP 1.7 for linux (i.e. lampp). No issue till here. 

I run a command in the terminal that functions perfectly (it is R-specific, something like R CMD BATCH /path/input_file.txt /path/output_file.txt where input_file if a bunch of R-specific commands & it writes the output in a text file called output file on the path defined.)
I can run it under my user as well as under user "nobody", this is important since Apache installed via XAMPP runs under user "nobody" (or so it tells me when I open a .php file with command "echo exec('whoami');")

The problem I have is when I try to run the R command via a exec command in the .php file (so something like "exec('R CMD BATCH /path/input_file.txt /path/output_file.txt');") it creates the file "output.txt" (so no permission issue) but the content of this file is an error:

/usr/lib/R/bin/exec/R: symbol lookup error: /usr/lib/R/lib/libR.so: undefined symbol: gzopen64


I googled this & could not really get my head around. It seems some people had this error message with Apache but mentioning other libraries...& their solution was to simply delete the libraries which is not really an option for me.

So my best guess currently is that I need to modify two environment variables:
PATH >> to include /usr/lib/R/bin/exec/
LD_LIBRARY_PATH >> to include /usr/lib/R/lib/

so that Apache knows where R & R libraries are when I called them via my command line instruction.

Am I correct? & if so could someone tell me how to do this "permanently", i.e. so that everytime I login & start lampp these paths are included? (I googled this also but saw many different posts quite confusing to be honest, but probably my own limitation...?)

Has anyone got any other idea?


Any help would be greatly appreciated, I lost my weekend on this without any success till now


Thanks & regards,
J

---

### Post by geiv on 2010-02-12
Hi

I was getting the same error you mention. 
It may be something related to how R is executed from php. I tried 
the following example taken from 
[http://www.math.ncu.edu.tw/~chenwc/R_note/index.php?item=php&subitem=ex_1](http://www.math.ncu.edu.tw/~chenwc/R_note/index.php?item=php&subitem=ex_1)
and works:

<?
  $cmd = "echo 'argv <- \"ex_1.r\"; source(argv)' | " .
         "/usr/bin/R --vanilla --slave";
  $ret = system($cmd);
  echo $ret;
?>

I did not get any errors running the previous code, but I tried it in a 
server other than the server I was getting the error.

---

### Post by timmannn on 2011-04-10
I also had this problem while trying to install the R extension with Mediawiki, and using the default R package through 'apt-get install r-base'.    

I ended up resolving this by downloading the R source ([http://cran.r-project.org/sources.html](http://cran.r-project.org/sources.html) ) , and configure; make; make install. 

The one thing about the configure parameters, I used the parameter, '--with-x=no'.

---

