---
title: "Braid install issue: NVidea CG Toolset required on ATI Raedon laptop"
date: 2012-06-08
forum: Gaming &amp; Leisure
---

### Post by bartonski on 2012-06-08
I'm running 10.04 on a laptop with the following in lspci:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
```

I tried installing Braid from Humble Indie Bundle 5, via the 32 bit deb package. The dialog box from the installer says

> Requires the installation of 1 packages

When I click on the 'Details' button, I get a pop-up saying

> To install the following changes are required:
To be installed: nvidia-cg-toolkit

Does Braid require an nvidia chipset? 

I only see cg-shaders in the intall files. AFAIK, ATI doesn't support CG. Am I scrood?

---

### Post by thatguruguy on 2012-06-08
> **bartonski said:**
> I'm running 10.04 on a laptop with the following in lspci:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
```I tried installing Braid from Humble Indie Bundle 5, via the 32 bit deb package. The dialog box from the installer says


When I click on the 'Details' button, I get a pop-up saying



Does Braid require an nvidia chipset? 

I only see cg-shaders in the intall files. AFAIK, ATI doesn't support CG. Am I scrood?

Have you considered installing it and finding out if it works?

---

### Post by bartonski on 2012-06-08
I didn't know if it would conflict with someone else...

---

### Post by papibe on 2012-06-08
Hi bartonski.

If it does, the conflict will be resolve uninstalling the package.

It looks like the library is an abstract level to access GPU's shaders.

From this article: [CSC 471 Final Project - Vertex and Pixel Shaders]("http://users.csc.calpoly.edu/~zwood/teaching/csc471/finalproj24/jsoldo/index.html").
> Nvidia has recently developed a toolkit for writing shaders called CG. It uses extensions which seem to be fairly portable (they work on my ATI Radeon 9800 Pro)....

If I were you I'd install it to see if it solves the problem.

Just a thought.
Regards.

---

