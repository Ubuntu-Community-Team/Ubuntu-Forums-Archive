---
title: "problem with GSL ODE numerical solver"
date: 2009-02-17
forum: Education &amp; Science
---

### Post by bebops_lost on 2009-02-17
Hi everyone:
I'm having a problem with the ODE (ordinary differential equation) numerical solver from the GSL library. I have a system with, say, y elements, each of which evolve in time according to a differential equations that are coupled with each other.

so I allocate my array 
```
 double t = 0.0, t1 = 100, h = 1e-6; 
double *c = new double[y];
```

as well as the gsl parameters for the adaptive step-sizer as follows.

```

const gsl_odeiv_step_type * T = gsl_odeiv_step_rkf45;

gsl_odeiv_step    * s      =  gsl_odeiv_step_alloc (T, y );
gsl_odeiv_control * con    =  gsl_odeiv_control_y_new (1e-6, 1e-6);
gsl_odeiv_evolve  * e      =  gsl_odeiv_evolve_alloc (y);
gsl_odeiv_system sys = {func, jac, y, P};

```

and then proceed through time-evolution:
```

while( t < t1)
{ ...
status = gsl_odeiv_evolve_apply (e, con, s, &sys, &t, P->t1, &h, c);
...
}
```

and everything works fine as long as y doesn't change. ***BUT*** for my problem, if the last element c[y-1] starts to get reasonably big then I need to add on extra elements to the end of the array to make the numerical solver operate on a larger number of elements (i.e. I need to grow my hilbert space if that means anything useful.)

so to do that, I de-allocate all the previous ODE parameter data, and allocate new ones, as well as a new (larger) array c[y+10] and then switch over the pointers and clear the memory. like this:

```

if(need to grow)
{
gsl_odeiv_evolve_free (e); gsl_odeiv_control_free (con); gsl_odeiv_step_free (s);

c_new = new double[y +10]; ... /* then copy over the elements*/ 

s= gsl_odeiv_step_alloc (T, y+10);
con= gsl_odeiv_control_y_new (1e-6, 1e-6);
e =  gsl_odeiv_evolve_alloc ( y+10);
gsl_odeiv_system sys = {func, jac, y+10, P};
h = 1e-6;
}

```

and then time-evolve by proceeding back into the same while loop with the same gsl_odeiv_evolve_apply function used above (with the new parameters). However, this has resulted in some serious numerical problems. all the quantities in the system evolve smoothly with time immediately after this growth, but I notice discontinuous "jumps" in the variables at times long after the "growth."

I've used a number of different processors to do this, so I don't think the problems is specific to any particular machine.
Am I just going about this all wrong? any ideas would be much appreciated.
-B

---

