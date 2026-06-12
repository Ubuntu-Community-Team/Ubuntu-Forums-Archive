---
title: "octave or other matlab alternatives"
date: 2008-04-23
forum: Education &amp; Science
---

### Post by garfieldpbj on 2008-04-23
Hi.

I've been running octave for some months - now I searched the web, and found that there are other alternatives to this program - but which is best? (of course it should be free :-) ) 

And how do I "tune" octave the best way - especially what I think is bad is the plotting possibilities I have - I use gnuplot which I think is standard, but I know there are other programs to make octave use - which is  best? 

I do also think that GNUPLOT is very slow (when I want to plot a list of 10 millions of numbers, which I know is a lot, but it takes several minutes to plot - I've "only got a 1,7 ghz celeron and 2gb memory - but I do still think it is bad!).

Can anybody help me?

/Peter

---

### Post by thisismalhotra on 2008-04-23
Your options are SCILAB, MAXIMA from my knowledge, but I use octave all the time, I dont know why your are having issues with it.

One thing though the way you write you code also decides how fast it is executed and handles are passed to a plotting program. Second thing if you are using Octave 2.x, those are old versions and you should shift to Octave 3.0 which handles graphics much much better.

Here is my post from where you can get a deb for Octave 3.0

[http://ubuntuforums.org/showthread.php?t=713880](http://ubuntuforums.org/showthread.php?t=713880)

I use to do non - vectorized code all the time, but I tell once I figured out how to vectorize stuff boy it made the world change for me.

If you can specifically tell me what issues you are having we may try to fix it. Also plotting 10 million points in several minutes(you did not say how many) is good considering you have a celeron chip. 

Another good place to check is octave forums :)

Thats all I can say now :)

HTH

---

### Post by garfieldpbj on 2008-04-23
Thank you for your answer..

I have version 2.9.something - so I'll try to upgrade..

I do not execute any code - the only thing I do is reading a .txt file with 10 millions lines - with one number pr. line. When I plot these numbers.. (it takes about 3 minutes..)

Where do I find some octave forums? (I can not find information about it at octave's homepage)...

/Peter

---

### Post by garfieldpbj on 2008-04-23
Hi... I forgot one question: Should I use the gnuplot or some other plotting program?

/peter

---

### Post by garfieldpbj on 2008-04-23
I've now installed the package you linked to which should be ver. 3.0 - but I was told that I already had a newer ver. even though it was 2.9 - so I uninstalled 2.9 and installed 3.0 and now I get a reminder from update to update to ver. 2.9 - that's strange - can anyone explain this?

/Peter

---

### Post by xadder on 2008-04-24
I like matplotlib, in combination with ipython. The graphics is superb, and the combination with python is great for scripting. This has been my replacement for MATLAB.

---

### Post by vancheese on 2008-04-24
And don't forget sympy (in development) for symbolic maths stuff in conjuction with ipython, matplotlib and  numpy/scipy

---

### Post by thisismalhotra on 2008-04-24
> **garfieldpbj said:**
> Hi... I forgot one question: Should I use the gnuplot or some other plotting program?

/peter

I use gnuplot but an good alternate is easyplot

---

### Post by thisismalhotra on 2008-04-24
> **garfieldpbj said:**
> Thank you for your answer..

I have version 2.9.something - so I'll try to upgrade..

I do not execute any code - the only thing I do is reading a .txt file with 10 millions lines - with one number pr. line. When I plot these numbers.. (it takes about 3 minutes..)

Where do I find some octave forums? (I can not find information about it at octave's homepage)...

/Peter

That might be your slowness right there. Are you reading the file as you are executing/plotting. I would just read the file once into a matrix/vector and than plot the vector. Should be much faster??

---

### Post by thisismalhotra on 2008-04-24
> **garfieldpbj said:**
> I've now installed the package you linked to which should be ver. 3.0 - but I was told that I already had a newer ver. even though it was 2.9 - so I uninstalled 2.9 and installed 3.0 and now I get a reminder from update to update to ver. 2.9 - that's strange - can anyone explain this?

/Peter

Thats is perfectly normal. See ubuntu stores software version in channels/repositories. By default the OS assumes that the version in repos are the latest versions. Ubuntu 7.10 repos were made in October 2007 whereas Octave 3.0 came out in December 2007. So we dont have lates octave in ubuntu 7.10 repos. You will have to bear with this error as when I made this .deb my knowledge of .deb making process was limited.

Alternatively you can upgrade to latest version of Ubuntu which is 8.04. coming out today(surprise LOL).. but that would be going far... hehe :popcorn:

---

### Post by thisismalhotra on 2008-04-24
> **garfieldpbj said:**
> Thank you for your answer..

I have version 2.9.something - so I'll try to upgrade..

I do not execute any code - the only thing I do is reading a .txt file with 10 millions lines - with one number pr. line. When I plot these numbers.. (it takes about 3 minutes..)

Where do I find some octave forums? (I can not find information about it at octave's homepage)...

/Peter

Sorry I always say Octave forums but thats kinda misleading, GNU Octave only has mailing list but there is a web view of the mailing lists(thats is where I mix them up as webview looks just like a forum) where you can post questions. You will have to subscribe to mailing list to post question on the web version of it.

Here is a link to octave homepage and go to mailing list to subscribe.

[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

Here is the web view by Nabble

[http://www.nabble.com/Octave-f1895.html](http://www.nabble.com/Octave-f1895.html)

---

### Post by garfieldpbj on 2008-04-24
> **thisismalhotra said:**
> That might be your slowness right there. Are you reading the file as you are executing/plotting. I would just read the file once into a matrix/vector and thane+c_23-4_8_octavedump plot the vector. Should be much faster??

I do it this way:

load values.txt
plot(values)
title("title is this")

Isn't that the "correct way" to do it?

I do not understand the last thing you write (that is: thane+c_23-4_8_octavedump plot the vecto) can you explain this?

/peter

---

### Post by garfieldpbj on 2008-04-24
> **thisismalhotra said:**
> Thats is perfectly normal. See ubuntu stores software version in channels/repositories. By default the OS assumes that the version in repos are the latest versions. Ubuntu 7.10 repos were made in October 2007 whereas Octave 3.0 came out in December 2007. So we dont have lates octave in ubuntu 7.10 repos. You will have to bear with this error as when I made this .deb my knowledge of .deb making process was limited.

Alternatively you can upgrade to latest version of Ubuntu which is 8.04. coming out today(surprise LOL).. but that would be going far... hehe :popcorn:

So what would be the best to do? Install your 3.0 or the 2.9 ubuntu tells me to?

/Peter

---

### Post by ahmatti on 2008-04-25
I would go with the 3.0, it has significant improvements over 2.9. I had some issues with the 2.9 installed from the repos, although it was some time ago. Are you making a line plot or a surface plot? Surfaces take a lot more time and also reading a file that large also takes up some time. I can test to do something similar and see how long it takes.

If you don't need the compatibility with matlab I would also suggest checking out R ([www.r-project.org](www.r-project.org)). R is a statistical package, but it also does great with signals, neural networks, wavelets, simulations etc. I guess octave is suppose to be faster if you use a lot of matrices though. And the plotting capabilities in R are far better in my opinion (it also beats matlab in plotting).

---

### Post by thisismalhotra on 2008-04-25
> **garfieldpbj said:**
> I do it this way:

load values.txt
plot(values)
title("title is this")

Isn't that the "correct way" to do it?

I do not understand the last thing you write (that is: than dump plot the vecto) can you explain this?

/peter

LOL I dont know from where e+c_23-4_8_octave cme from but anyways what I meant was dump the whole file in a vector and than plot a vector.

Also, use 3.0 as the software channel thinks anything other that 2.9 is old :lolflag:

I don't have the code off the top of my head. It is very simple though but I will post that soon.

---

### Post by thisismalhotra on 2008-04-25
If your file is really big (10 mil lines) this is what I would do;

```
filename = "myfile.txt";
fid = fopen (filename, "r");
[A, count] = fscanf(fid, "%f");
plot(A); //Dont know how you are doing it here)
fclose (fid);
```

See if this is faster. Also you only have a decent processor(celeron) I would not expect things to lightning fast.

Note: text file have to be in the same directory as you code

HTH:)

---

### Post by krazyd on 2008-04-25
you really might like to check out sage: [http://www.sagemath.org/](http://www.sagemath.org/)

---

