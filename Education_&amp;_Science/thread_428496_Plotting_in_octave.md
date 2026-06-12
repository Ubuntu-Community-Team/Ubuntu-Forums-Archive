---
title: "Plotting in octave"
date: 2007-04-30
forum: Education &amp; Science
---

### Post by seyda on 2007-04-30
Hello. I use koctave and gnuplot. and when i make a plot, i can see it with gnuplot but i can't copy or paste or even do any thing with this plot. 
can someone tell me how to edit a plot?
Thank you...

---

### Post by harishg on 2007-05-02
The plot window does not have GUI interface like matlab does.You need to export the plot as an image file to be able to work with it.

---

### Post by ahmatti on 2007-05-03
You can edit the axis labels and title from the command window and print the figure into a file with print command.

Some examples:

```

xlabel('x-axis')
ylabel('y-axis')
title('plot title')
legend('plot legend')
print('-dpsc','figure.ps')

```

See Octave help for more info.

---

### Post by ahmatti on 2007-05-03
I have spent some time trying to get good quality plots in octave and I thought I'd post one function that I have made for my own usage. I know this is not perfect but maybe it helps someone...

I am quite happy with the output, the only problem is that I get too wide lines for the axis. If you know how to fix the issue please post!

I call the function "psprint" and the usage is psprint('filename')

```

function psprint(filename)
#Set linewidth and font size 
__gnuplot_set__ terminal postscript color eps lw 5 "Helvetica" 25
#Set figure size relative x,y
__gnuplot_set__ size 0.8,1
#Choose the legend position
__gnuplot_set__ top right
#Set the filename
a=(['__gnuplot_set__ output "' nimi '.ps"'])
eval(a)
#Print to file
replot

```

---

### Post by seyda on 2007-05-03
thank you for the advices. I want to ask one more thing : I think there exist an interface for gnuplot named xgnuplot. I searched for it on the net but I couldn't able to download it. (there was a japan ftp and couldn't connect to the server). do you know anyhing about it?

---

### Post by dstein on 2008-04-06
Does anyone know how to change the font size or other font properties of the labels created on Octave plots? Thanks.

---

### Post by dstein on 2008-04-06
So it seems that when using the print function to output a figure to an EPS file, I can use the -F:size argument to modify the size. However, this argument seems to modify the size of all text, including the axis labels, axis titles, figure title, ...

Is there any way to modify these with more control, such that I can make some of the text large and some small (and edit other font/text options)? I am mostly concerned with the output file, not the actual presentation on the screen while using octave.

---

### Post by Xnst on 2008-08-22
Hi!

When I use octave for making figures to print I format
the output in the m-file, like this: 

---------------------------------------
figure(1)
plot(a3(:,2),a3(:,1),'-r',"linewidth",3)
hold on
plot(a1(:,2),a1(:,1),'-b',"linewidth",3)
plot(a2(:,2),a2(:,1),'-g',"linewidth",3)
hold off
axis([0 2 0 16])
legend('orig','3% plast','8% plast',"fontsize",14)
xlabel('strain (%)',"fontsize",14)
ylabel('stress (MPa)',"fontsize",14)
--------------------------------------

Then You just do a :

print -dpng filename.png

or similar.

Hope it helped!

---

### Post by mdecler2 on 2008-09-06
> **Xnst said:**
> Hi!
Then You just do a :

print -dpng filename.png

or similar.

Hope it helped!

I have a problem with this above suggestion. I get
```
gdImageStringFT: Could not find/open font while printing string <SOME_STRING_VALUE> with font Helvetica
```
Where <SOME_STRING_VALUE> is a label I used on the graph. In fact I get this message repeated for all labels I have set, and the output file just fails to contain the labels.

I am using Hardy Heron.

---

### Post by Xnst on 2008-09-12
Hi,

I had the same problem. Something with gdfont(I think it was something like that).I found a post that described the problem and solution, but unfortunately I do not remember where. Basically you do not have helvetica in your system in the format this gdfont like it to be. But you can always use another font. Just tell gdfont the new font: put this in your .profile. for use of bistream-vera (use your own preference)


```

export GDFONTPATH="/usr/share/fonts/truetype/ttf-bitstream-vera"
export GNUPLOT_DEFAULT_GDFONT="Vera.ttf"

```

The last row above is said to work, but for me I do not think it does. Therefore, I force the vera font to the text by adding the "FontName" definition:

```

xlabel('strain (%)','FontName','Vera','FontSize',14)
ylabel('stress  (MPa)','FontName','Vera','FontSize',14)

```


I think you get the idea. 

Regards
Niclas

---

### Post by mdecler2 on 2008-09-22
Thank you Xnst! I find your second solution, forcing a system identified font into the script, is suitable for my needs.

---

### Post by snakep on 2008-09-23
Hello, I also have a question about plotting in octave, and I thought I'd post here rather than start a new thread.

I have created an octave program to plot a function.  The program seems to execute fine, and I get the return value that I want, but it does not print from within the program.  I can print from the command line, though.

How do I plot from within an octave program or script?

Thanks,

Jeremiah

---

### Post by snakep on 2008-09-23
Never mind, I figured it out.  Stupid mistake on my part.

Jeremiah

---

### Post by garba on 2008-09-24
i think the best thing to do when using different computing platforms is saving the output to a file and then process it through an external plotting app such as gnuplot and the like (btw its pslatex terminal rocks)

---

### Post by jdoge13 on 2008-10-09
I have the same issue as the original poster, however assigning a specific font (no matter the font) still gives the same results. It graphs fine, it just will not print to file.
*Edit:
I figured out the problem wasn't with the font.  For some reason it just didn't want to print to a .png file.  I changed the file type to a epsc file and it works like a dream now (with any font).

---

### Post by browny254 on 2008-10-19
> **Xnst said:**
> Hi,

I had the same problem. Something with gdfont(I think it was something like that).I found a post that described the problem and solution, but unfortunately I do not remember where. Basically you do not have helvetica in your system in the format this gdfont like it to be. But you can always use another font. Just tell gdfont the new font: put this in your .profile. for use of bistream-vera (use your own preference)


```

export GDFONTPATH="/usr/share/fonts/truetype/ttf-bitstream-vera"
export GNUPLOT_DEFAULT_GDFONT="Vera.ttf"

```

The last row above is said to work, but for me I do not think it does. Therefore, I force the vera font to the text by adding the "FontName" definition:

```

xlabel('strain (%)','FontName','Vera','FontSize',14)
ylabel('stress  (MPa)','FontName','Vera','FontSize',14)

```


I think you get the idea. 

Regards
Niclas

Hi, Im having the same problem, but the solution here isnt working.

the export command, where am I meant to do that? I have just done it in a terminal window but there is no confirmation that it has done anything, do I have to be in a specific directory?

Any ideas?

---

### Post by kg4gyt on 2008-10-19
Any thoughts on what to do when most of the plotting is done by a built in function?

I'm trying to plot a bode plot, and I need to be able to export it as a PNG, but no matter what I do it seems to always want the Helvetica font.

---

### Post by Morrad on 2008-10-21
> **Xnst said:**
> Hi,

I had the same problem. Something with gdfont(I think it was something like that).I found a post that described the problem and solution, but unfortunately I do not remember where. Basically you do not have helvetica in your system in the format this gdfont like it to be. But you can always use another font. Just tell gdfont the new font: put this in your .profile. for use of bistream-vera (use your own preference)


```

export GDFONTPATH="/usr/share/fonts/truetype/ttf-bitstream-vera"
export GNUPLOT_DEFAULT_GDFONT="Vera.ttf"

```

The last row above is said to work, but for me I do not think it does. Therefore, I force the vera font to the text by adding the "FontName" definition:

```

xlabel('strain (%)','FontName','Vera','FontSize',14)
ylabel('stress  (MPa)','FontName','Vera','FontSize',14)

```


I think you get the idea. 

Regards
Niclas

To clarify, Xnst, you mention setting the export commands in ".profile".  If I put those commands in my ~/.profile, Ubuntu gets an error on login, and I have to take it out.  Is there another .profile that you're referring to?  Where are you suggesting putting those commands?

---

### Post by mdecler2 on 2008-11-03
To clarify, Xnst has said that exporting the font to an environment variable did not work for him. It did not work for me either. His second suggestion was to modify the xlabel(...) and ylabel(...) commands in the Matlab .m script to force gnuplot to use a different font other than Helvetica (namely, Vera). This worked for me. You can see his syntax above.

If neither proposed solution works, you could try outputting the plot in a different format, like eps. you can do this with ```
print('-deps','name_of_plot.eps');
``` I believe that the -d means 'driver'. Use the eps driver to convert the gnuplot into an eps file. EPS is just one format among many, you can look it up on Wikipedia. You can find out the formats that most octave installations support at [http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/learn_matlab/f3-1212.html&http://www.google.com/search?hl=en&q=matlab+print(%27-depslatex%27&btnG=Search]("http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/learn_matlab/f3-1212.html&http://www.google.com/search?hl=en&q=matlab+print(%27-depslatex%27&btnG=Search")

---

### Post by Xnst on 2008-11-11
Hi Morrad,

I have been away for a couple of weeks and could not answer you until now. 

Yes, I have the export lines in my ~/.profile and for me it works, no error at all. However, I still have to force gnuplot to choose Vera with

```
xlabel('text','FontName','Vera','FontSize',14)
```

in my m-file. It works, but it is not really efficient.

What type of error do you get? Is it the wrong font path? 

As for the different types of output formats, octave does not seem to support all formats as matlab does. As an example jpeg is not fully supported. 

```
>> help print
```

gives the options you can use. However, the -FFONT does not seem to work for switching font on labels and titles, just the numbers.

---

### Post by JHBrewer on 2010-10-01
I would like to be able to make a publishable 2D plot in Octave, but nothing I have found will generate a plot with axis **numbering** that would survive the usual size reduction for two-column journals.  I have learned how to control the fonts used in axis labels and titles, so those are fine, but there seems to be no control whatever over the font size used for the **numbers **that go beside the tick marks on the axes.  Perhaps I have just failed to guess what these are called in Octave and/or Gnuplot.  

I had the same problem in Gnuplot, but was able to solve it (sort of) by simple making the whole plot smaller (set size).  This was once possible with the old __gnuplot_set__ command, but it has been deprecated and its effect turned off.  This logically implies that some other command has taken its place, but if so, I have been unable to discover it.   

Since no one could publish a Figure with tiny little numbers, I assume that someone must know a way around this problem.  I would be happy to know it, but much happier to see the Octave documentation address it directly.

---

### Post by PureW on 2010-11-03
> **JHBrewer said:**
> 
Since no one could publish a Figure with tiny little numbers, I assume that someone must know a way around this problem.  I would be happy to know it, but much happier to see the Octave documentation address it directly.

I second this, it's not clear how to make the axis-numbering readable in this code:
```

plot(1:50);
xlabel('Time (1969=t_0)', 'FontSize', 100);
print -deps -color -F:64 population_k0.eps 

```
Neither FontSize, nor -F:64 seems to result in any change to the font size.

---

### Post by UChris on 2010-11-25
Some discussion on the help-octave mailing list suggests trying:
```
set(gca, 'fontsize', size)
```
This will not fix legend sizing, but will fix the axis sizing.  (This tip from "MA")

The same sizing problem also affects image annotations made using the text() command.  The set() solution above does not fix text() annotation. If using the text() command, you can use LaTeX sizing commands to control font size.  This appears to work in conjunction with the print() command.  For example:
```
text(-2, -2, '{\fontsize{16} 0.6175}')
```
This produces text with a size of 16pt.

---

