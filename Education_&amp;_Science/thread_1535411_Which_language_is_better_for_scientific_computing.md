---
title: "Which language is better for scientific computing?"
date: 2010-07-20
forum: Education &amp; Science
---

### Post by perroazul on 2010-07-20
I ran a simultaneous benchmark test in a computer cluster with a code for doing a simple computation (computing a square root) in a loop with 10^12 iterations. here are the results:
```

>time ./bench_fO 
15485.034u 0.699s 4:18:08.29 99.9%	0+0k 0+0io 0pf+0w
>time ./bench_f
17205.607u 0.001s 4:46:48.45 99.9%	0+0k 0+0io 0pf+0w
>time ./bench_c
34843.920u 0.054s 9:40:49.82 99.9%      0+0k 0+0io 0pf+0w

```
the first result corresponds to a fortran 90 code compiled with the -O4 flag (maximum optimization of the code). the second one is the result for the same code without optimization and the third one is for a line-by-line equivalent C++ code. the fortran executable completes the task in less than half of the time for the C++ code!!
so, the programming language choice for running large simulations is still fortran.

---

### Post by ahmatti on 2010-07-21
Your benchmark only shows that Fortran computes the square root faster...  I'd be  happy to see a more complete benchmark though. Also could you post the code for this one?

---

### Post by perroazul on 2010-07-21
> **ahmatti said:**
> Your benchmark only shows that Fortran computes the square root faster...  I'd be  happy to see a more complete benchmark though. Also could you post the code for this one?

I don't think so. it could be any floating point operation. also the difference in times is because of the number of iterations. if you decrease this number, both codes execute in the same time. the codes are below:
```

program test
integer :: i,j,k,n
real :: x

n=10000

do i=1,n
   do j =1,n
      do k=1,n
         x=sqrt(real(i)*real(j)*real(k))
      enddo
   enddo
enddo

end program test

```
and C++
```

#include <stdio.h>
#include <math.h>

int main(){
    int n = 10000;
    int i, j, k;

    for (i = 0; i < n; i++){
        for (j = 0; j < n; j++){
            for (k = 0; k < n; k++){
                sqrt(((double)i)*((double)j)*((double)k));
            }
        }
/*        printf("i = %d\n", i);*/
    }

    return 0;
}

```
also, the problem with using more complex code, is that it will be harder to get line-by-line equivalents.

---

### Post by perroazul on 2010-07-21
> **numinous said:**
> 
There isn't a perfect language for everything and Fortran for numerical Scientific programming is a good choice, but I'm not sure about Fortran libraries to code a GUI or database program.  Also I've yet to find a good book for learning any modern Fortran.

How about comparing C also?

I completely agree with you. I would only recommend fortran to anybody interested in scientific computing, who wants to do some heavy computations. In my case, I use matlab for manipulating and visualizing the data that my fortran simulations generate. I would never ever try to use fortran or C or C++ for doing that. 
I would gladly run a C simulation if you or anybody else translates the code. Unfortunately I don't know C or C++ for that matter. the C++ translation of the code above was done by a friend of mine :)

---

### Post by KIAaze on 2010-07-23
> **perroazul said:**
> I would gladly run a C simulation if you or anybody else translates the code.

It's actually exactly the same code in this case since no C++ specific features are being used. :)

If you want to compile it as C code:
```
gcc -lm -o bench_c bench_c.c
```
If you want to compile it as C++ code:
```
g++ -lm -o bench_cpp bench_c.cpp
```
(usually, the files are named ".cpp" for C++ code)

Very interesting comparison.
But did you use any optimization flags for the C++ code?
Here's a list of them:
[http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html)

It looks like using "-Ofast" would be the best for this test.

On a sidenote: There are pretty cool tricks for improving the speed of square root calculations. :)
Example: : [http://www.codemaestro.com/reviews/9](http://www.codemaestro.com/reviews/9)
C and C++ also allow working directly on bits which can make multiplying and dividing integers by 2 much faster.
I don't really know fortran, so I don't know if it has the same capabilities.

---

### Post by Azrael3000 on 2010-07-24
I'm a fortran programmer myself working in academia. I wouldn't take your simple test as a valid benchmark. It just looks at one specific aspect of the progam. Furthermore if you haven't used any optimizations on the c++ code, the results are not comparable. Also you'll get different results depending on the specific compiler you are using.

From my experience there is one thing which can really make a program fast. And that's proper coding. This for example is especially true with higher level languages like Python. If you use the correct tools for your task you can end up being a hundred times faster than before.

Unfortunately that's something very difficult to learn and I have yet to find any guides on how to do efficient programing. If anybody has some references I'd be very thankful.

Cheers,
Arno

---

### Post by perroazul on 2010-07-31
> **KIAaze said:**
> It's actually exactly the same code in this case since no C++ specific features are being used. :)

If you want to compile it as C code:
```
gcc -lm -o bench_c bench_c.c
```
If you want to compile it as C++ code:
```
g++ -lm -o bench_cpp bench_c.cpp
```
(usually, the files are named ".cpp" for C++ code)

Very interesting comparison.
But did you use any optimization flags for the C++ code?

my apologies for my C-C++ ignorance, and thanks for the info. If you read the original post carefully, you will notice that times for 2 fortran executables were reported, one compiled with full optimization and one compiled with **no optimization whatsoever**. in both cases the execution times where half the time for the C code program. 
However comparing the execution time for an optimized C program is interesting and so I compiled the C code above as follows
```
gcc bench_c.c -lm -O4 -o bench_c
```
right now I'm waiting for the results and I'll post them as soon as the program finishes. 
one thing I noticed re-reading the original post was that I didn't mentioned that *I used gfortran and gcc compilers for the cases reported*.

---

### Post by Silentvoice on 2010-08-01
Notice that you're calling printf in the C code, but are using no OS services in the FORTRAN code. Furthermore you are calling it within quite a large loop.
[EDIT]: Sorry, didn't see you commented that out.


Also this isn't really a valid benchmark, I would be more interested in seeing a benchmarks run with comparable parallel linear algebra done on both languages.

Also I don't know the difference between compilers of Fortran and C when it comes to using things like SSE2 instructions for vectorization. This can make a huge difference in a scientific application, and if I remember right you must explicitly declare you wish the compiler to do it for you for both GCC and intel's compiler. Otherwise you must use inline asm (or intrinsics for Intel), and I don't know how people like to see that in a benchmark for a particular language.

---

### Post by gunksta on 2010-08-01
Question - Which language is better for scientific computing

Answer - It depends.

Does this simulation really shed any light on the question? Probably not. I'm not trying to be rude, but it's a fact. Comparing a set of languages on a single test isn't a particularly valid speed comparison and the ONLY thing you learn from this test is a partial sense of speed.

In today's world, where you can rent a powerful computer from Amazon for a few bucks a month to run math on (this is a great cheat btw. I've done some cool stuff from my netbook) the raw speed of the language is not necessarily the most important factor when comparing languages.

I would tend to include several additional measures. First - what are you familiar with? If you already know a reasonably appropriate tool, your time as a developer/researcher may be more valuable than the additional 5-10 minutes the simulation might take using a slower tool that you already know. It depends on what you are doing. It may be that the simulation won't run on the tools you already know and if you have to learn a new tool anyways, then learning the fastest tool may be a good choice.

Like I said, it depends. I don't do the type of simulation that C & Fortran are good at. I tend to work with statistics so I tend to use either R or Python. Compared to C or Fortran, it's safe to say these won't win very many speed contests, but for what I do, their speed is adequate and the ease of programming what I need to do more than makes up for the small difference in run-time.

Lots of considerations that this test does not evaluate.

---

### Post by perroazul on 2010-08-02
> **Silentvoice said:**
> 
Also this isn't really a valid benchmark, I would be more interested in seeing a benchmarks run with comparable parallel linear algebra done on both languages.

yes! I agree. a comparison like that is what I would really like to see.  
> **Silentvoice said:**
> 
Also I don't know the difference between compilers of Fortran and C when it comes to using things like SSE2 instructions for vectorization. This can make a huge difference in a scientific application, and if I remember right you must explicitly declare you wish the compiler to do it for you for both GCC and intel's compiler. Otherwise you must use inline asm (or intrinsics for Intel), and I don't know how people like to see that in a benchmark for a particular language.
this is a very sophisticated question actually. I use vectorial operations in fortran all the time but as I stated before, I'm not familiar with C, and thus I can't answer that. 
My point with the tests shown above was the following: whether your code comes from the discretization of a PDE, or solving a linear algebra problem, doing some fixed point iteration, or applying some transform (fourier, etc) to some variable, at the very end, what your program does is millions of algebraic calculations (complex or real). And the fact remains that if you ask fortran to do a huge number of floating point operations, and you ask C to do the same, those test shown that the execution times are not even comparable. fortran does it in half  **h.a.l.f** of the time it takes C to do it. 
and that makes a good case for using fortran in scientific computation.

---

### Post by perroazul on 2010-08-02
below is a summary of the execution times for all the test I have run until now:
```

fortran (no optimization)
4:46:48.45   (4 hours, 46 min, 48 seconds)
fortran (full optimization)
4:18:08.29   (4 hours, 18 min, 8 seconds)
C       (no optimization)
9:40:49.82   (9 hours, 40 min, 49 seconds)
C       (full optimization)
6:55:52.98   (6 hours, 55 min, 52 seconds)
Matlab
8:20:33:25.64(8 days, 20 hours, 33 min, 25 seconds)

```
the matlab code I used is below:
```

format long
n=10000;
tic;
for i=1:n
  for j=1:n
    for k=1:n
      x=sqrt(i*j*k);
    end
  end
end
tElapsed=toc;
save('benchmark_m', 'tElapsed','-ASCII')
exit

```
this code will save the execution time, in secons, in the text file called benchmark_m.

---

### Post by Silentvoice on 2010-08-02
> **perroazul said:**
> 
this is a very sophisticated question actually. I use vectorial operations in fortran all the time but as I stated before, I'm not familiar with C, and thus I can't answer that. 
My point with the tests shown above was the following: whether your code comes from the discretization of a PDE, or solving a linear algebra problem, doing some fixed point iteration, or applying some transform (fourier, etc) to some variable, at the very end, what your program does is millions of algebraic calculations (complex or real). And the fact remains that if you ask fortran to do a huge number of floating point operations, and you ask C to do the same, those test shown that the execution times are not even comparable. fortran does it in half  **h.a.l.f** of the time it takes C to do it. 
and that makes a good case for using fortran in scientific computation.

Well the main reason I brought it up is because of the sqrtpd instruction, which computes square roots of two doubles in parallel. Last time I checked none of the -O options in GCC will do this automatically, GCC has the capability to try and use instructions like this, but you must enable it with -msse2. Worse the compiler might be defaulting to x87 instructions for the floating point, which you must also explicitly switch using 
-mfpmath=sse. Things like this might be enabled by default on a Fortran compiler since Fortran is much more domain specific than C. Care to post the assembler output of both those codes?

I'm not saying Fortran is a bad scientific computing language, it's obviously good because it has survived for so long. But when it comes to writing optimized code, there is no substitute for understanding what's going on. A compiler will only take you so far, but in the end it's up to the programmer. At that point, it doesn't matter what language you're using.

---

### Post by perroazul on 2010-08-03
> **Silentvoice said:**
> Well the main reason I brought it up is because of the sqrtpd instruction, which computes square roots of two doubles in parallel. Last time I checked none of the -O options in GCC will do this automatically, GCC has the capability to try and use instructions like this, but you must enable it with -msse2. Worse the compiler might be defaulting to x87 instructions for the floating point, which you must also explicitly switch using 
-mfpmath=sse. Things like this might be enabled by default on a Fortran compiler since Fortran is much more domain specific than C. Care to post the assembler output of both those codes?

great!! that's really good stuff. I'm running two executables compiled with those tags right now, and I'll post the results tomorrow. Also, given that computing the square root has been source of much controversy,  I changed the instruction 
```

x=sqrt(real(i)*real(j)*real(k))

```
to
```

x=sqrt(real(i))/real(j) +log(real(k))

```
and compiled the C code as follows
```

gcc bench_c.c -lm -O4 -ffast-math -msse2 -mfpmath=sse -o bench_c

```
I used the same options with gfortran.
> **Silentvoice said:**
> 
I'm not saying Fortran is a bad scientific computing language, it's obviously good because it has survived for so long. But when it comes to writing optimized code, there is no substitute for understanding what's going on. A compiler will only take you so far, but in the end it's up to the programmer. At that point, it doesn't matter what language you're using.
hehe. I guess that at some point engineers/scientists and programmers really have to talk to each other in order to improve their codes and programs.

---

### Post by Lootbox on 2010-08-03
The Matlab test isn't really fair considering how slow for-loops are in Matlab.

---

### Post by perroazul on 2010-08-03
> **lootbox said:**
> the matlab test isn't really fair considering how slow is matlab.

ftfy ;)

---

### Post by perroazul on 2010-08-06
> **perroazul said:**
> 
and compiled the C code as follows
```

gcc bench_c.c -lm -O4 -ffast-math -msse2 -mfpmath=sse -o bench_c

```
I used the same options with gfortran.


using those flags (-msse2 -mfpmath=sse) increased the execution time for both C and Fortran executables, and also made them run in similar times.  I'll look into that and post the best results with a combination of those flags.

---

### Post by Silentvoice on 2010-08-06
> **perroazul said:**
> using those flags (-msse2 -mfpmath=sse) increased the execution time for both C and Fortran executables, and also made them run in similar times.  I'll look into that and post the best results with a combination of those flags.


Was this for the new code (with the logarithm), or for the old code? In a bit I might compile your codes on a machine I use for testing HPC codes and see what I get. I tried to get GCC to auto-vectorize earlier and couldn't get it to do squat, had to do it all in inline asm. It'll use all the SSE registers, but only do the single FP ops for some reason, which is kind of silly. I don't really do much Fortran though.

Also, what's the -O4 option do? I don't see it in the docs for GCC, did you mean to use -O3? Docs could be out of date though. I'm pretty sure -O3 is the most aggressive optimization flag (that also keeps everything standard, and safe).

I still don't think that's a very valid benchmark, but I am now pretty interested in what the difference is between the compilers on the use of different floating point instruction sets.

The thing is that not all floating point operations are created equal. The only real way to truly benchmark one language against another is to have them both solve many many (real) problems and see how they do. Here's one such comparison:

[http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=ifc&lang2=gcc](http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=ifc&lang2=gcc)

A compiler has to do a lot of things for optimization, and just having a huge chunk of floating point operations doesn't mean it will still do all the same optimizations. It has to schedule instructions so that pipelining is used as efficiently as possible, this may not be possible in some cases (e.g. Newton-Raphson, Runge-Kutta) where there is a lot of data dependence. It has to fiddle with your logic so that the CPU's branch prediction is as accurate as possible (this is a minor problem in scientific computing problems usually). Then there's using arch-dependent stuff like SSE-SSE4.2, which is difficult to do automatically (similar problem to automatic parallelization). There is also a technique called strip mining loops, which tries to take advantage of the instruction cache (L1 on Intel), this can also help make use of L2-L3 cache too, but that depends on what's happening.

In the end though, like I said before, it's up to the programmer.

---

### Post by Silentvoice on 2010-08-06
Well here's what happened on my machine, I don't do much Fortran so I don't know if this is just due to misuse of the compiler. I compiled both your exact codes, and here's the reason on my machine at least the Fortran ran much faster:

(inner loop)
```
 
 39         cvtsi2ss        -16(%rbp), %xmm1
 40         cvtsi2ss        -8(%rbp), %xmm0
 41         mulss   %xmm0, %xmm1
 42         cvtsi2ss        -12(%rbp), %xmm0
 43         mulss   %xmm1, %xmm0
 44         sqrtss  %xmm0, %xmm0
 45         movss   %xmm0, -20(%rbp)
 46         movl    -36(%rbp), %eax
 47         cmpl    %eax, -12(%rbp)
 48         sete    %al
 49         movzbl  %al, %eax
 50         addl    $1, -12(%rbp)
 51         testl   %eax, %eax
 52         jne     .L6
 53         jmp     .L7

```

The suffixes "ss" stands for "scalar single" meaning the operation works on a single 32 bit floating point number. Here's the C code:

```

 23         cvtsi2sd        -16(%rbp), %xmm1
 24         cvtsi2sd        -12(%rbp), %xmm0
 25         mulsd   %xmm0, %xmm1
 26         cvtsi2sd        -8(%rbp), %xmm0
 27         movapd  %xmm1, %xmm2
 28         mulsd   %xmm0, %xmm2
 29         movsd   %xmm2, -24(%rbp)
 30         sqrtsd  -24(%rbp), %xmm0
 31         ucomisd %xmm0, %xmm0
 32         jp      .L13
 33         je      .L8

```

The suffix "sd" stands for "scalar double" meaning it operates on a single 64 bit floating point number. It's less instructions, but double precision math is also roughly twice as slow as single precision math, accounting for your discrepancy.

Both of these were compiled as such:

```

gfortran -S fbench.f90
gcc -S cbench.c

```

-S just gives assembler output.

---

### Post by KIAaze on 2010-08-06
The fortran code uses "real", while the C code uses "double".

According to [this page]("http://www.math.utah.edu/software/c-with-fortran.html#common-types"), it should be real/float or float/REAL or double/DOUBLE PRECISION.

Another related link:
[http://www-classes.usc.edu/engr/ce/108/text/fbk01.htm](http://www-classes.usc.edu/engr/ce/108/text/fbk01.htm)

However, in my case (32-bit machine), both assembler outputs used "fsqrt".

---

### Post by perroazul on 2010-08-07
> **Silentvoice said:**
> I tried to get GCC to auto-vectorize earlier and couldn't get it to do squat, had to do it all in inline asm. It'll use all the SSE registers, but only do the single FP ops for some reason, which is kind of silly. I don't really do much Fortran though.

this is chinese to me :D, I'm not really a programmer. If matlab were as fast as fortran or C, I wouldn't bother using anything else.
> 
Also, what's the -O4 option do? I don't see it in the docs for GCC, did you mean to use -O3? Docs could be out of date though. I'm pretty sure -O3 is the most aggressive optimization flag (that also keeps everything standard, and safe).

I regularly used that flag, until a couple of years ago, when I was using a borland fortran compiler. when you use it with gfortran it interprets it as -O3. I was just to lazy to change all my make files to -O3 

> 
The suffix "sd" stands for "scalar double" meaning it operates on a single 64 bit floating point number. It's less instructions, but double precision math is also roughly twice as slow as single precision math, accounting for your discrepancy.

ok. I was also suspecting that. thank you and thanks KIAze for pointing that out too. while checking both codes I noticed also that the C loop ran from 0, to n-1 and the fortran one from 1 to n (actually I wasn't sure about the exact C syntax and I had to check to make them equal killing a possible source of discrepancy). I made those corrections and left the executables running yesterday (compiled them with -O4 -ffast-math only), but after the last posts I believe that the times should be comparable. I have learned a bunch of things from this thread nonetheless. thanks guys :)

---

### Post by Azrael3000 on 2010-08-08
for more details on the -O4 / -O5 flags see:
[http://www.nersc.gov/nusers/resources/software/ibm/opt_options/on.php](http://www.nersc.gov/nusers/resources/software/ibm/opt_options/on.php)
[http://www.nersc.gov/nusers/resources/software/ibm/opt_options/ipa.php](http://www.nersc.gov/nusers/resources/software/ibm/opt_options/ipa.php)

So it's really not just O3 if you use an appropriate compiler. Basically -O4 / -05 do processor specific optimization which is not done by the lower ones. They only optimize the code itself.

---

### Post by ssam on 2010-08-08
C is more flexible than FORTRAN. sometimes the compiler can't optimise something, because the side effects are less predictable. for example you could have 2 pointers pointing to the same memory, so the compiler can't assume that a value has not changed, just because you have not explicitly changed it. it is worth using keywords like const and restrict as much as you can.

also seen as you program does nothing with the results, you risk the optimiser just dropping the pointless "sqrt(((double)i)*((double)j)*((double)k));" line.

if you are really trying to write high performance code then it needs to parallelise. so the real question is in which language can you write the best parallel code?

---

### Post by perroazul on 2010-08-09
> **ssam said:**
> C is more flexible than FORTRAN. 
definitely!. no doubt about that
> **ssam said:**
> 
if you are really trying to write high performance code then it needs to parallelise. so the real question is in which language can you write the best parallel code?
now, that is a very interesting question. I have little knowledge about parallelization. I have used the MPI library before, and as far as I know, its use is similar in both languages. care to share any insights you have about this topic with us, please?
> **ssam said:**
> 
also seen as you program does nothing with the results, you risk the optimiser just dropping the pointless "sqrt(((double)i)*((double)j)*((double)k));" line.
indeed that happened :D
I'll post the execution times together with the corrected codes and compilation flags as soon as I have time.

---

### Post by perroazul on 2010-08-10
the execution times below
```

fortran
7:54:38.40 (7 hours 54 minutes 38.4 seconds)
C
7:54:06.71 (7 hours 54 minutes 6.7 seconds)

```
were obtained when compiled as shown here
```
gfortran bench_f.f90 -O4 -ffast-math -o bench_f
gcc bench_c.c -lm -O4 -ffast-math -o bench_c

```
and the revised codes are
```

#include <stdio.h>
#include <math.h>
int main(){
    int n = 10000;
    int i, j, k;
    double x;
    for (i = 1; i <= n; i++){
        for (j = 1; j <= n; j++){
            for (k = 1; k <= n; k++){
                x=sqrt(((double)i)*((double)j)*((double)k));
            }
        }
    }
    printf("x = %f\n", x); 
    return 0;
}

```
and fortran:
```

program test
integer :: i,j,k,n
real*8 :: x    !double precision real
n=10000
do i=1,n
   do j =1,n
      do k=1,n
         x = sqrt(dble(i)*dble(j)*dble(k))
      enddo
   enddo
enddo
print*, x
end program test

```

---

### Post by ssam on 2010-08-11
the optimiser could still drop all but the last iteration of the code.

anyway, parallelisation with openmp 
```

#include <stdio.h>
#include <math.h>
int main(){
    int n = 10000;
    int i, j, k;
    double x;
#pragma omp parallel for
    for (i = 1; i <= n; i++){
        for (j = 1; j <= n; j++){
            for (k = 1; k <= n; k++){
                x=sqrt(((double)i)*((double)j)*((double)k));
            }
        }
    }
    printf("x = %f\n", x); 
    return 0;
}

```
compile with
```

gcc bench.c -lm -O4 -ffast-math -o bench_c -fopenmp

```
4 times faster on my quadcore :-) . in this case it may output a different answer, cause all the threads are overwiting the same x. in a real code they would probably be writing to different elements of an array.

(the openmp trick works in fortran too. but i have seen fortran code where the layout has made it impossible)

---

### Post by Silentvoice on 2010-08-13
> now, that is a very interesting question. I have little knowledge about parallelization. I have used the MPI library before, and as far as I know, its use is similar in both languages. care to share any insights you have about this topic with us, please?

I think in this respect, Fortran and C are roughly equivalent. Really it's a matter of taste. In general it's best to make what you are doing very apparent to the compiler, because then it can perform better optimizations. Fortran has an advantage here because it is more domain specific. It was created with the explicit intention of making numerics easier for the working scientist/engineer. C on the other hand was designed to be a low level language that can be used for applications ranging from embedded systems to OS design. It can be used for numerics also, but more consideration must be taken into account when writing it. C does not assume you are doing numerics.

I gravitate towards C for this reason though. Being close to the system means also that it's easier to take advantage of architecture dependent features. It also means that future revisions of the standard will deviate very little from this paradigm.

---

### Post by perroazul on 2010-08-13
> **Silentvoice said:**
> Really it's a matter of taste. In general it's best to make what you are doing very apparent to the compiler, because then it can perform better optimizations. Fortran has an advantage here because it is more domain specific. It was created with the explicit intention of making numerics easier for the working scientist/engineer. C on the other hand was designed to be a low level language that can be used for applications ranging from embedded systems to OS design. It can be used for numerics also, but more consideration must be taken into account when writing it. C does not assume you are doing numerics.

I think that this comment summarizes what I have learned in this thread and answers my original question. thanks

---

### Post by perroazul on 2010-08-13
> **ssam said:**
> 
anyway, parallelisation with openmp 

here is the change you did, but in fortran version:
```
program test
integer :: i,j,k,n
real*8 :: x
n=10000
!$OMP PARALLEL do
do i=1,n
   do j =1,n
      do k=1,n
         x = sqrt(dble(i)*dble(j)*dble(k))
      enddo
   enddo
enddo
!$omp end parallel do
print*, x
end program test
```
which then I compiled as follows
```
gfortran bench_f.f90 -O4 -ffast-math -fopenmp -o bench_f
```
the results are below
```

time ./bench_c
2:13:06.34 (2 hours 13 minutes 6.34 seconds)
time ./bench_f
2:10:19.09 (2 hours 10 minutes 19.09 seconds)

```
roughly, a fourth of the time without the parallel instructions. awesome!!
although, it seems that openmp works with shared memory systems. Do you know if it works with distributed memory systems? it would be nice to be able to use those instructions in a real cluster. MPI is much harder to use, you have to explicitly control the flux of information between the machines you're using.
> **ssam said:**
> 
(the openmp trick works in fortran too. but i have seen fortran code where the layout has made it impossible)
could you be more specific? do you remember any specific examples?

P.S. if any of you guys change the instruction sqrt(i*j*k) to sqrt(i)/j +log(k), the execution time (both for fortran and C codes) increases a lot. it goes from 7 hours, 54 min to 18 hours, 25 min.

---

### Post by Silentvoice on 2010-08-13
> **perroazul said:**
> here is the change you did, but in 
although, it seems that openmp works with shared memory systems. Do you know if it works with distributed memory systems? it would be nice to be able to use those instructions in a real cluster. MPI is much harder to use, you have to explicitly control the flux of information between the machines you're using.


It is unlikely that a shared memory paradigm will ever provide scalable performance for clusters. Intel IS working on their own implementation of OpenMP which they claim will scale well to clusters. I find this difficult to believe, however: [http://software.intel.com/en-us/articles/cluster-openmp-for-intel-compilers/](http://software.intel.com/en-us/articles/cluster-openmp-for-intel-compilers/)

Something you might find interesting though is a (relatively) new paradigm which attempts to take the best of both worlds from distributed and shared paradigms. It's called Parallel global address space (PGAS): Here's some implementations of this model:

Unified ParallelC:
[http://en.wikipedia.org/wiki/Unified_Parallel_C](http://en.wikipedia.org/wiki/Unified_Parallel_C)

Co-Array Fortran
[http://en.wikipedia.org/wiki/Co-array_Fortran](http://en.wikipedia.org/wiki/Co-array_Fortran)


It is supposed to make distributed programming simpler, while maintaining the scalability of explicit message passing.

---

### Post by ssam on 2010-08-13
> **perroazul said:**
> 
could you be more specific? do you remember any specific examples?


a particle tracking code. it had a loop that went though all the particles in an array. for each particle it would load its coordinates into some global variables, and then call a bunch of subroutines that acted on the global variables. use of fortran features like gotos, computed gotos, multiple entry points to subroutines etc make the code hard to follow, so re-factoring would be a scary task.

in C you would tend to either pass the data to a function as an argument, or pass a pointer to the data. this means you can call the function simultaneously with different arguments.

---

### Post by perroazul on 2010-08-19
> **ssam said:**
> use of fortran features like gotos, computed gotos, multiple entry points to subroutines etc make the code hard to follow, so re-factoring would be a scary task.

in C you would tend to either pass the data to a function as an argument, or pass a pointer to the data. this means you can call the function simultaneously with different arguments.
I don't see why that wouldn't be possible with fortran. also, using gotos etc seems a bit like using outdated bad programming practices to me. 
gotos were common with the fortran 77 standard, but not anymore.

---

### Post by Silentvoice on 2010-08-19
> **perroazul said:**
> I don't see why that wouldn't be possible with fortran. also, using gotos etc seems a bit like using outdated bad programming practices to me. 
gotos were common with the fortran 77 standard, but not anymore.


Well actually Fortran passes by reference by default. C does not (except with arrays, which due to the way they're represented in C you have no choice but to pass by reference). So it's not really an advantage of C that you can do this.

Also goto still exists in C, in fact so does the dreaded longjmp. I think arguments for a particular language based on its intended style are in the end pointless. It's up to the programmer to write good code, no set of standards will think for you.

---

### Post by perroazul on 2010-08-20
> **Silentvoice said:**
> 
Also goto still exists in C, in fact so does the dreaded longjmp. I think arguments for a particular language based on its intended style are in the end pointless. It's up to the programmer to write good code, no set of standards will think for you.

I thought that you and I agreed with respect to the parallelization capabilities of both languages:
> **Silentvoice said:**
> I think in this respect, Fortran and C are roughly equivalent. Really it's a matter of taste.
**ssam** was arguing about C being better than fortran in this respect (parallelization), basing his argument in some example of a particle tracing code, and the use of gotos, etc, but I'm not sure about that being really an issue, unless there is no other way for you to translate that particular algorithm to fortran code but using gotos or something else that would kill the possibility of parallelization. 
I still think that fortran and C should be roughly equivalent with respect to making your code parallelizable.

---

### Post by Silentvoice on 2010-08-20
> **perroazul said:**
> I thought that you and I agreed with respect to the parallelization capabilities of both languages:

**ssam** was arguing about C being better than fortran in this respect (parallelization), basing his argument in some example of a particle tracing code, and the use of gotos, etc, but I'm not sure about that being really an issue, unless there is no other way for you to translate that particular algorithm to fortran code but using gotos or something else that would kill the possibility of parallelization. 
I still think that fortran and C should be roughly equivalent with respect to making your code parallelizable.

I should have been more clear. I was responding to what he said, but directing it at you since you're so curious about the differences.


[Edit] Fact is that neither C nor fortran are particularly well suited to parallel programming by themselves. The reason people use them is ubiquity, and portability. Neither has built in concurrency features (but the new C standard is supposed to include multithreaded programming). Programming in parallel is still a paradigm shift, even though it's been around for us scientific computation people for nearly thirty years. That lack of demand though shows itself in the tools available to us. This will change dramatically in the coming years, I think.

---

### Post by perroazul on 2010-08-23
> **Silentvoice said:**
> 
[Edit] Fact is that neither C nor fortran are particularly well suited to parallel programming by themselves. The reason people use them is ubiquity, and portability. Neither has built in concurrency features (but the new C standard is supposed to include multithreaded programming). 

that sounds interesting. meanwhile I'm investing some time in learning openMP. I'm really surprised about how easily you can paralellize a code for using it with a multicore machine. considering how common are those nowadays, being able to divide your execution time by a fraction really pays off.  
I'll be posting anything that I find useful or interesting

---

### Post by Azrael3000 on 2010-08-23
well OpenMP is nice for starters (and multicore machines) but for really large scale projects (which "should" be standard in scientific computing) you'll require MPI. Shared memory just won't do the trick on real clusters (which doesn't mean that it can't be used in combination with MPI).

---

### Post by perroazul on 2010-08-23
> **Azrael3000 said:**
> well OpenMP is nice for starters (and multicore machines) but for really large scale projects (which "should" be standard in scientific computing) you'll require MPI. Shared memory just won't do the trick on real clusters (which doesn't mean that it can't be used in combination with MPI).

yes indeed. as I stated in a previous post I learned about the "parallel universe" of programming with MPI. however MPI is much harder to use than openMP. and from what I've been reading you only need to do minor modifications to an existing code to make it parallel in a SMC.

---

### Post by rubecdrevo on 2010-08-24
Every year there is more updating for the scientific computing, I think tell now the best is C++, as I think windows XP is the best even there are new operating systems every year

---

### Post by perroazul on 2011-01-27
I decided to learn a bit of C++ and now, I definitely and absolutely prefer fortran 90. check the following fortran 90 code for matrix times vector multiplication and compare it to the equivalent C++ code taken from [[COLOR="Blue"]this page[/COLOR]]("http://www.physics.utah.edu/~detar/lessons/c++/matrices/node3.html"):
```
program vectmatmult
  implicit none
  integer :: i,j,m,n
  real, dimension (:), allocatable :: x,b
  real, dimension (:,:), allocatable :: a
  
  print*,'Enter the number of rows in the matrix'
  read*, m
  print*,'Enter the number of columns in the matrix'
  read*, n
  allocate(a(m,n))
  allocate(x(m))
  allocate(b(m))

  print*, 'Enter the matrix'
  do i=1,m
     read*, (a(i,j), j=1,n)
  enddo
  print*, 'Enter the vector'
  do i=1,m
     read*, x(i)
  enddo

  call mulmatvec(m,n,a,x,b)
  
  print*, 'A*x ='
  do i=1,m
     print*, b(i)
  enddo

  deallocate(x,b,a)
contains
  subroutine mulmatvec(m,n,a,x,b)
    integer i,j
    integer, intent(in) :: m,n
    real, dimension(:) :: x,b
    real, dimension(:,:) :: a
    do i=1,m
       b(i)=0.
       do j=1,n
          b(i)=b(i)+a(i,j)*x(j)
       enddo
    enddo
  end subroutine mulmatvec
end program vectmatmult

```
The fortran 90 syntax is way simpler and clearer than C++ syntax. consider for example the code for dynamic memory allocation for the matrix a:
```
  double **a = new double* [m];
  for(i = 0; i < m; i++)
    a[i] = new double[n];
```Compare that beast to the fortran 90 code below:
```
allocate(a(m,n))
```You don't even have to worry about pointers!

---

