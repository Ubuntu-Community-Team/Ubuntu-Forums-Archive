---
title: "Averaging values from a large data file for plotting"
date: 2010-09-25
forum: Education &amp; Science
---

### Post by nandugopan on 2010-09-25
I have run into an issue while sorting data files. I know this may not be the best forum to post this, but this has been the place from which I have got the best advice.Hope my luck continues..:P
 
My problem is that I have a very large data file consisting of two columns of data (over 30000 entries). The data is unsorted and the file format looks like this:

A         B
1         2.56  
55        56.32
33        6.33 
674       -88.34
2         -53.898
5         9.765
...       ....


 I need to find average of values in column B for a particular range in column A. That is if I have to find the average of values from 1 to 5 (assuming there are only 3 entries 1,2 and 5 in the range 1 to 5), I should get the average of 2.56,-53.898 and 9.765 (as column B) printed to a new file along with the average of 1,2 and 5 (as column A). I need to do this for the entire range of data in A. The idea is to have a single output file that will have two columns of averaged values. 

Any help or suggestions as to how to do this using scripts or any open source software will be greatly appreciated. I need to repeat this procedure for 200 or so files, so spreadsheets does not look like an option.

Thanks in advance!:)

---

### Post by euler_fan on 2010-09-25
What are your dependent and independent variables? Is you average over fixed intervals or moving intervals (e.g. over Dependant indices 1-5 then 5-10 or 1-5 then 2-6?)? R can handle such tasks with relative ease. I'm sure python or perl could too and those might make more sense if you're doing this for batches of files, but I defer to the forum on this point as I am an R user and not fluent in python or perl.

Until your averaging scheme is well defined then any sort of batch script is not meaningful.

---

### Post by gunksta on 2010-09-25
I have a funny feeling that worrying about dependent v independent variables may be a little off-base here. This sorta sounds like a homework assignment from an intro-level CS class.

But, I've been wrong before.

euler_fan is right -  This could be easily implemented in any programming language. Something like C would make you jump through a few more hoops, but it's not exactly hard. Python and Perl could do it really easily. Some of Perl's data structures would work well here. You could even do this, easily, in a database system.

R would work too although it feels a little over-kill (albeit less so than C).

Do it in a database like SQLite where you can then turn it in both the data and the resultant answer as a single file. If this is a homework assignment, I'm not going to say anymore. If it's someone trying to learn how to program or something independently, I'll offer some syntax. I'll trust the OP to be honest (combined with a little gut-listening).

---

### Post by nandugopan on 2010-09-26
@euler_fan: Thanks for the tips. I have been trying to do this with perl. Any idea as to how to take average of a set of columns in perl and then output that average to a new file. The averaging is to be performed for fixed indices. This is essentially to average atomic velocities at fixed spatial positions. The variation is assumed to be one-dimensional, so one column of values are sufficient for denoting position. I need to average out the velocity over a fixed range, 1-5,5-10 and so on. 

@gunksta: Nope. This is not a homework assignment. This is for splitting and averaging velocities from a Molecular Dynamics simulation. Anyway, thanks for your insights.

---

### Post by gunksta on 2010-09-26
@nandugopan -- No hard feelings I hope. I wasn't trying to be rude, but I also don't want to do someone's homework for them.

I don't know if you have ever used R. It's a lovely program and if you continue to do things like this, it might be very helpful. Using R to calculate just a series of averages -- ain't necessary. Perl can certainly do that, although I don't do much in Perl. If you get some Perl code working, I'd love to see if so I can get a better sense of how to use Perl.

Attached you will find a .R file. If you run this syntax (bit by bit) in the interactive R terminal, you will learn a little bit about R syntax and get some code that is probably similar to what you need to do (I think).

I documented the syntax and developed it step by step, rather than just blindly hand you some obfuscated line of nonsense. But, it's also nearly time for me to crash for the night. If something doesn't make sense, just ask me for clarification and I'll see what I can do.

The syntax creates a dummy data set, finds some averages, and then saves these averages to a file called foo.csv. I think this is more or less what you are looking for, although I certainly don't understand your application (I am just a lowly social scientist).

---

### Post by nandugopan on 2010-09-27
@gunksta: No. I didn't take it as a rude comment. Just wanted things to be clear.A friend of mine came up with a python code.The script works decently.

#Python Averaging script#
import sys

inFile = sys.argv[1]
outFile = inFile+'_processed'
delimiter = '\t'
outputDelimiter = '\t'
avgRange = 2

def comp(a,b):
    return cmp(a[1], b[1])

f = open(inFile, 'r')
data_list = [[float(item) for item in line.strip().split(delimiter)] for line in f]
data_list.sort(comp)

f.close()

w = open(outFile, 'w')
i = 0
k = 0
a1 = 0
a2 = 0
for j in data_list:
    if (int(data_list[0][1])+(avgRange*i)) <= j[1] <= (int(data_list[0][1])+(avgRange*(i+1))):
        k = k+1
        a1 += j[1]
        a2 += j[2]
    else:
        w.write(str(a1/k)+outputDelimiter+str(a2/k)+'\n')
        a1 = 0
        a2 = 0
        k = 0
        i = i+1
w.close()

I work in molecular dynamics simulations. It involves a lot of statistical methods, so R looks really promising. You should consider writing an intro to R.:P The documented syntax that you sent works like a charm. Thanks for your time and effort.

---

### Post by radioboy on 2010-10-08
The Numpy library for Python could also be a good option for this kind of stuff. :D
You would just open the file as: file = numpy.loadtxt('file.dat',sep=delimiter) and 
get the two columns of your first example as A=file[:,0] and B=file[:,1].

Check this:
[http://www.scipy.org/Numpy_Example_List_With_Doc]("http://www.scipy.org/Numpy_Example_List_With_Doc")
Scipy, Matplotlib and ipython are good tools too, and if you need a GUI, Spyder:
[http://code.google.com/p/spyderlib/]("http://code.google.com/p/spyderlib/")
(Useful to test the scripts, examine values of arrays after execution, etc)

---

### Post by nandugopan on 2011-08-11
Thank you radioboy. Those were some really cool tools. Now you have me confused as to which way to go.:P

---

### Post by tommpogg on 2011-08-13
Octave can perform the task too

---

