---
title: "QtiPlot Scripting Help (total noob)"
date: 2009-12-21
forum: Education &amp; Science
---

### Post by slapfish on 2009-12-21
hello everyone,

I'm trying to build 1 or 2 scripts but I can't get enough help from the qtiplot manual and furthermore I do not have any programming experience other than altering existing codes. 

the first thing I'm trying to do is make some calculations by picking points on a graph with data reader. The code should look (I think) like that:


```

include some libraries (which???)

use data reader (how???) and get the values: (tablename_colYname[rownumber]: xVal ; yVal) 

t = table(tablename)    #select the graphs table, if necessary

if t.numCols() < 3 : end     # if the table has less than 3 columns end

if xVal: end          # if the xVal of the selected point is 0 end

v = t.cell(3, 12)        #when I import my data, in this cell I get the frequency I need for the calculation

g = 714.48*v/xVal

print g to resultsLog() (how?)
copy g to clipboard       (how?)


```the second one is to pick two points on a graph with the screen reader and do some calculations with both xvalues and yvalues. I guess that if I get some help with the first one the only thing I'll be missing for the second will be how to get the values from the screen reader.

I would be REALLY grateful for any help here,
Kind regards
Dmtri


P.S. I'm trying to get rid of windows and work for my phd on linux and that two "blocks" are the last to pass. (I have a custom toolbar for origin that it was given to me by my proff that does the job)

---

