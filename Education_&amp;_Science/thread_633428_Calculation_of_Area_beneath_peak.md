---
title: "Calculation of Area beneath peak"
date: 2007-12-06
forum: Education &amp; Science
---

### Post by disabled_20220313 on 2007-12-06
Evening,

I am trying to find a linux program that will calculate the area beneath a curve for me.

I have a set of data (electrochemical reaction of Au and Pt), and it makes a very nice graph with lots of curves.

I need to find the area beneath the curves to obtain some physical information about the electrode.

But I can't seem to find an easy solution. I have tried looking at Octave and Scilab, and they seem very technical and dont have a "intergrate (data)" command I could use.

Has anyone else had this problem and how did you solve it?

Cheers,

Ciarán 

Ps. The alternative written in the lab manual is to cut out the graphs from pieces of paper and weigh them. I'm far to lazy and cack-handed to that!

---

### Post by Blutack on 2007-12-06
Have you tried wxmaxima?
Import your data and then use the integrate command.

Otherwise you could try qtiplot, which I'm fairly sure has that functionality.

---

### Post by Whiffle on 2007-12-06
here's an octave script...

```


% Function homer was written by E343 Section 01 on 09/26/07
% Last revised on 09/26/07
%
% Function homer uses Simpson's First Rule to compute the area
% under a curve defines by the ordinates y1,y2,..., yn
% Usage: area = homer(y,s)
%
% Inputs:
% y is the vector of ordinates of the curve being integrated and must
% have an odd number of elements greater than or equal to three
% 
% s is the spacing between ordinates, and must equal
%
n =length(y);
if (n > 2 && mod(n,2) = 1)
	# write program statements here
	sum = y(1) + y(n);
	for i = 2:(n-1)
		if mod(i,2) = 0
			sum = sum +4*y(i);
		else
			sum = sum + 2*y(i);
		endif
	endfor
	retval = s*sum/3;
else
	printf("ERROR: The number of ordinates must be odd and at least 3\n");
endif

endfunction

```

[http://maritime-engineers.com/E343_F07/E343_01_09262007.txt](http://maritime-engineers.com/E343_F07/E343_01_09262007.txt)

---

### Post by subs on 2007-12-07
matlab would be perfect 4 u!!!

---

### Post by disabled_20220313 on 2007-12-07
Matlab is not Free software. 

Octave seems just as capable for my applications.

Thanks Whiffle, how do I input that into Octave?? Can i save it as a file and get octave to run it along the lines of 

octave intergratescript.txt for (x,y)

??

---

### Post by disabled_20220313 on 2007-12-07
Hey Wiffle,

I have tried using your script but it doesnt seem to be compaitable with my version on Octave. I keep getting an error.

```

error: invalid lvalue function called in expression
error: evaluating assignment expression near line 16, column 23
error: if: error evaluating conditional expression
error: evaluating if command near line 16, column 1
error: called from `homer' in file `/home/ciaran/homer.m'

```

I'm using Octave 2.1.73

---

### Post by artesian_spring on 2007-12-07
I think the problem (at least one of them) is that one of the comment lines (the one that says "# write program statements here") starts with a "#" when it should start with a "%." I recommend opening the homer.m file in gedit, turning on syntax highlighting for octave (view->highlight mode->[scripts OR scientific]->octave) and seeing if anything else looks amiss.

If you have a lot of analyses of this sort to do, I'd really recommend learning octave. Here's a link <www-mdp.eng.cam.ac.uk/CD/engapps/octave/octavetut.pdf>  to a tutorial from Cambridge University; resources for MATLAB are useful, too, as the syntax is very similar.

---

### Post by artesian_spring on 2007-12-07
I took a closer look at the code and realized that there was something important missing. Add the following to the beginning of homer.m:

```
function retval=homer(y,s)
```

Also, tests for equality should have a double-instead of single-equals sign ("=="); they apparently should also have parentheses around them. 

I made these changes and got the following (correct) results:

```
octave:6> y=[0 1 2 3 4 5 6];
octave:7> s=1;
octave:8> area=homer(y,s)
area = 18
```

Finally, here is the working homer.m file that I used:

```

function retval=homer(y,s)

% Function homer was written by E343 Section 01 on 09/26/07
% Last revised on 09/26/07
%
% Function homer uses Simpson's First Rule to compute the area
% under a curve defines by the ordinates y1,y2,..., yn
% Usage: area = homer(y,s)
%
% Inputs:
% y is the vector of ordinates of the curve being integrated and must
% have an odd number of elements greater than or equal to three
% 
% s is the spacing between ordinates, and must equal
%
n=length(y);
if (n > 2 && mod(n,2) == 1)
	% write program statements here
	sum=y(1) + y(n);
	for i=2:(n-1)
		if (mod(i,2) == 0)
			sum = sum +4*y(i);
		else
			sum = sum + 2*y(i);
		endif
	endfor
	retval = s*sum/3;
else
	printf("ERROR: The number of ordinates must be odd and at least 3\n");
endif

endfunction
```

Hope this helps.

---

### Post by disabled_20220313 on 2007-12-08
Ah Brilliant.

I'm quite surprised that they havnt integrated this kind of calculation into octave itself.

I think there is a school of thought that its better to "roll your own" in the octave / maths world. Which is great, but beyond my capabilities.

I have started using the traps(x,y) command, and it seems to give me values that are accurate enough, but more accuracy can't do any harm.

Cheers,

Ciarán

---

### Post by engla on 2007-12-09
> **ciaran.mooney said:**
> Ah Brilliant.

I'm quite surprised that they havnt integrated this kind of calculation into octave itself.

I think there is a school of thought that its better to "roll your own" in the octave / maths world. Which is great, but beyond my capabilities.

I have started using the traps(x,y) command, and it seems to give me values that are accurate enough, but more accuracy can't do any harm.

Cheers,

Ciarán
Um, you seem to have realized this but at the same time not, *trapz* is really the function you were asking for.

Also if you want an even simpler method ("square block" integration instead of trapezoidal) simply take the sum of your array times the data point separation :)

```
A= sum(f)*dx
```

---

### Post by Lux Perpetua on 2007-12-09
The trapezoid rule is not much more complicated: ```
(sum(f) - (f(1) - f(end))/2)*dx
```

---

### Post by engla on 2007-12-09
actually, my suggestion for trapezoid would be
```
end = length(f)-1
trapz = sum(f(1:end) + diff(f)*0.5)*dx
```
diff(f) is a vector 1 shorter than its argument, with the differences of each sucessive pair of elements in f. And it's correct that the square integral is not sum(f) but sum(f(1:end)) (you skip the last data point)

And, I would like to add, this is not "rolling your own", but some understanding behind what you want to do. Scientists have to know a bit of mathematics; often it's very simple things, you just have to sit down and think about it (this process is something you lear I've found out. I always want to just know everything without working for it, but boringly it's not that simple)

---

