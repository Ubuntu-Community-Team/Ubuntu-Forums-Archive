---
title: "Good 3D data Visualization Library"
date: 2008-09-09
forum: Education &amp; Science
---

### Post by Telescope_Nerd on 2008-09-09
Hi there, I am a bit of a noob with all the terminology around this subject so I am just going to spell out exactly what I am trying to do and any advice or tips are very welcome.

The Plan:
I have created some software for simulating the flight path of hobby rockets which is being released soon as a tool box for Octave: [http://cambridgerocket.sourceforge.net/]("http://cambridgerocket.sourceforge.net/")

But now I want to turn it into a stand-alone program. So I have written the core simulation part in C++ and it works great but it just produces lots of numbers and I need to visualize them.

So I want my program to output 2D and 3D scatter and line plots of flight paths after a simulation. So I guess I need a library for c++ or another language is fine too (e.g. Java), but it must be open source.

Help please!:
I am quite new to all this and web searches are just bamboozling me with terms like OpenGL VTK etc none of which I fully understand. If you have any tips for good libraries or resources that can help me learn more please let me know! Thanks.

TN.

---

### Post by ProgramErgoSum on 2008-09-09
Check out [GNUPlot]("http://www.gnuplot.info/").

Excerpt :> 
Gnuplot  is a portable command-line driven interactive data and function plotting utility for UNIX, IBM OS/2, MS Windows, DOS, Macintosh, VMS, Atari and many other platforms. The software is copyrighted but freely distributed (i.e., you don't have to pay for it). It was originally intended as to allow scientists and students to visualize mathematical functions and data. It does this job pretty well, but has grown to support many non-interactive uses, including web scripting and integration as a plotting engine for third-party applications like Octave. Gnuplot has been supported and under development since 1986.

Gnuplot supports many types of plots in either 2D and 3D. It can draw using lines, points, boxes, contours, vector fields, surfaces, and various associated text. It also supports various specialized plot types. 

---

### Post by kaspar_silas on 2008-09-09
Gnuplot is a really good idea. In case you want another, a really nice option in the pngwriter libraries. It can be installed from synaptic (libpng12-0) and (libpng12-dev). 

You can find full details on the package at 
[http://pngwriter.sourceforge.net/]("http://pngwriter.sourceforge.net/")
which details how to do everything you could want.


For an simple example program take the following.

```

#include "pngwriter.h"
#include <iostream>
int main()
{
   int i;

   pngwriter png(400,300,0.999,"test.png");
   /*Make a 400,300 white window called test*/

   for(i = 1; i < 900;i++)
     {
        png.plot(i,150+100*sin((double)i*45/900.0), 1.0, 0.0, 0.0);
        /*The above plots a red sin graph*/
     }
   png.close();

   system("eog test.png");/*If you want to show the file*/
   system("rm test.png");/*If you want the remove the file after*/

   return 0;
}

```

Once you installed pngwriter, compile the above, remembering to link to the pngwriter library (check the link above if stuck how to do this) and bob's your uncle.

---

### Post by Nick Lake on 2008-10-01
You know what would be cool...

Use NVIZ and draw your trajectories in 3D against satellite imagery back drops and other 3D features.

---

### Post by slaanco on 2008-10-03
I have good experiences with piping C++ sim data to gnuplot :) worked for me without any problem

---

### Post by Zdravko on 2008-10-03
> **slaanco said:**
> I have good experiences with piping C++ sim data to gnuplot :) worked for me without any problem
Windows doesn't have the notion of pipes. Your solution is not portable.

---

