---
title: "How to: Enzymes with Linux."
date: 2009-03-30
forum: Education &amp; Science
---

### Post by ENigma885 on 2009-03-30
I was searching for a program to plot a [[COLOR="Blue"]Michaelis-Menten[/COLOR]]("http://en.wikipedia.org/wiki/Michaelis-Menten") graph of [[COLOR="Blue"]Catalase[/COLOR]]("http://en.wikipedia.org/wiki/Catalase") vs. [[[COLOR="Blue"]Hydrogen peroxide[/COLOR]]("http://en.wikipedia.org/wiki/Hydrogen_peroxide")] as a substrate for a university mini-research. 
And it took me some days to find this one [[COLOR="Red"][SIZE="2"]_[SIZE="4"]BioGraph[/SIZE]_[/SIZE][/COLOR] (click to download)]("http://downloads.sourceforge.net/biograph/bioGraph_1.0.zip?modtime=1175679115&big_mirror=0") a pretty _simple_ and easy to use enzyme plotting program. Plots like 
[LIST=1]
[*]Michaelis-Menten [[COLOR="Blue"]enzyme kinetics[/COLOR]]("http://en.wikipedia.org/wiki/Enzyme_kinetics") (*Also it calculates MM constant Km and maximum velocity Vmax automatically and displays them on the graph*) , 
[*]pH and 
[*]temperature effects on the enzyme activity
[/LIST]
can be drawn in such a nice-looking graphs like those ones:-
[[IMG]http://img18.imageshack.us/img18/4124/mymm2.th.jpg[/IMG]](http://img18.imageshack.us/my.php?image=mymm2.jpg)
and
[IMG]http://webscripts.softpedia.com/screenshots/bioGraph-19639.png[/IMG]
I also face some [_problems_]("http://ubuntuforums.org/showthread.php?p=6436990#post6436990") to get it to work. But finally, it worked and here's how:
i'm not sure if i understand every step, a friend helped me, but here's wat i did:-

**1. **Installed Apache, PHP5, Imagemagick, and Gnuplot.
**2.** Checked Apache with [http://localhost/](http://localhost/) and i got "It works!".
**3.** ```
cd /var/www
```
**4.** ```
sudo chmod 777 .
```
**5.** Copied bioGraph extracted folder to /var/www
**6.** In an internet browser, probably Firefox, paste "http://localhost/bioGraph_1.0/"
**7.** Using ```
whereis gnuplot
``` and ```
whereis convert
``` to localize gnuplot and convert to c if there's a need to modify config.php
and in my case the defaults works fine;  /usr/bin/gnuplot and /usr/bin/convert correct places.
**8.** 1st run i got error log containing something like ```
Warning: chdir() [function.chdir]: No such file or directory (errno 2) in /var/www/bioGraph_1.0/mmgraph.php on line 32
Warning: fopen(/home/vimal/public_html/biograph/upload/tmp/file4646.dat) [function.fopen]: failed to open stream: No such file or directory in /var/www/bioGraph_1.0/mmgraph.php on line 34
```
**9.** In Terminal window ```
sudo gedit /var/www/bioGraph_1.0/config.php
```
Edited the temporary directories, last 3 lines, to ```
$TMP_DIR ="/var/www/bioGraph_1.0/tmp";

$CACHE_DIR ="/var/www/bioGraph_1.0/cache";

$URL_PATH = "http://localhost/bioGraph_1.0/cache";
```
**10.** WORKED PERFECTLY

*I'm sure it will help any biochemistry newbies overthere. Just thought of sharing it. =) *

---

### Post by nateperson on 2009-03-31
Nice,

On a similar point, I just found nice paper in pubmed couple of days ago,
>  PMID: 18031997 That may be of interest to people
Its a review paper, focusing on bacterial bioinformatic tools and databases.  

Just thought I'd chime in with some post lunch slump reading for anyone interested.

---

### Post by chev1n on 2011-11-03
It did indeed help! Thanks!

---

