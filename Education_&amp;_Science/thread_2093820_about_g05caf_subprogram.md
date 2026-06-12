---
title: "about g05caf subprogram"
date: 2012-12-11
forum: Education &amp; Science
---

### Post by mgallom on 2012-12-11
Hello every one! I'm a new FORTRAN programmer and I 've gotten a confusion about some NAG library subprogram,the subprogram g05caf. I know that it is used to generate random numbers uniformly distributed in the range [0.0,1.0] and can be initialized by one of these two subroutines g05cbf or g05ccf.
Now what I'm confused about is that is this subprogram (g05caf) a function or subroutine because the text book that I'm reading name it a routine but deal with it as a function not subroutine (declared as a function). So if some one can explain this matter?
Note: you may like to have a look for my program, please open this link and refer to page number 48:
[http://mgg.coas.oregonstate.edu/~andreas/OC599/climate_modeling_11/138fortran90.pdf](http://mgg.coas.oregonstate.edu/~andreas/OC599/climate_modeling_11/138fortran90.pdf)
Best regards
gallo

---

### Post by mgallom on 2013-01-03
Are there any one can help this, please?

---

### Post by rewyllys on 2013-01-04
> **mgallom said:**
>  . . . . Now what I'm confused about is that is this subprogram (g05caf) a function or subroutine because the text book that I'm reading name it a routine but deal with it as a function not subroutine (declared as a function). So if some one can explain this matter? . . . . 
Whether a particular group of lines of code should be considered a function or a subroutine is actually rather arbitrary.  

What makes the distinction is how you use that group of lines of code in your overall program: e.g., whether you declare it as a function or call it as a routine.

---

