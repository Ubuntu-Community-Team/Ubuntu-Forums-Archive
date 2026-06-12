---
title: "Centre of Mass analysis"
date: 2008-02-14
forum: Education &amp; Science
---

### Post by in_flu_ence on 2008-02-14
Is there any software which I can estimate the centre of mass from a grayscale image of a particle? I want to calculate that centre point to derive some correlation.

Any help?

Thanks a million.

---

### Post by euler_fan on 2008-02-14
> **in_flu_ence said:**
> Is there any software which I can estimate the centre of mass from a grayscale image of a particle? I want to calculate that centre point to derive some correlation.

Any help?

Thanks a million.

Unfortunately, your problem as stated is non-trivial. For instance, does the software need to do edge detection? That's a very hard problem to solve well.

Without more information we're not really going to be able to give you a good answer.

If the shade of the pixel is related to the amount of mass at that point, I would say import it into python using the Python Image Library and write a module to do the [standard center of mass computation]("http://en.wikipedia.org/wiki/Center_of_mass") for discrete masses assuming each pixel's mass is located somewhere convenient (say centers or a given corner). Not elegant, but it would work.

This method would also work if you could convert your image into one containing the same information (each pixel's shade corresponds to the mass at that location under some invertible transformation).

Good luck!

EF

---

### Post by NeiNastran on 2008-02-15
Did you ever find software to fit your needs?

---

### Post by in_flu_ence on 2008-02-15
NOt at the moment. I do have particle with a distinctive edge. So i m more looking into the edge detection option. Something like softwares which normally come with a pendant drop contact angle meter.

I do have the option to write a code to find the mass but I try not to do the more challenging way if there is a proven software that works:P

---

### Post by [woodstock] on 2008-02-16
If I understand you correctly, you are examing images of kind of spherical particles. If your images are saved in a standard graphics format, you might be able to solve your problem using [ImageJ]("http://rsb.info.nih.gov/ij/"). There are several plugins for it available and some might actually do the job.
Another approach would be to ask an operator of an EM-microscope. They have usually commercial software to do similar things you described. If it it just one measurement he/she might be helpful and calculate the center of mass.
However, if you are writing some python scripts, it would be kind of you to publish it here(or somewhere else).

---

