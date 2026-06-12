---
title: "Linear Equations graphing program"
date: 2010-11-22
forum: Education &amp; Science
---

### Post by bhoth on 2010-11-22
Hi All,

looking for a simple program that graphs linear equations.

I have already tried lybniz, extcalc, and qtiplot, but have not been able to figure out how to simply enter an equation like y=5x+1 and have it graph it.

Thanks!

---

### Post by frncz on 2010-11-23
I Qtiplot:


Right click on the top of the first column and choose
Fill column
choose
row number

Right click on top of second column
Choose 'set colum values '

Then in the open box, enter something like:

5*col("1")+6

Then Apply

Then close

highlight both columns by left clicking on the two top labels,


Then click on Plot on the top bar
select line

an now you have it. Easy peasey

Hope it helps

Mike

---

### Post by frncz on 2010-11-23
Actually

You can also click on the F(x) icon, enter an expression in the box, such as
34*x^2+12
choose the range for x, and the graph appears miraculously!

---

### Post by bhoth on 2010-11-23
How do I set the x and y ranges on the graph to -10 to 10 so the graph is easier to read and plot the points?

---

### Post by frncz on 2010-11-23
The box has the option to set the range for x. You can also edit the graph to edit the axes
Hope it works for you.

---

### Post by ubuntu27 on 2010-11-23
You can also try [Qalculate!]("http://qalculate.sourceforge.net/")
It is in the repositories.

If you are using Ubuntu (gnome), install [qalculate-gtk]("apt://qalculate-gtk")

```
sudo apt-get install qalculate-gtk
```

If you are using Kubuntu (KDE) install [qalculate-kde]("apt://qalculate-kde")

```
sudo apt-get install qalculate-kde
```


A guide on how to use Plotting with [Qalculate!]("http://qalculate.sourceforge.net/") can be found at:

[http://qalculate.sourceforge.net/gtk-manual/ar01s08.html](http://qalculate.sourceforge.net/gtk-manual/ar01s08.html)

Another guide:

[http://qalculate.sourceforge.net/gtk-manual/ar01s08.html](http://qalculate.sourceforge.net/gtk-manual/ar01s08.html)

---

### Post by fr4nko on 2010-11-24
Hi,

you can do it using GSL shell. It is very easy:

```
p = fxplot(|x| 4*x - 3, -5, 5)
```

to plot the equation y = 4*x-3 for x going from -5 to 5. Then, if you want to add a second line in blue instead of red you can give:

```
p:addline(fxline(|x| 3*x + 2, -5, 5), "blue")
```

You can also plot inequalities like y > 4*x - 3. To do it, as an examples:

```
f = |x| 4*x - 3
ln = fxline(f, -5, 5)
area = fxline(f, -5, 5)
area:line_to(5, f(5))
area:line_to(-5, f(5))
area:close()

p = plot('y > 4*x - 3')
p:add(area, rgba(0,0,1,0.4))
p:addline(ln, "blue")
p:show()
```

GSL shell it is a software that I've developed, I've just released the 1.0-beta2. It is quite mature and interesting (at least, I think). The documentation page is:

[http://www.nongnu.org/gsl-shell/](http://www.nongnu.org/gsl-shell/)

and the project page at savannah is:

[http://savannah.nongnu.org/projects/gsl-shell/](http://savannah.nongnu.org/projects/gsl-shell/)

You can easily compile the program by installing the packeges libagg-dev and libgsl-dev.

Best regards,
Francesco

---

### Post by mionescu on 2010-11-27
In Octave:
x=-10:0.1:10;
y=5*x-1;
plot(x,y);

Wxmaxima it has a graphical tool to help you plot all kind of functions.

---

