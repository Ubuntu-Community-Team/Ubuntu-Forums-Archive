---
title: "Sorting a jumbled face using Matlab"
date: 2009-01-26
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2009-01-26
I am developing a matlab code for the problem.

I have a idea but would like to improve it and therefore would want to ask for opinions.

We are given a jumbled up image of a human face.
We have to arrange the face back into place.
We will be shown and given the randomized image. The randomized image in general will comprise of parts(p's) 20(4X5,4X4...) parts. Dont expect it to be many.


My idea. I will use the face that the from face of an individual is symmetrical. Therefore i plan to take the p's and place them in random order, and 
check for symmetry. In brief i will take left hand side of image-right hand side of image. Calculate deviation and i will set the treshold value.

Any idea which iseasier to implement. I myself am not understanding how to make the code for doing the above.



Any reference websites that i can read and get something read.

---

### Post by jpkotta on 2009-01-28
That's an interesting problem.  

As I understand it, your idea only determines if a piece contains symmetry or not.  If you had an even number of pieces horizontally (e.g. 3x4), then you would expect none of them to be symmetrical.  More generally, you could determine if pieces are mirror images of each other, but that still doesn't determine where they go vertically.

I think no matter what you do, you need a test to see if you have arranged the pieces in the correct locations, i.e. a test that says whether an image is of a face vs. a scrambled face.

Assuming the number of pieces is fixed, maybe you could somehow characterize them (e.g. this is a lower left piece because there appears to be skin only in the upper right part of it).  Have tests for each piece location; each run each test on each piece; and choose the best match for each test.  

So how can you recognize an image of a face or a region of a face?  That I'm not so sure of.  I think a good potential idea is to use [eigenfaces]("http://en.wikipedia.org/wiki/Eigenface").  Maybe neural networks?

---

