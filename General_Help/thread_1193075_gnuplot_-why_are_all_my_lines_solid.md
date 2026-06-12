---
title: "gnuplot -why are all my lines solid?"
date: 2009-06-21
forum: General Help
---

### Post by bebops_lost on 2009-06-21
ok, so I've used gnuplot for years, but something in the default features must have recently changed; the thing that I'm trying to do is staggeringly simple: all I want is to plot data with lines that are not solid (dashed, dotted -I don't care, I just want to be able to distinguish more than 3 different lines on a plot after printing it out in black and white )

suppose I have three files with tab-seperated data foo1.txt, foo2.txt, foo3.txt, and I want to be able to tell them apart after plotting and color just won't do. I try:

```
 $gnuplot 
>plot "foo1.txt" w l lt1, "foo2.txt" lt 2 w l, "foo3.txt" lt 3 w l

```
you'd think that would change the linetype, but it only changes the color, so I go to see what my linetype options are by typing ">test" and a list of line types is shown on the right with a whole bunch of lines in different colors (only one of them is not solid.) I used to just enter ">plot 'foo1' w l, 'foo2' w l ... etc" and it made different line types by default - so I know it *can* make dashes and dots, but now something has changed and every tutorial I find online just refers to the 'lt' option.
the only other clue I've got online is that I need to change my terminal, but I would really think it ought to be possible -by default- to have some lines solid and others not.

Is it really not possible to change the line type (i.e. dashed, solid. dotted, etc) ****_independent_**** of the color ? I'm going crazy here: It's such a simple thing for a plotting tool to do!  
I have faith in the smart people that maintain gnuplot, and I refuse to believe that they would omit such an obviously essential piece of functionality. I'm probably being the dumb one here, can someone tell me how?

---

### Post by bebops_lost on 2009-06-21
just a follow-up, I've also tried playing around with

$set terminal postscript portrait enhanced {solid | dashed } lw 1 "Helvetica" 14 

and switching solid <--> dashed, and dashlength etc. nothing seems to be working, I really need to get some plots out, and trying to learn how to use xmgrace at this point looks like a big investment (I thought I already knew gnuplot -and I know how to do lots more complicated stuff with gnuplot -this should be so simple!!!)
anybody?

---

### Post by bebops_lost on 2009-06-25
ok, well if anyone is still interested, it turns out the the line types seem to inextricably linked to the color type, and are different for each terminal type. I recommend doing this once:

```

set size 1.0, 0.6
set term postscript portrait enhanced color lw 1 "Helvetica" 14 

set output "test-ref.ps"
test
set terminal x11
set size 1,1

```

and saving the "test-ref" file as a reference for future use when you want to know what your lines are going to look like for a given type.

For the record though, I really think this is a cumbersome way of doing it. Perhaps there could be one command "lt" for dashes, dots, etc, and another one "lc" for line color with a few numbered options (i.e. 1-blue, 2-red, etc) standardized across the terminals. I think that would make it a lot easier, though I don't really know how to do this myself (and I do appreciate the hard work of the people who make gnuplot in the first place, I just think this change would make more people want to use it)

---

