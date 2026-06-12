---
title: "The worst language to learn programming from:"
date: 2008-02-22
forum: Education &amp; Science
---

### Post by 1337455 10534 on 2008-02-22
I have seen this thread: [http://ubuntuforums.org/showthread.php?t=641120](http://ubuntuforums.org/showthread.php?t=641120). But my question may be one of a more serious nature.

My high school is teaching kids Scheme as their first language. Any thoughts?

To demonstrate;
```

;; This must be done in the IDE
;; (2r^2 * .5h^3)/(3r8h^1/2)
(define (thing r h) ((/ (* (* 2 (expt r 2)) (* .5 (expt h 3))) (* (* 3 r) (* 8 (sqrt h))))
(thing 1 2)
;; In Python for eg:
; thing = lambda r,h: (2(r**2) * .5(h**3))/(3r * 8(h**.5))
; thing(1,2)

```

Scheme may teach you things about structure, but it has 0 real life use... Any defense for Scheme?

---

### Post by sryth on 2008-02-22
My opinion is simply going to be that, my opinion.  But I think it is an excellent choice.  

Learning Scheme teaches students to think in a mindset conducive to programming.  Everything is data, everything is a list, from primitive to procedure definition, everything else is mere abstraction.  This is true in every language, but it is most accessible in that format in scheme/lisp.  Learning scheme will make anyone a better programmer, and make learning any other language much easier, no matter where you are in programming knowledge.  

As far as real world use, yes, I prototype in scheme at times, it can be the easiest way to knock something out quickly.  Scheme is a very active language and has a good community behind it.  [http://www.plt-scheme.org](http://www.plt-scheme.org)     for more info and check out the DrScheme IDE.  Nice stuff.  

Scheme is also experiencing an upsurge due to the new r6rs standards being discussed/formalized.  These will standardize the various dialects a good bit and make commercial applications a lot less leery of using it.

You may feel that it is a bad language to start out with, but personally I think that is probably because you have learned other languages first and have habits and preconceptions based on those languages, as a first language I don't think it'll be a problem.

---

### Post by InfinityCircuit on 2008-02-22
C++ 

[http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

---

### Post by euler_fan on 2008-02-23
I have a professor who is a major Fortan user who is teaching an applied math course using Mathematica of all things. His defense of Mathematica (despite almost none of us using it after his course) is--paraphrasing of course--this:

> It's just as important you learn how to learn a language as to learn a language you will use. In the real world, you won't always be given a choice about what language or software to use, so having experience learning a new language from scratch is a very useful skill.


I tend to agree. When learning to program the choice of language should ultimately support teaching not only the right mindsets and skill sets but also how to learn a language. If [brainfuck]("http://en.wikipedia.org/wiki/Brainfuck") serves the point of the class, I would expect to see it used (in the absence of at least better named languages) even though it serves almost no practical value.

---

