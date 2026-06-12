---
title: "Graphing Software"
date: 2012-10-02
forum: Education &amp; Science
---

### Post by Tk007LwZFJW5ej on 2012-10-02
Is there graphing software available that would allow me to graph the little empty circles (or some other recognizable symbolism) at points where the function is discontinuous? See the picture for what I mean.

[IMG]http://www.worsleyschool.net/science/files/discontinuous/d04.jpg[/IMG]

---

### Post by bryncoles on 2012-10-11
Hi StarKid.  

You could do that in [R](http://cran.r-project.org/).  It's a very powerful statistical analysis software, with a particular strength in making graphs.  I know people in the past to have made very powerful and complicated graphs using this software.  

It's a bit of a steep learning curve though!  You can use the following three web pages to help get you started if you like though

[http://en.wikibooks.org/wiki/Statistical_Analysis:_an_Introduction_using_R](http://en.wikibooks.org/wiki/Statistical_Analysis:_an_Introduction_using_R)
[http://en.wikibooks.org/wiki/R_Programming](http://en.wikibooks.org/wiki/R_Programming)
[http://scs.math.yorku.ca/index.php/R:_Getting_started_with_R](http://scs.math.yorku.ca/index.php/R:_Getting_started_with_R)

To install R, search synaptic (or the Ubuntu Software Centre actually) for r-base and install that.  To run R, simply (!) open a terminal and type ```
R
``` 

That took me ages to work out when I first started using R! 

Post back here (or start a new thread) if you need further help. 

Oh -- and since Googling for 'R' is a pain in the Rs, you might like to try using the [r-seek](http://www.rseek.org/) website instead.  

Good luck!

---

### Post by PC_load_letter on 2012-10-11
If the OP would like to program R from a nice GUI, the open-source project RStudio from [www.rstudio.org](www.rstudio.org) provides a deb binary package for Ubuntu, it works like a charm once you install R from Ubuntu repos.

---

### Post by bryncoles on 2012-10-12
I used to use Rcmdr, but Rstudio looks nice too!

---

### Post by Information Technology on 2012-10-12
> **StarKid said:**
> Is there graphing software available that would allow me to graph the little empty circles (or some other recognizable symbolism) at points where the function is discontinuous? See the picture for what I mean.]

Hi,

I recommend you take a look at a new javascript library that has been evolving very rapidly, called "D3.js".  It stands for "Data Driven Documents" and it allows you to build some pretty amazing graphical representations that render and run directly in your browser.  So, if you know how to set up a web server and perform an http request for data, you can pull the data back into the browser and then manipulate it to any type of graphical representation you'd like.  This makes it easy for you to share your visualizations with other people that need to see them (especially if you're doing this at work).  Once you have the data, you can build any visualization you want, including your disjointed graph.

Here are some examples...

[LIST]
[*][Interactive Pie Charts]("http://bl.ocks.org/2212156") (Complexity = Simple)
[*][Interactive Bar Charts]("http://bl.ocks.org/2141479") (Complexity = Simple)
[*][Interactive Radial Browser]("http://bl.ocks.org/3169420") (Complexity = High)
[*][Interactive Graph]("http://bl.ocks.org/2879486") (Complexity = Moderate)
[/LIST]

You can find tons more examples, like the graph your trying to build at [D3js.org]("http://d3js.org/").

I hope this helps and you find it useful because this library was VERY useful for me.

My Best

---

