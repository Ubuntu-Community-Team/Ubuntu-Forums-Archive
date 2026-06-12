---
title: "Guidance on programming assignment"
date: 2010-08-31
forum: Education &amp; Science
---

### Post by omi291 on 2010-08-31
Hello everybody,

I'm a first year college student (CS major :D), and I've received a small project that I need to complete by Friday. It revolves around manipulating photos. Information about the project can be found at the pdf file below:

[http://userweb.cs.utexas.edu/users/lin/cs315h/prog1.pdf](http://userweb.cs.utexas.edu/users/lin/cs315h/prog1.pdf)

I was kind of stumped on the "black and white" effect. At first, I thought I'd just take the average of the RGB values for each pixel, then, depending on whether or not it's greater than some threshold (I decided on 127, the halfway point between 0 and 255), setting each pixel's RGB values to 0 or 255. 

I started thinking more about it, and I was wondering...black and white photos are usually more of a gray shade - instead of making each pixel purely black or white, am I supposed to merely lighten or darken the shade of each pixel?

I'm not searching for anyone to write the code for me - I just want to get some feedback/constructive criticism on my current method.

Many thanks in advance!

---

### Post by dv3500ea on 2010-08-31
You probably want a 'greyscale' effect.

For each pixel you could do something like:
```

red = green = blue = integer(average(red, green, blue))

```

---

### Post by PandaGoat on 2010-09-02
A more interesting method is to do a one-bit quantization of the pixels to either black or white and dither it.

Note: there are various measures of how a color's lightness. You'll have to pick one. The previous poster gives a simple measure. See [http://en.wikipedia.org/wiki/HSL_and_HSV#Lightness](http://en.wikipedia.org/wiki/HSL_and_HSV#Lightness).

---

