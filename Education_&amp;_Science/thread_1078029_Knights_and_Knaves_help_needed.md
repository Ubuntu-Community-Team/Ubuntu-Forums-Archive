---
title: "Knights and Knaves help needed"
date: 2009-02-22
forum: Education &amp; Science
---

### Post by Kralizec on 2009-02-22
I hope people who have taken logic and/or a discrete math course know of the type of problem I mean, but here's what you need to know: Knights always speak the truth, and knaves always lie.

> We are on a knight-knave island. Our troubles aren't over. In order to save our lives we must determine which of three men are king. Their names are Jal, Tak, and Zeb, and they made the following statements.
               Jal:  "I am not the king."
               Tak:  "I am the king."
               Zeb:  "I am the king." 
From this, of course, nothing can be determined, but then two witch doctors Weg and Woo speak up and say the following.
            Weg:  "Either Tak is a knave or Zeb is a knight."
            Woo:  "Either I am a knave or Weg and Jal are the same type
             (meaning both knights or both knaves)."

From this the identity of the king can be determined. Which one is he: Jal, Tak or Zeb? Also, what type is each of the five?

Can anyone help solve this problem?

---

### Post by Kralizec on 2009-02-22
Also, it only helps me if you explain your reasoning. Thanks!

---

### Post by PandaGoat on 2009-02-23
Is it possible for two to be king?  And are you sure you wrote the problem correctly?  I keep arriving at either there are no kings (which I'm assuming to be a contradiction) or there are two kings.  Note that the question implied plurality: "which of three men are king."

I googled the problem and got [http://www.csee.umbc.edu/~stephens/203/EXAM/exam1prep07.html](http://www.csee.umbc.edu/~stephens/203/EXAM/exam1prep07.html).  Since this is the University of Maryland, UF says you're from Maryland, and it's the same problem, I'm going to say you have an exam soon :P.

---

### Post by Kralizec on 2009-02-23
You are correct about the exam, unfortunately. That's actually my teacher's website. So you can see from the webpage that I wrote the problem down correctly.

---

### Post by Kralizec on 2009-02-23
Whew, just finished my exam. Thankfully there weren't even any knights and knaves problems on it. But I'd still be interested in knowing the answer to this problem if anyone can do it.

---

### Post by PandaGoat on 2009-02-24
I've thought about it some more.  My initial mistake was not knowing what to do not knowing if the dichotomy of some statements is inclusive or exclusive.  Anyway, I know now to assume they are inclusive, so here it goes:

First look at this statement: "Woo: 'Either I am a knave or Weg and Jal are the same type.'"  Let's convert this into (A v B).  A implies ~(A v B) which is a contradiction, so we have that Woo must be a knight, and since this statement must be true, B must be true.


Next, let's look at "Weg: 'Either Tak is a knave or Zeb is a knight'".  We have, (A v B) if Weg is a knight or ~(A v B) if he is a knave, right?  

Well, let's start with the latter, ~(A v B).  From De Morgan's law, we have (~A and ~B), but then we would have two kings, which is a contradiction.  So Weg is a knight.

So, now we have (A v B):  Let's assume A and ~B; then we have two kings, which is a contradiction.  Now, let's assume ~A and B; again, we have two kings.  Let's now do A and B; we have one king; thus, this must be the truth since we've depleted our choices and there is no contradiction.

In conclusion, Woo must be a knight; Weg and Jal are the same type; Weg and Jal are knights; Tak is a knave; and Zeb is a knight and the king.



This probably isn't the best explanation, but heh.

---

### Post by Kralizec on 2009-02-24
This, my friend, is the only decent explanation for this particular problem, and by far the clearest explanation of a knights and knaves problem I've ever heard. Thank you very much.

On a side note, you're the only person who's answered this who hasn't come to the conclusion that Jal is the king. However, you are the only one who could successfully defend their conclusion.

---

