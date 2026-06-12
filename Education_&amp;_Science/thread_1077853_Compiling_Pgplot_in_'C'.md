---
title: "Compiling Pgplot in 'C'"
date: 2009-02-22
forum: Education &amp; Science
---

### Post by SuperNomad on 2009-02-22
As part of my course at university I get to explore the world of fractals, via the medium of C programming and pgplot. I can do all the compiling using the university linux machines in which the code I have is all set up for.

However I would like to be able to do all this in the comfort of my own home but I have no idea how to set up pgplot5.2.2 to compile my code.

This is the code I'm trying to compile:

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <cpgplot.h>

/* source /home/z/zrw/under/pgplot_c (set up just once a session)
    cc fractal1.c `cpgplot_link` -o fractal1 (to compile program) */

/* maximum number of iterations for each point */
#define NITER 10000
/* number of columns in image */
#define NCOLS 800
/* number of rows in image */
#define NROWS 400

/* function to set colour table in pgplot */
void cpgsetlut();

int main()
{
  float rmin = -2.0, rmax = 2.0;
  float pix=(rmax-rmin)/NCOLS;
  float imin = -1.0, imax = imin+NROWS*pix;
  double rtarget=1.e8, cr=-0.74543, ci=0.11301;
  int i,j,ni;
  float arr[NROWS*NCOLS], tr[6], zmin, zmax;
  double rs,vr,vi,sr,si,tt;
  zmin=NITER;
  zmax=0.0;
  for(i=0; i<NROWS; i++) {
    si=imin+pix*(i+0.5);
    for(j=0; j<NCOLS; j++) {
      sr=rmin+pix*(j+0.5);
      vr=sr;
      vi=si;
      rs=vr*vr+vi*vi;
      ni=0;
      while((rs<rtarget)&&(ni<NITER)) {

/* 4 lines to calculate the quadratic mapping missing */

	tt = vr ;
	vr = (vr*vr - vi*vi)  + cr ;
	vi = (2*tt*vi) + ci ;
	rs = vr*vr + vi*vi ; 
        
	ni++;
      }
      tt=ni; tt=log(tt);
      arr[j+i*NCOLS]=tt;
      if(zmax<tt)
        zmax=tt;
      if(zmin>tt)
        zmin=tt;
    }
  }
  cpgbeg(0, "?", 1, 1);
  cpgsetlut();
  cpgwnad(rmin,rmax,imin,imax);
  tr[0]=rmin-0.5*pix; tr[1]=pix; tr[2]=0.0;
  tr[3]=imin-0.5*pix; tr[4]=0.0; tr[5]=pix;
  cpgimag(arr,NCOLS,NROWS,1,NCOLS,1,NROWS,zmin,zmax,tr);
  cpgbox("BCTN", 0.0, 0, "BCNST", 0.0, 0);
  cpglab("real axis","imaginary axis","Julia set by the Level Set Method");
  cpgend();
}

void cpgsetlut()
{
  int i,icmin,icmax,n1,n2;
  float dd, rcol,gcol,bcol;
  cpgqcir(&icmin,&icmax);
  dd=3.0/(icmax-icmin);
  n1=icmin+(icmax-icmin)/3;
  n2=icmin+((icmax-icmin)*2)/3;
  for(i=icmin; i<icmax+1; i++) {
    if(i<=n1) {
      rcol=(i-icmin)*dd; gcol=0.0; bcol=0.0;
    } else if((i>n1)&&(i<=n2)) {
      rcol=1.0; gcol=(i-n1)*dd; bcol=0.0;
    } else if(i>n2) {
      rcol=1.0; gcol=1.0; bcol=(i-n2)*dd;
    }
    if(rcol>1.0) rcol=1.0; if(gcol>1.0) gcol=1.0; if(bcol>1.0) bcol=1.0;
    cpgscr(i,rcol,gcol,bcol);
  }
}

To enable this to work at the start of each session I execute the source command at the top. Howver all this appears to do is make `cpgplot_link` as echo `cpgplot_link` doesn't work before the source command is executed.

Doing echo `cpgplot_link` after returns this:

 echo `cpgplot_link`
-I /home/z/zrw/pgplot -B /home/z/zrw/pgplot -lcpgplot -lpgplot -lf2c -L /usr/X11R6/lib -lX11 -lgcc -lm -lc /usr/lib/libf77blas.so.2.3

Which I'm guessing is what I need to run to compile the code, however I don't have libf77blas.so.2.3. (as well as some of the other bits)

Can anyone tell me how to compile the code on ubuntu 8.1, the university is using debian (if that helps).

Thanks in advance

---

### Post by Endless_Nameless on 2009-05-29
I think you already found your answer somewhere, but here we go:

You can install pgplot in Ubuntu using the apt-get (as root):

# apt-get install pgplot5

To compile your code I write

# cc fractal1.c -o fractal1 -L/usr/lib/ -lcpgplot -lpgplot -lm

which generated a beautiful image (I wish I know how to zoom in it!). Thanks for this image!

---

