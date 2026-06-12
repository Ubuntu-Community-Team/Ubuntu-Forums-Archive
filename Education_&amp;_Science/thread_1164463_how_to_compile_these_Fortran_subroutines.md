---
title: "how to compile these Fortran subroutines???"
date: 2009-05-19
forum: Education &amp; Science
---

### Post by subjugater on 2009-05-19
I have uploaded all the programs and subroutines via a tar file (see attachment). I have problem with compiling two of them which are named chebexc.f and durdec.f respectively.

These two subroutines were given by one of my research collaborators, which are in a very old fashion. I tried to compile them by G95 and Gfortran, but failed. I even tried G77, ending with the same results.

I am 100% sure that they are correct. Could anybody try these two subroutines and suggest something? Perhaps you could suggest me some compiler options, such as -fugly or -std=g77 (I tried these two options, but they don't work).

---

### Post by ad_267 on 2009-05-19
Could you post the errors you receive when trying to compile them?

---

### Post by subjugater on 2009-05-19
> **ad_267 said:**
> Could you post the errors you receive when trying to compile them?

When I was compiling the subroutine chebexc.f, I got
> kent@kent-desktop:~/study/codes/mextest/ver3$ g95 -c chebexc.f
In file chebexc.f:452

       TDIFF(2) = 0
             1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:453

       TDIFF(1) = TEXP(2)*SC/2
                       1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:498

       TINT(2) = TEXP(1)*SC
            1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:500

       TINT(2) = TEXP(1)*SC
            1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:501

       TINT(3) = TEXP(2)*SC/4
            1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:501

       TINT(3) = TEXP(2)*SC/4
                      1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:503

       TINT(2) = TEXP(1)*SC
            1
Warning (108 ): Array reference at (1) is out of bounds
In file chebexc.f:504

       TINT(3) = TEXP(2)*SC/4
            1
Warning (108 ): Array reference at (1) is out of bounds
kent@kent-desktop:~/study/codes/mextest/ver3$ 

When I was compiling the subroutine durdec.f, I got
> kent@kent-desktop:~/study/codes/mextest/ver3$ g95 -c durdec.f
In file durdec.f:59

      IFAC(3) = 2
           1
Warning (108 ): Array reference at (1) is out of bounds
In file durdec.f:62

      IFAC(2) = NF
           1
Warning (108 ): Array reference at (1) is out of bounds
In file durdec.f:156

      NF = IFAC(2)
                1
Warning (108 ): Array reference at (1) is out of bounds
In file durdec.f:715

      NF = IFAC(2)
                1
Warning (108 ): Array reference at (1) is out of bounds
In file durdec.f:149

      CALL DURAB1 (N,C,WSAVE,WSAVE(IW1),WSAVE(IW2))
                                        1
In file durdec.f:153

      SUBROUTINE DURAB1 (N,C,CH,WA,IFAC)
                                   2
Warning (155): Inconsistent types (REAL(8 )/INTEGER(4)) in actual argument lists at (1) and (2)
In file durdec.f:31

      CALL DURA1 (N,WSAVE(IW1),WSAVE(IW2))
                               1
In file durdec.f:35

      SUBROUTINE DURA1 (N,WA,IFAC)
                             2
Warning (155): Inconsistent types (REAL(8 )/INTEGER(4)) in actual argument lists at (1) and (2)
In file durdec.f:708

      CALL DURAF1 (N,C,WSAVE,WSAVE(IW1),WSAVE(IW2))
                                        1
In file durdec.f:712

      SUBROUTINE DURAF1 (N,C,CH,WA,IFAC)
                                   2
Warning (155): Inconsistent types (REAL(8 )/INTEGER(4)) in actual argument lists at (1) and (2)


---

### Post by kleeman on 2009-05-20
You are only getting warnings from the compiler which should not prevent an object file being created. The type of warning errors you are getting appear due to non-standard fortran such as using pointers for arrays instead of fully declaring them. They should not be serious errors.

do you actually get an object file after compiling? You should....

---

### Post by subjugater on 2009-05-21
> **kleeman said:**
> You are only getting warnings from the compiler which should not prevent an object file being created. The type of warning errors you are getting appear due to non-standard fortran such as using pointers for arrays instead of fully declaring them. They should not be serious errors.

do you actually get an object file after compiling? You should....

Thanks for your reply, buddy. I actually got the executable output. But I got some results which does not make sense when running this output.

Do you know by using any option of G95 compiler I can overcome this difficulty? 

Again, I appreciate.

---

