---
title: "Favourite plotting software"
date: 2007-05-05
forum: Education &amp; Science
---

### Post by pillu on 2007-05-05
Hi all,

I am looking for a software which can do professional quality plots from my data sets. I am tired of the hideous looking plots that I get from MATLAB. Mathematica plots though slightly better, look nowhere close to those printed in journals. I am just being nitpicky here because I want my plots to have an aesthetic value to them.

I was looking at GLE ([http://glx.sourceforge.net/index.html]("http://glx.sourceforge.net/index.html")). Does anyone have any experience with this? If there is anything else that you use, I would love to give it a try as well

Cheers
pillu

---

### Post by tgalati4 on 2007-05-06
I've been using gnuplot since 1985 and it hasn't changed much.  It's not easy to use, but if you climb the learning curve it can do some pretty nifty things.  It can output to several formats and it's close to journal quality.

---

### Post by ahmatti on 2007-05-07
> **pillu said:**
> Hi all,

I am looking for a software which can do professional quality plots from my data sets. I am tired of the hideous looking plots that I get from MATLAB. Mathematica plots though slightly better, look nowhere close to those printed in journals. I am just being nitpicky here because I want my plots to have an aesthetic value to them.

I was looking at GLE ([http://glx.sourceforge.net/index.html]("http://glx.sourceforge.net/index.html")). Does anyone have any experience with this? If there is anything else that you use, I would love to give it a try as well

Cheers
pillu

Are you serious about the Matlab plots!? Which version are you using? I use Matlab for all of my publications and I haven't yet (unfortunately) found an opensource application that can produce the same quality. Honestly, I think that the Matlab output is better than the GLE link that you posted... Not to mention the possibility to set the resolution, figure size and wide range of formats...

I agree that it is possible to get quite good quality with gnuplot. I also find that R has nice plotting capabilities. Also matplotlib with python looks nice, but I have no exprience from using that one.

---

### Post by WW on 2007-05-07
My initial reaction was similar to ahmatti's.  Matlab has worked for me (but maybe I'm not as demanding?).   If I use a script to choose appropriate font sizes, linewidths, axis sizes, etc, and output as Encapsulated Postscript (.eps), the plots look pretty good to me.  Since "hideous looking" is relative, could you give an example of a "hideous looking plot"?

---

### Post by pillu on 2007-05-07
I think MATLAB does a bad job when plotting on log-log scale especially with the grid lines on (How do I make the grid lines solid instead of dotted!!). But you are right, hideous is a relative term. Also the default font is too thin and looks bad when compared to any TeX font. All this might just be my fault as I might not have explored all the options available in MATLAB (I will try to tinker around with all the graph options).  I was just looking at alternative options out there. I have a very limited experience with gnuplot but will give it a try again. Thanks for all the help

---

### Post by tgalati4 on 2007-05-07
Do a google search for gnuplot scripts.  There are several out there from smart folks.  You just have to take one and modify it to work with your data.  Gnuplot is definitely old school.

---

### Post by WW on 2007-05-07
Some useful GNUPlot tips are here: [http://t16web.lanl.gov/Kawano/gnuplot/index-e.html](http://t16web.lanl.gov/Kawano/gnuplot/index-e.html)

---

### Post by pillu on 2007-05-07
thanks for the help guys. I will check gnuplot out....

though I think the examples on the link above look just like MATLAB...probably no point in reinventing the wheel by learning another plotting software

pillu

---

### Post by tkjacobsen on 2007-05-08
I think scipy with matplotlib make really nice plots. You can also use TeX code in title/axis/annotations

[http://matplotlib.sourceforge.net](http://matplotlib.sourceforge.net)
[http://www.scipy.org/Cookbook/Matplotlib](http://www.scipy.org/Cookbook/Matplotlib)

It requires a little python skills, but not much if you are used to matlab.

---

### Post by pillu on 2007-05-08
> **tkjacobsen said:**
> I think scipy with matplotlib make really nice plots. You can also use TeX code in title/axis/annotations

[http://matplotlib.sourceforge.net](http://matplotlib.sourceforge.net)
[http://www.scipy.org/Cookbook/Matplotlib](http://www.scipy.org/Cookbook/Matplotlib)

It requires a little python skills, but not much if you are used to matlab.

Wow...scipy seems really cool...I don't have MATLAB on my home computer and octave really is not the same thing...I will give this a try...thanks

---

### Post by Eric_T on 2007-05-09
May I suggest the LaPrint script for Matlab: 
[http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file](http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file)
It converts your Matlab plot to an eps-file with all the numbers and text replaced by psfrags elements, and a tex-file which contains all the actual data.
That means that this will be passed through your latex compiler, and you will get the same font and size as in the rest of your document. That way you get a very consistent looking article. You can also edit the labels and ticks after you've saved the plot. I've used it for several of my publications. Nowadays I mostly use Tecplot for my plotting, since it's more flexible. However, I still use "tricks" to get labels and such passed through the latex compiler.

---

### Post by ahmatti on 2007-05-09
> **pillu said:**
> I think MATLAB does a bad job when plotting on log-log scale especially with the grid lines on (How do I make the grid lines solid instead of dotted!!). But you are right, hideous is a relative term. Also the default font is too thin and looks bad when compared to any TeX font. All this might just be my fault as I might not have explored all the options available in MATLAB (I will try to tinker around with all the graph options).  I was just looking at alternative options out there. I have a very limited experience with gnuplot but will give it a try again. Thanks for all the help

Formatting the graphs has become much easier in Matlab since version 7, I really recommend exploring the options. I really like matlabs "export setup" feature, where you can set the resolution, figure size, fonts, line widths etc. for the whole figure :) And you can save the options too, I have saved the settings for different journals for fast access...

There also an option in Matlab to use latex interpreter for the text in figures that you may want to try!

As for the grid lines: Right click axis -> choose "Show propery editor" -> from property editor choose "More properties" -> Look for "Gridlinestyle". Or do it from the command line (see matlab help).

---

### Post by ahmatti on 2007-05-09
> **Eric_T said:**
> May I suggest the LaPrint script for Matlab: 
[http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file](http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file)
It converts your Matlab plot to an eps-file with all the numbers and text replaced by psfrags elements, and a tex-file which contains all the actual data.
That means that this will be passed through your latex compiler, and you will get the same font and size as in the rest of your document. That way you get a very consistent looking article. You can also edit the labels and ticks after you've saved the plot. I've used it for several of my publications. Nowadays I mostly use Tecplot for my plotting, since it's more flexible. However, I still use "tricks" to get labels and such passed through the latex compiler.

Thanks for the tip :) ! This makes Matlabs output even better... I don't think (?) there is an option in Matlab to use Latex formatting for tick numbers... Otherwise Matlabs latex interpreter does the same thing.

---

### Post by pillu on 2007-05-10
> **Eric_T said:**
> May I suggest the LaPrint script for Matlab: 
[http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file](http://www.mathworks.com/matlabcentral/fileexchange/loadFile.do?objectId=4638&objectType=file)
It converts your Matlab plot to an eps-file with all the numbers and text replaced by psfrags elements, and a tex-file which contains all the actual data.
That means that this will be passed through your latex compiler, and you will get the same font and size as in the rest of your document. That way you get a very consistent looking article. You can also edit the labels and ticks after you've saved the plot. I've used it for several of my publications. Nowadays I mostly use Tecplot for my plotting, since it's more flexible. However, I still use "tricks" to get labels and such passed through the latex compiler.

Thanks Eric...LaPrint looks very good....now I have got one more thing to tinker around with...Yay!!

pillu

---

