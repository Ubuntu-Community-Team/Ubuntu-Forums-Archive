---
title: "AD Model Builder"
date: 2008-04-21
forum: Education &amp; Science
---

### Post by kvk on 2008-04-21
Is anyone running AD Model Builder on Ubuntu (or any other distro, for that matter) and more importantly- has anyone ever written the code in parallel form to allow synchronous processing on a cluster?

---

### Post by kvk on 2008-04-23
I'll take that as a "no". :razz:

---

### Post by bite on 2008-04-23
I don't think I am running any AD Model Builder at present :) but just to know, *what* is an AD Model Builder? Wikipedia lists some tens of possible meanings for the two letters... maybe I *am* running an AD Model Builder without knowing :)

---

### Post by kvk on 2008-04-23
Too funny- I actually am using that shark picture in one of my presentations on the results of a model build using AD Model Builder!! :)

AD Model Builder is a statistical modeling package using a C++ general architecture with a number of pre-built libraries for establishing MLEs and a number of other statistical analyses, including a Bayesian approach. The "AD" stands for "auto-differential". 

[http://otter-rsch.com/admodel.htm](http://otter-rsch.com/admodel.htm)

It's been a long day- I tried to come up with some really good witticisms, but I'm empty. My bad! :)

---

### Post by bite on 2008-04-24
So eventually I can confirm you that I am *not* running an AD model builder, in spite of the shark :) but if I understand I am doing something similar, with a self-made c++ program, and maybe I can give you a suggestion.

I have a large image containing tens to hundred of thousands of points (edgels) lying on the edges of objects in the image.

The first stage of the processing consists of fitting to these points a large number (thousands to tens of thousands) of small segments of straight lines. The segments must be small because they must adapt to curved edges.

Then I must gather neighboring segments in chains representing the edges; I do this with Adaptive Hierarchical Clustering.

I can parallelize the clustering process by noting that only entities that are geometrically close together are candidates to clustering. So I divide the image in squares and I run a separate clustering thread in every square. Of course, the edgels must be assigned to squares, too, and this is done when extracting them.

The process may then be repeated with larger squares if a higher level clustering is needed.

(Remember that stl containers (I am using std::map) are reentrant for reading but not for writing).

---

### Post by otterrsch on 2008-05-07
> **kvk said:**
> Is anyone running AD Model Builder on Ubuntu (or any other distro, for that matter) and more importantly- has anyone ever written the code in parallel form to allow synchronous processing on a cluster?

I have run AD Model builder on various Redhat versions as well as on Ubuntu, both 32 and 64 bit.

BTW AD stands for Autodif or automatic differentiation and this is a package for doing 
large scale nonlinear statistical modeling.

It has some built in support for parallelization
using PVM, but this is rather poorly documented.

It also has support for doing nonlinear mixed models.  (That is a statistical concept).

---

### Post by kvk on 2008-05-08
Excellent. I'll check out PVM, and let you know the results of my project if it ever comes to fruition. Thanks!

---

