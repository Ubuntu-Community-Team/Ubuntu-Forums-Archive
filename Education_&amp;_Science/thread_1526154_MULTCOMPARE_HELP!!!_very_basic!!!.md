---
title: "MULTCOMPARE HELP!!! very basic!!!"
date: 2010-07-07
forum: Education &amp; Science
---

### Post by Megg22 on 2010-07-07
Hi,
 
Im new to MatLab (first day!!!) and am trying to use the Multcompare command. This is probably a really basic question but I cant figure it out and its bugging me!!
 
My data set is basically a 38X12 matrix of numbers with no headings etc. 
The rows are 38 countries and the cols are months.
I couldnt figure out how to name the variables as their countries so I did:
Ireland =data(1,;)
England =data(2,;)
etc. 
This worked fine.
 
I basically want to compare every country in my dataset to each other.The multcompare command seemed ideal but I cant work it. 
 
Syntax=
[c,m,h] = multcompare(stats)
 
How do I compute a 'stats' structure with my data?I got "Undefined function or variable 'stats'." when I tried the command above.
When I tried
[c,m,h]=multcompare(Ireland,England), I got 
"??? Error using ==> multcompare at 138
STATS must be a structure."
 
I can see from the example given:
[p,t,st] = anova1(MPG,Origin,'off');
[c,m,h,nms] = multcompare(st,'display','off');
[nms num2cell(m)]
ans = 
'USA' [21.1328] [0.8814]
'Japan' [31.8000] [1.8206]
'Germany' [28.4444] [2.3504]
'France' [23.6667] [4.0711]
'Sweden' [22.5000] [4.9860]
'Italy' [28.0000] [7.0513]
 
that you can do it using anova1 etc but that data seems to be in a different format. 
 
I want results like they got, for all the combinations of my countires.
 
Can anyone help me???
 
Thanks in advance,
 
Meg

---

### Post by nick_goodfate on 2010-07-07
> I basically want to compare every country in my dataset to each other.

can you explain how you want to compare them ?
you may can do it with for-loops ....

EDIT: from what i read , multcompare takes a struct as argument, you tried to give two arrays (Ireland,England) ...

---

### Post by Megg22 on 2010-07-07
Thanks so much for replying. 
 
I basically want to do difference between the mean tests and from what I can see from the multcompare help this function will do it. The explanation going with the syntax I gave below is:
"The output c contains the results of the test in the form of a five-column matrix. Each row of the matrix represents one test, and there is one row for each pair of groups. The entries in the row indicate the means being compared, the estimated difference in means, and a confidence interval for the difference. 
For example, suppose one row contains the following entries.
2.0000  5.0000  1.9442  8.2206  14.4971
These numbers indicate that the mean of group 2 minus the mean of group 5 is estimated to be 8.2206, and a 95% confidence interval for the true mean is [1.9442, 14.4971].
In this example the confidence interval does not contain 0.0, so the difference is significant at the 0.05 level. If the confidence interval did contain 0.0, the difference would not be significant at the 0.05 level."
 
This is exactly what I want to do. 
 
Im really sorry but I dont understand what you mean by 'array' . I really am just starting out!!

---

### Post by nick_goodfate on 2010-07-07
the c in form of 5 columns is what you want as output. in what form are the data you have and you want to process? i want to give me two or three examples of the data you have and two or three examples of the data you want to have after as output, and i ll try to understand :). the answer you took from matlab community was not what you wanted ?

EDIT : by array i mean for example this [2 3 4 5] .

---

### Post by Megg22 on 2010-07-07
ok so my data is a 38X12 speadsheet.
rows - countries, cols= months
example:
[FONT=Calibri]12[/FONT][FONT=Calibri]13[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]19[/FONT][FONT=Calibri]17[/FONT][FONT=Calibri]18[/FONT][FONT=Calibri]15[/FONT][FONT=Calibri]16[/FONT][FONT=Calibri]16[/FONT][FONT=Calibri]45[/FONT][FONT=Calibri]36[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]13[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]19[/FONT][FONT=Calibri]17[/FONT][FONT=Calibri]18[/FONT][FONT=Calibri]15[/FONT][FONT=Calibri]67[/FONT][FONT=Calibri]27[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]13[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]19[/FONT][FONT=Calibri]17[/FONT][FONT=Calibri]18[/FONT][FONT=Calibri]15[/FONT][FONT=Calibri]89[/FONT][FONT=Calibri]37[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]13[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]19[/FONT][FONT=Calibri]17[/FONT][FONT=Calibri]18[/FONT][FONT=Calibri]15[/FONT]
 here is the forst four lines.
 
as my data wasnt named, I used:
Ireland =data(1,;)
(as above [FONT=Calibri]12[/FONT][FONT=Calibri]13[/FONT][FONT=Calibri]12[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]14[/FONT][FONT=Calibri]19[/FONT][FONT=Calibri]17[/FONT][FONT=Calibri]18[/FONT][FONT=Calibri]15[/FONT][FONT=Calibri]16[/FONT][FONT=Calibri]16[/FONT])
England =data(2,;)
etc, to name the countries. 
So I now have a 38x12 matrix in the workspace called data, and 38 (1X12) matrices for all the individual countries.
 
It is these countries I want to compare (or all the rows of the 'data' matrix). 
 
The output from the matlab community is exactly what i mean but i cant understand how to get it. 
 
So basically as in their output:
2.0000 5.0000 1.9442 8.2206 14.4971
These numbers indicate that the mean of group 2 minus the mean of group 5 is estimated to be 8.2206, and a 95% confidence interval for the true mean is [1.9442, 14.4971].
Id like something like:
Ireland England 1.9442 8.2206 14.4971
or 
row1 row2 1.9442 8.2206 14.4971

and the same for all my countries. 
 
Hope I have explained myself ok. Thanks a lot for your help!:p

---

### Post by Megg22 on 2010-07-07
that first exampple came out really badly:
first four lines of my matrix:
[1 4 6 3 8 5 7 3 10 14 16 5
 3 8 5 7 3 10 14 16 5  3   7
 5 7 3 10 14 16  5   5  8   9
 1 4 6 3 8 5 7 3 10  2  6  9]

---

### Post by nick_goodfate on 2010-07-07
> The output from the matlab community is exactly what i mean
Excellent !
they give you this :
> clear all;
close all;
clc;
for j=1:38, c{j} = sprintf('c%d',j); end
c{1} = 'Ireland'; c{2} = 'England';
x = randn(38,12);
[p,tbl,st] = anova1(x',c);
multcompare(st);

in line > c{1} = 'Ireland'; c{2} = 'England'; continue to name your countries, > c{1} = 'Ireland'; c{2} = 'England'; c{3} = 'India'; ... c{38} = Greece;

Matrix x, in your case is your 38X12 speadsheet. so in line > [p,tbl,st] = anova1(x',c); replace x' with the name of your 38X12 matrix.

---

### Post by Megg22 on 2010-07-07
THANK YOU SO MUCH!!!!
 
Its 12.10 am and I  got kicked out of my office at work 30 mins so I will try it first thing in the morning. 
 
so basically i copy exactly this:
clear all;
close all;
clc;
for j=1:38, c{j} = sprintf('c%d',j); end
c{1} = 'Ireland'; c{2} = 'England';
x = randn(38,12);
[p,tbl,st] = anova1(x',c);
multcompare(st); 
 
making all the adjustments you said????
 
I cant thank you enough-you saved me days!!
 
Would you mind if i got back to you tmw if i have any other questions? Do i just reply to this thread again and you will be alerted? 
 
Im new to this forum as well as matlab!

---

### Post by nick_goodfate on 2010-07-07
I hope it eventually do what you want! yes make those adjustments and let me know if it is what you wanted . if you post something in this thread i ll be alerted yes , and i ll do my best to help you :D

---

### Post by nick_goodfate on 2010-07-07
replacing " x' " in line " [p,tbl,st] = anova1(x',c); " , dont forget " ' " after the name of your matrix ...

EDIT: and one last adjustment i forgot ! delete the whole line " x = randn(38,12); " , its useless for you . they used it cause they didnt had the 38X12 matrix that you have, so they created a random one with this expression ...

---

### Post by Megg22 on 2010-07-08
IT WORKED!!!!
 
thanks a lot, i really appreciate your help, you saved me a lot of work. 
apologies if i confused you explaining, at least we go tthere!

---

### Post by nick_goodfate on 2010-07-08
> **Megg22 said:**
> IT WORKED!!!!
 
thanks a lot, i really appreciate your help, you saved me a lot of work. 
apologies if i confused you explaining, at least we go tthere!

glad to know i helped somehow:) No need for apologies , as you said the point is we get there even though it wasnt too far :P

---

