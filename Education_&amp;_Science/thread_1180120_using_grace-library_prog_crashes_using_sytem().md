---
title: "using grace-library prog crashes using sytem()"
date: 2009-06-06
forum: Education &amp; Science
---

### Post by hanseldansel on 2009-06-06
Dear ubuntu-users,

I use the grace-library grace_np.h for displaying and printing data from a running c-program;
my problem is:
As soon as I use a system command in this c-program, the grace-window closes and the running program outputs: "No grace subprocess4" for every xmgrace command.
OK so the grace-process stops due to a command sent to the shell. Is there a way to prevent the grace process being killed?

the function for displaying with grace:


  ```
 1 #include <stdio.h>
  2 #include <stdlib.h>
  3 #include <math.h>
  4 #include <unistd.h>
  5 #include <grace_np.h> // including xmgrace library
  6 void displaygrace( int Nel, int emr, double** fast, double** slow,
  7                    double** strain, double** Ta )
  8 {
  9 static int firsttimegrace = 1;
 10 static int gracecount = 0;
 11 int i, j;
 12 if ( firsttimegrace == 1 )
 13         {
 14         firsttimegrace = 0;
 15         if ( GraceOpen( 2048 ) == -1 )
 16                 {
 17                 fprintf( stderr, "Can't run Grace. \n" );
 18                 exit( 1 );
 19                 }
 20         /*
 21         .
 22         .
 23         */
 24
 25         }// if ( firsttimegrace == 1 )
 26         /*
 27         .
 28         .
 29         */
 30 GracePrintf ("redraw");
 31 if ( GraceIsOpen() ) // grace alive? then save and print otherwise crash!
 32         {
 33         GracePrintf("DEVICE \"PostScript\" OP \"color\" \n");
 34         GracePrintf("HARDCOPY DEVICE \"PNG\"  \n");
 35         GracePrintf("print to \"output/PNGs/sample%.4d.png\" \n", gracecount );
 36         GracePrintf("print \n");
 37         GracePrintf("saveall \"output/grace/sample%.4d.agr\"", gracecount );
 38         }
 39 else
 40         {
 41         exit(EXIT_FAILURE);
 42         }
 43 gracecount++;
 44 }// void displaygrace
```Thank you very much in advance for suggestions!

Cheers!
Daniel

---

