---
title: "wxMaxima doesn't pause to read in batch(&quot;*.max&quot;)"
date: 2008-06-15
forum: Education &amp; Science
---

### Post by silbar on 2008-06-15
Greetings,

Now using wxMaxima 0.7.1 (based on maxima 5.13.0) in Hardy.  In going through Richard Rand's "Introduction to Maxima", which can be found at

[INDENT]maxima.sourceforge.net/docs/intromax/intromax.pdf ,[/INDENT]

I ran into some problems in his Sec. 7, "Programming in Maxima".  For the program script which he gives,

       [INDENT]/* maxima program critpts.max */
	critpts():=(
	print("program to find critical points"),
	f: read("enter f(x,y)"),
	print("f = ",f),
	eqs: [diff(f,x), diff(f,y)],
	unk: [x,y],
	solve(eqs,unk)
	)$[/INDENT]

then the command 'batch("critpts.max")' in wxMaxima doesn't do what he claims it does (in Maxima -- he's not talking about wxMaxima).  It doesn't pause for the reads and just prints out each (unevaluated) command:

[INDENT](%i6) batch("critpts.max");
batching #p/home/silbar/critpts.max
(%i7) critpts():=(print(program to find critical points),f:read(enter f(x,y)),
print(f = ,f),eqs:[diff(f,x),diff(f,y)],unk:[x,y],solve(eqs,unk))[/INDENT]

I haven't tried this yet in the command-line maxima, but I assume that Rand's claim it works there is correct.

Any thoughts, anyone?

   Dick Silbar

---

### Post by silbar on 2008-06-23
Hmmm, no responses.

An additional quirk in wxMaxima.  This time in going through Robert Dodier's "Minimal Maxima" tutorial, in the section (7.4) on plotting:
```
(%i2) xx: makelist(i/2.5,i,1,10);
(%o2) [0.4,0.8,1.2,1.6,2.0,2.4,2.8,3.2,3.6,4.0]

(%i6) yy: map(lambda([x], exp(-x)*sin(x)), xx);
(%o6) [0.26103492114346,0.32232886922706,0.28072477796927,0.20181042993345,
0.12306002480578,0.061276637261957,0.020370650389687,-0.0023794587414574,-
0.012091305769841,-0.013861321214153]

(%i7) wxplot2d([['discrete, [xx], [yy]]], [x,-5,5]);
Maxima encountered a Lisp error:
 Error in MEVAL [or a callee]: ((MLIST SIMP) 0.40000000000000002
                                0.80000000000000004 1.2
                                1.6000000000000001 2.0
                                2.3999999999999999 2.7999999999999998
                                3.2000000000000002 3.6000000000000001
                                4.0) is not of type (OR RATIONAL
                                                     LISP:FLOAT).
Automatically continuing.
To reenable the Lisp debugger set *debugger-hook* to nil.
(%i8) 
```
The wxplot2d function is obtained from the pull-down menu on plotting and after selecting discrete from the Special button.  

On the other hand, the usual maxima command
```

plot2d([discrete,xx,yy]);
```
does work in wxMaxima (but only if you have already installed the gnuplot-x11 package).

   Dick Silbar

---

