---
title: "So, anyone digs Principal Components Analysis?"
date: 2008-05-16
forum: Education &amp; Science
---

### Post by aimran on 2008-05-16
I don't know if this is the right sub-forum so mods feel free to move this to the appropriate section :)

Principal Components Analysis (PCA) is a data analysis method famous for dimensionality reduction and pattern seeking. I've been toying around with an algorithm I created from the description given by Danilov[1] for time series forecast. 

[IMG]http://watafak.com/aimran/POD.png[/IMG]

I did a prediction of a time series after point 120 of the red line. The dotted blue line is the prediction. As can be seen, the prediction is offset by a bit, but shows the appropriate trend :P

I don't need help fixing this :P. Just wanted to show off  something cool. Anyone else toyed with PCA before? 

Of course, the next step is stock market prediction :guitar:

---

### Post by luca.b on 2008-05-18
I use PCA all the time when dealing with biological data coming from high-throughput analyis. It's the first step in identifying outliers and see if everything worked as it should.

---

### Post by aimran on 2008-05-18
Did you publish anything?

---

### Post by K.Mandla on 2008-05-18
Moved to OMG Pink Ponies.

---

### Post by DrOlaf on 2008-05-18
> **aimran said:**
> Did you publish anything?

I don't know if luca.b is one of the authors of these papers, but there were two papers published in this month's issue of *Nature Genetics* that use PCA to re-assess the patterns of genetic variation reported in Cavalli-Sforza's *The History and Geography of Human Genes*. Unfortunately you need to be able to access the journal website from a college campus machine, unless you have a personal subscription, but here are the links:

Paper: [Interpreting principal component analyses of spatial population genetic variation]("http://www.nature.com/ng/journal/v40/n5/abs/ng.139.html")

Commentary: [Principal Component analysis of genetic data]("http://www.nature.com/ng/journal/v40/n5/abs/ng0508-491.html")

I have used PCA, and its cousin Multidimensional Scaling, in the past to do analyses like this and it's a powerful tool.

You may want to ask your question in the Education and Science subforum as well - I see quite a lot of people posting in there on topics like this, who I have never seen in OMGPP.

---

### Post by mips on 2008-05-18
> **K.Mandla said:**
> Moved to OMG Pink Ponies.

Probably more appropriate over here, [http://ubuntuforums.org/forumdisplay.php?f=169](http://ubuntuforums.org/forumdisplay.php?f=169)  Education & Science forum.

---

### Post by aimran on 2008-05-18
Thank you DrOlaf. This thread was originally in the cafe but the mods moved it here. I have to agree with all who've said this belongs in the Edu&Sci section.

---

### Post by LaRoza on 2008-05-18
> **aimran said:**
> I have to agree with all who've said this belongs in the Edu&Sci section.

Moved

---

### Post by aimran on 2008-05-18
Thank you :)

---

### Post by kleeman on 2008-05-19
PCA is used a lot in the earth sciences particularly in atmospheric science, physical oceanography and climate science. It is referred to there as EOF analysis. Basically you take all your data and work out the covariance between all variables. The eignvectors of the this matrix are the PCs or EOFs. The eigenvalues tells you how much of the total variance each PC explains. Often very few PCs explain a lot of the total variance so they are a very powerful way of reducing the dimensionality of the data.

---

### Post by earlycj5 on 2008-05-20
I've used it for remote sensing modeling.

Not very extensively though.  Pretty neat stuff.  You can find some very interesting things using it.

---

### Post by aimran on 2008-05-20
Glad to see lots of people using PCA :D. Would be great if we decorated this section with pictures :P :D! I'll post more of my results here after I've submitted my paper. And of course, my code...

---

### Post by earlycj5 on 2008-05-20
> **aimran said:**
> Glad to see lots of people using PCA :D. Would be great if we decorated this section with pictures :P :D! I'll post more of my results here after I've submitted my paper. And of course, my code...

I'll dig around my hard drive, I should still have results from last fall doing PCA on vegetation patterns based on NDVI in South America.  It was quite pretty.

---

### Post by earlycj5 on 2008-05-22
I've uploaded my images. 
 
[http://www.flickr.com/photos/earlycj5/tags/pca/](http://www.flickr.com/photos/earlycj5/tags/pca/)

PCA 4 was the component I picked for the excercise as describing the most variability.  Never got any feedback on the assignment, I got an A in the class though, guess that's good enough.

[[img]http://farm4.static.flickr.com/3246/2513176855_85928e898b_m.jpg[/img]](http://www.flickr.com/photos/earlycj5/2513176855/)

Loading graphs are there on my Flickr site with the PCA tag as well.

---

### Post by aimran on 2008-05-23
What program did you use to do these? These are amazing :)

---

### Post by earlycj5 on 2008-05-23
> **aimran said:**
> What program did you use to do these? These are amazing :)

The maps were made with Clark Labs IDRISI-Andes remote sensing software, [http://www.clarklabs.org/](http://www.clarklabs.org/) .

The graphs were of course generated in R from the data from IDRISI.

---

### Post by NikoC on 2008-05-25
In the lab ([http://www.ecotox.be]("http://www.ecotox.be")) I do my phd in a lot of people are using PCA, especially those who are conducting field studies...

I myself only use simple testing (correlation, t-test, one/two way ANOVA) at the moment...

---

### Post by brunovecchi on 2008-05-27
I used PCA in my degree thesis, to analyze the changes of in the electrophoretic pattern of a complex mixture of proteins in time when being hydrolyzed. I liked it a lot. I remember using MatCad for that (I hadn't switched to linux yet).
A friend of mine uses it to study a complex microbial community of yeasts.

---

### Post by Bakke on 2008-07-15
Hi everyone. I'm doing my field research for my Industrial Engineer title and the work concerns the usage of PCA on data related to wine fermentations, specifically on Cavernet Sauvignon. I just started applying PCA on a huge amount of data (near 22.000) PCA must be used in order to detect fermentation problems over 22 compounds.

I'd like to share my progress if anyone's interested.

See ya :)

---

### Post by earlycj5 on 2008-07-15
> **Bakke said:**
> Hi everyone. I'm doing my field research for my Industrial Engineer title and the work concerns the usage of PCA on data related to wine fermentations, specifically on Cavernet Sauvignon. I just started applying PCA on a huge amount of data (near 22.000) PCA must be used in order to detect fermentation problems over 22 compounds.

I'd like to share my progress if anyone's interested.

See ya :)

That certainly sounds interesting, both as a scientist and someone who appreciates a fine wine.

---

### Post by bite on 2008-07-15
Suppose you have a cloud of thousands of 2D points and you know that they belong to just two different straight lines. Can PCA be used to get the equations of the lines? (ie a1 x + b1 y + c1 = 0, a2 x + b2 y + c2 = 0)

---

### Post by ursulamojo on 2008-07-17
> **kleeman said:**
> PCA is used a lot in the earth sciences particularly in atmospheric science, physical oceanography and climate science.

i'm a geologist, and i work with paleoclimate and oceanographic data...what programs do you (and others) commonly use for PCA?  i learned PCA using SPSS because that's what is available to me, is there a program similar to it in ubuntu?

---

### Post by earlycj5 on 2008-07-18
> **ursulamojo said:**
> i'm a geologist, and i work with paleoclimate and oceanographic data...what programs do you (and others) commonly use for PCA?  i learned PCA using SPSS because that's what is available to me, is there a program similar to it in ubuntu?

R does PCA, [http://rss.acs.unt.edu/Rdoc/library/pcaMethods/html/00Index.html](http://rss.acs.unt.edu/Rdoc/library/pcaMethods/html/00Index.html)

---

### Post by aimran on 2008-07-21
> **bite said:**
> Suppose you have a cloud of thousands of 2D points and you know that they belong to just two different straight lines. Can PCA be used to get the equations of the lines? (ie a1 x + b1 y + c1 = 0, a2 x + b2 y + c2 = 0)

PCA was originally intended by its discoverer, Karl Pearson, as a method to find the line of best fit. Is the line of best fit what you mean? 

I can only point you in that direction. I can't remember the math of PCA for line of best fit.

---

### Post by aimran on 2008-07-21
> **ursulamojo said:**
> i'm a geologist, and i work with paleoclimate and oceanographic data...what programs do you (and others) commonly use for PCA?  i learned PCA using SPSS because that's what is available to me, is there a program similar to it in ubuntu?

I programmed my PCA routine in Matlab. My code is easily transferred to Octave. I can't provide the program to you now as I have misplaced the USB I put it on, but roughly:

```

A = input data;
B = A*A'; (autocorrelate the data)
C = B - mean(B);
E,D = eig(C); (E = eigenvalues, D = eigenvectors)

```

And there you have it is your principal components in their most basic form. Note that my PCA routine was performed on singular spectrum data (SSD) for example: stock markets, daily temperature variation, and the like.

I would imagine that PCA for multidimensional data (like a set of facial images) would require you to compute up to B in the above program for each individual data set. For example you should autocorrelate each image of a facial snapshot of your whole classroom for each pupil.

Continuing from the above example would be taking the pixel to pixel mean. Starting from the top-left most pixels of each autocorrelated images, you take a mean of each pupils autocorrelated image. Doing this for each pixel would net you a "mean face" so to say.

I'm just theorising. I have no experience in multidimensional PCA. Hope it helps.

---

### Post by mj_ja55 on 2008-07-22
I use PCA to analyze global metabolic changes in yeast.  Specifically, in a yeast model of a neurodegenerative disease.  I am currently using MS Excel add-in to run the PCA (XLSTAT), but I am very interested in learning how to do PCA in R.  I still haven't really learned the basics of R yet, but I hope to get around to it soon.  I think it is really cool to see so many scientists using Ubuntu AND doing PCA!

---

