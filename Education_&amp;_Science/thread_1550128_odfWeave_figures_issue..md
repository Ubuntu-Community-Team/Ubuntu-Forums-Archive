---
title: "odfWeave figures issue."
date: 2010-08-10
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2010-08-10
Hi, I'm doing some basic results stuff for some coursework and was trying to do it in odfWeave for R. In the document I have a chunk of code to start with that loads datasets and such and sets up a workspace, then a line of normal text, then some code chunk where I wanted to actually start the analysis. The document goes thus (I've only just started it and run it through odfWeave to check everything was in order):

[CENTER]**_Data Analysis_**[/CENTER]
<<echo=FALSE>>=
library( lattice )

QuadratData <- read.table( "~/Documents/BSc Biology/Second Year/Research Methods/Ireland Trip/Data and Analysis/RNuts.csv", header=T )

NutFrequency <- read.table( "~/Documents/BSc Biology/Second Year/Research Methods/Ireland Trip/Data and Analysis/RChi.csv", header=T )

Adata = subset( QuadratData, site=='A' )
Bdata = subset( QuadratData, site=='B' )
Cdata = subset( QuadratData, site=='C' )
@

_Analysis of the Light penetration levels in the three different sites:_

<<echo=FALSE, fig=TRUE>>=
bwplot( QuadratData$penetration~QuadratData$site, ylab="Light Penetration (%)", xlab="Site" )
@

But when I run it through odfWeave with:


> library(odfWeave)
> file.in <- "~/Documents/Squirrel.odt"
> file.out <- "~/Documents/Squirrelout.odt"
> imageDefs <- getImageDefs()
> imageDefs$dispWidth <- 4.5
> imageDefs$dispHeight<- 4.5
> setImageDefs(imageDefs)
> odfWeave(file.in, file.out)

And the image shows the icon of a broken image and says Read-Error.
I'm only using R and such for basic results analysis for my Biology coursework, nothing overly fancy or convoluted. And what I'd done seemed simple enough so I'm at a loss of what's wrong.

Cheers.
Ben.

[EDIT]

SOLVED! this is how it was done:

<<echo=FALSE, fig=TRUE>>=
plot(bwplot( QuadratData$penetration~QuadratData$site, ylab="Light Penetration (%)", xlab="Site" ))
@

This was because I was using the lattice package.

---

