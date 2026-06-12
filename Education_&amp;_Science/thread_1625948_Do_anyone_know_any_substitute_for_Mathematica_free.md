---
title: "Do anyone know any substitute for Mathematica free of charge?"
date: 2010-11-19
forum: Education &amp; Science
---

### Post by subjugater on 2010-11-19
Does anyone know any substitute for Mathematica free of charge?

Just like Scilab or Octave for Matlab. Thanks.

---

### Post by Blutkoete on 2010-11-20
I never tried it myself, but I found this while searching the internet:
[URL="http://www.sagemath.org/"]
http://www.sagemath.org/[/URL]

It's GPL open-source and claims to be an alternative to Magma, Maple, Mathematica and MATLAB. If you use it, I'd be glad to hear whether it's worth a look or not.

---

### Post by subjugater on 2010-11-20
> **Blutkoete said:**
> I never tried it myself, but I found this while searching the internet:
[URL="http://www.sagemath.org/"]
http://www.sagemath.org/[/URL]

It's GPL open-source and claims to be an alternative to Magma, Maple, Mathematica and MATLAB. If you use it, I'd be glad to hear whether it's worth a look or not.

Buddy, thanks for your suggestion. Though this software seems rather immature for many aspects at a first glance, I'll try and let you know how I feel.

Again, thanks.

---

### Post by Blutkoete on 2010-11-20
What exactly do you want to do with the program?

You might find single programs for each of the tasks (like [XPPAUT]("http://www.math.pitt.edu/%7Ebard/xpp/whatis.html")), but I don't know whether there is a mature open source one-fits-all mathematics program.

Good luck!

---

### Post by stefangr1 on 2010-11-20
> **subjugater said:**
> Does anyone know any substitute for Mathematica free of charge?

Just like Scilab or Octave for Matlab. Thanks.

What about R? It's cross platform, and at least in my field knowing R would be a real asset on your CV.

---

### Post by rhoparkour on 2010-11-22
Hey,

I don't know exactly what you're looking for, but maxima is a great symbolic calculation package.

[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)

BTW I know sage uses it to do symbolic calculations, but sage doesn't use maxima's full features.

---

### Post by agm. on 2010-11-23
Like the others, I am not sure exactly what you are trying to do through Mathematica, but if it is fairly simple stuff, I really like [ Wolfram Alpha ](http://www.wolframalpha.com) as it uses all the same syntax as Mathematica and can do some of the plotting and easy graphing and evaluation of derivatives and such.

Otherwise, I'd second using R.  It's a very powerful program.

---

### Post by nicolastraffic2 on 2010-12-08
I never got this myself . but with the help of internet  i got.

---

### Post by Silentvoice on 2010-12-08
> **rhoparkour said:**
> Hey,

I don't know exactly what you're looking for, but maxima is a great symbolic calculation package.

[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)

BTW I know sage uses it to do symbolic calculations, but sage doesn't use maxima's full features.


I think maxima is the best bet here, everything I've tried to do on it that I know I could have done on mathematica (but didn't have mathematica vailable) it was able to do, and pretty much as good.

I usually only need to perform very length symbolic integrations to construct quadrature rules, Gram matrices, or vandermonde matrices in arbitrary precision.. It depends on the nature of your problem whether or not maxima will be sufficient.

---

### Post by gjbalzano on 2010-12-21
Hi - People telling you to choose Maxima over Sage obviously haven't been reading the docs carefully. Because, quite clearly, in the Sage Tutorial, on the _["Interfaces" page]("http://www.sagemath.org/doc/tutorial/interfaces.html")_, it says "Maxima is *included with* Sage, as well as a Lisp implementation. (italics mine)" In fact, one of the main points of Sage is to make it "possible for you to use most mathematics software together. SAGE includes interfaces to Magma, Maple, Mathematica, MATLAB, and MuPAD … and also the free programs Axiom, GAP, GP/PARI, Macaulay2, Maxima, Octave, and Singular." (This last quote from a talk given by Sage's creator, William Stein.) So I'd give Sage a serious look if I were you.

---

### Post by rhoparkour on 2010-12-21
> **gjbalzano said:**
> Hi - People telling you to choose Maxima over Sage obviously haven't been reading the docs carefully. Because, quite clearly, in the Sage Tutorial, on the _["Interfaces" page]("http://www.sagemath.org/doc/tutorial/interfaces.html")_, it says "Maxima is *included with* Sage, as well as a Lisp implementation. (italics mine)" In fact, one of the main points of Sage is to make it "possible for you to use most mathematics software together. SAGE includes interfaces to Magma, Maple, Mathematica, MATLAB, and MuPAD … and also the free programs Axiom, GAP, GP/PARI, Macaulay2, Maxima, Octave, and Singular." (This last quote from a talk given by Sage's creator, William Stein.) So I'd give Sage a serious look if I were you.

Even though Sage includes Maxima, Sage cannot take advantage of every Maxima package. For example, I use Maxima's tensor packages, which Sage cannot use directly, you must always do something like 

```

maxima('include maxima commando here')

```

As you can see, very annoying.

---

