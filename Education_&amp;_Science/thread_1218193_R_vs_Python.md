---
title: "R vs Python"
date: 2009-07-20
forum: Education &amp; Science
---

### Post by ahmatti on 2009-07-20
I've been using R now for about 2 years and do most my analysis using R and sometimes resort to Matlab. However I've always been curious about python+numpy+scipy+matplotlib (having seen it recommended also in this forum) and now I have also find the time to study it a bit.

At this point I got curious and tried google how it compares to R and found a lot of comparisons between Python and Matlab and some comparing R and Matlab, but not a really interesting comparison of R and Python. 

So if you know both R and Python, which do you prefer for your data analysis and why? Or if you don't know both, which one do you use and why do you like it :) 

e.g. I really like R's ability to mix different data types in the data frames, which something I haven't found from SciPy (but do tell me if it exists). On the other hand with Python I can create GUIs easily.

If you have no idea about either one and want to find out start from [www.r-project.org](www.r-project.org), [www.python.org](www.python.org) and [www.scipy.org](www.scipy.org)

BTW I am an agricultural engineer working with machine learning, classifiers, signal processing and traditional statistics.

---

### Post by gunksta on 2009-07-20
I voted for R because I generally prefer R for data analysis but I use python from time to time.

I think the preference will be heavily dependent on the nature of the analysis / field of study. My data analysis is focused on the human services field. The ability to mix data types in a data frame is a key feature for most of the projects I work on. I suspect that engineers and scientists (in some fields) may not necessarily need this ability and python is arguably easier to learn and the skills can be applied to other projects beyond data analysis which could be a winning combination for many users.

I suspect you didn't find too many comparisons between the scipy/numpy feature set and R because the over-lap is genuinely minimal. R has the ability to do more advanced analysis for many fields (econometrics, etc). AFAIK, the scipy package is really more aimed at matlab users.

---

### Post by ahmatti on 2009-07-20
> **gunksta said:**
> 
I suspect that engineers and scientists (in some fields) may not necessarily need this ability and python is arguably easier to learn and the skills can be applied to other projects beyond data analysis which could be a winning combination for many users. 

Thanks for the input :) One the reason for posting this was to find out which are the fields that Python is more suitable for. I guess I find Python also a bit easier to learn, but R is not that difficult either if you have any coding experience. 

> **gunksta said:**
> 
I suspect you didn't find too many comparisons between the scipy/numpy feature set and R because the over-lap is genuinely minimal. R has the ability to do more advanced analysis for many fields (econometrics, etc). AFAIK, the scipy package is really more aimed at matlab users.

This is how I feel too and I find that R is often overlooked as an alternative to Matlab, because people think it is only limited to statistics. If you do purely matrix manipulations then I think that Matlab and Numpy have a bit nicer syntax for it, but then I have replaced practically all of my Matlab work with R and find R to be more productive.

Interestingly my recent work deals with wavelets and SVMs (I used R) and there is an interface for them in Python as well R. For SVMs they both even use the same C library libsvm [http://www.csie.ntu.edu.tw/~cjlin/libsvm/](http://www.csie.ntu.edu.tw/~cjlin/libsvm/).

Python voters let me hear your reasons, I really like Python too and would like to know what would be the best project to use it for.

---

### Post by unutbu on 2009-07-20
Could you explain what is meant by "The ability to mix data types in a data frame"?

---

### Post by ahmatti on 2009-07-20
> **unutbu said:**
> Could you explain what is meant by "The ability to mix data types in a data frame"?

Sure, glad you asked. It is always as easy to forget that others are not familiar with your favorite software.

This is from the R manuals:
*A data frame, a matrix-like structure whose columns may be of differing types (numeric, logical, factor and character and so on).*

Basically you can have columns of numeric data together with their labels that can be of several types (strings of factors) in the same structure. This makes the grouping and summarizing of data and statistical analysis very easy. Each column of a data frame also has a name so you don't have to remember the index for each data column.  

This is common feature in stats software and speadsheets, but Matlab doesn't have it and AFAIK Numpy doesn't either

---

### Post by unutbu on 2009-07-20
In numpy you can define "structured arrays":
```

#!/usr/bin/env python
import numpy as np

C0=[1,2]
C1=['a','b']
C2=[3.3,4.4]
x=np.array(zip(C0,C1,C2),dtype=[('day', '<i4'), ('title', '|S1'), ('value', '<f8')])
```

So x looks like this:
```

print(x)
# [(1, 'a', 3.2999999999999998) 
#  (2, 'b', 4.4000000000000004)]
```

The first "column" are 4-byte integers, the second are 1-byte strings, the third are 8-byte floats. (You can also use any Python object as a data type.)
 
You can access rows via integer indexing:
```

print(x[1])
# (2, 'b', 4.4000000000000004)
```

and the columns via string indexing:
```

print(x['day'])
# [1 2]
print(x['title'])
# ['a' 'b']
print(x['value'])
# [ 3.3  4.4]
```

Even after you slice by row, you can still access individual column values via string indexing:
```

for row in x:
    print('%s: On day %s we ate %s beans'%(row['title'],row['day'],row['value']))
# a: On day 1 we ate 3.3 beans
# b: On day 2 we ate 4.4 beans
```


PS. Ubuntu offers a package called python-rpy which provides python-bindings for R. So you can use R from within Python. I don't have any meaningful experience with this, however.

---

### Post by ahmatti on 2009-07-20
> **unutbu said:**
> In numpy you can define "structured arrays":


I didn't know that! Thanks a lot, thats exactly what I want, just couldn't find it from the docs :) 

I've also come across rpy when surfing on the web, but haven't used personally. Its a great idea, but if I make e.g a GUI application for some analysis in python and send it to a colleague it is nicer if I don't have R as a depency.

---

### Post by gunksta on 2009-07-20
The other nice thing about R is the ability to recognize factors. For example, if I have a dataframe with a structure such as:

NAME    GENDER (M/F)    Date of Birth    Height   Weight

R is "smart" enough to recognize that Gender only has two values M or F while the others have multiple values. Because R recognizes Gender as a factor variable, the syntax can be relatively simple to compare males to females by other variables such as weight or height.

---

### Post by unutbu on 2009-07-20
That's interesting, gunksta. I'm not sure if this is the same thing [1], but in numpy you can pick off those rows of data where gender is 'M' by using "fancy indexing":
[PHP]
#!/usr/bin/env python
import numpy as np

C0=[1,2,3]
C1=['M','F','M']
C2=[3.3,4.4,5.5]
x=np.array(zip(C0,C1,C2),dtype=[('day', '<i4'), ('gender', '|S1'), ('value', '<f8')])

print(x)
# [(1, 'M', 3.2999999999999998) (2, 'F', 4.4000000000000004) (3, 'M', 5.5)]

# "x['gender']=='M'" returns a boolean array, and we can feed that boolean array
# back into x[...] to select those rows where the boolean array is true.
# In numpy this is called "fancy indexing".
print(x[x['gender']=='M'])
# [(1, 'M', 3.2999999999999998) (3, 'M', 5.5)][/PHP]


[1] If I'm undestanding you correctly, R somehow analyzes the data and recognizes there are only two possible values for gender. Numpy does no such thing.

---

### Post by ahmatti on 2009-07-21
> **unutbu said:**
> 
If I'm undestanding you correctly, R somehow analyzes the data and recognizes there are only two possible values for gender. Numpy does no such thing.

Yes, if you convert a string to a factor then R knows what levels it has. For example:
```

> a <- c('male','female')
> a
[1] "male"   "female"
> factor(a)
[1] male   female
Levels: female male

``` 

Gunksta,  thanks for brinning up this feature. I really like it too! A small demonstration using the crabs dataset in library MASS *(# begins a comment in R code)*

```

#Load MASS library
> library(MASS)

#Show the first 6 rows from the dataframe "crabs"
#We see that it contains measurements from crabs of 2 different species sp (B or O) and sex (M or F)
> head(crabs)
  sp sex index   FL  RW   CL   CW  BD
1  B   M     1  8.1 6.7 16.1 19.0 7.0
2  B   M     2  8.8 7.7 18.1 20.8 7.4
3  B   M     3  9.2 7.8 19.0 22.4 7.7
4  B   M     4  9.6 7.9 20.1 23.1 8.2
5  B   M     5  9.8 8.0 20.3 23.0 8.2
6  B   M     6 10.8 9.0 23.0 26.5 9.8

# Now suppose we want to calculate the mean for each measure in the dataset
# grouped be sex and species. We can do this easily with the command

> aggregate(crabs[,4:8], list(crabs$sex,crabs$sp) , mean)
  Group.1 Group.2     FL     RW     CL     CW     BD
1       F       B 13.270 12.138 28.102 32.624 11.816
2       M       B 14.842 11.718 32.014 36.810 13.350
3       F       O 17.594 14.836 34.618 39.036 15.632
4       M       O 16.626 12.262 33.688 37.188 15.324
```


Also when reading in text files R tries to recognize the correct data type for each column, sometimes it does make a wrong guess and you need specify the correct option.

---

### Post by ahmatti on 2009-07-21
R is often blamed to have slow loops and is not therefore recommended for applications that require long loops. In interesting thread in the "Programming talk" - section gave a perfect opportunity to test it:

The thread has Python code that looks for the first 100 000 prime numbers in about 0.5 s on the authors computer and mine. I wrote the same code in R and it takes 15 s to accomplish the same task. *The Python solution for the specific task is therefore ~ 30 faster.*

Here is a link to the thread: [http://ubuntuforums.org/showthread.php?t=1215711](http://ubuntuforums.org/showthread.php?t=1215711) and my post with the R code [http://ubuntuforums.org/showpost.php?p=7647630&postcount=79](http://ubuntuforums.org/showpost.php?p=7647630&postcount=79).

I haven't found any need for this kind of loops in any of my practical work and anyway in my applications its the stuff inside of the loops that takes the majority of time. Often I can also vectorize the calculation which makes it considerably faster. Also a lot of R functions and add on packages are written in C and are therefore really fast. If you find a way to accelerate my R code in the above thread please post in that thread and I will link your solution here. 

However if you do need to write an application that requires long loops it seems you are much better of with Python. 

If you are interested in the ways of accelerating your R code have a look at the excellent doc R inferno [http://www.burns-stat.com/pages/Tutor/R_inferno.pdf](http://www.burns-stat.com/pages/Tutor/R_inferno.pdf)

---

### Post by unutbu on 2009-07-21
I am not an expert with numpy, so there might be an easier way than what I do below.
[php]
#!/usr/bin/env python
import numpy as np

def combinations(*lists):   
    '''
    http://www.mail-archive.com/numpy-discussion@scipy.org/msg05644.html
    '''
    lens = [len(l) for l in lists]
    for indices in np.ndindex(*lens):
        yield [l[i] for l, i in zip(lists, indices)]

def aggregate(group_data,value_data,groupby,func):
    groups=[np.unique(group_data[group]) for group in groupby]
    combos=[combo for combo in combinations(*groups)]
    result=np.zeros((len(combos),len(groupby)+value_data.shape[1])).astype(object)
    for idx,combo in enumerate(combos):
        cond=np.logical_and.reduce(
            [group_data[group]==c for group,c in zip(groupby,combo)])
        subdata=value_data[cond].astype(float)
        result[idx]=np.hstack((combo,func(subdata,axis=0)))
    return result

fh=open('crabs.out')
fields=fh.readline().split()
crab=np.array([tuple(line.split()[1:]) for line in fh],
              dtype=np.dtype([(field,'object') for field in fields]))
values=np.column_stack([crab[field] for field in fields[3:8]])
agg=aggregate(crab,values,['sex','sp'],np.average)
for row in agg:
    print(' '.join([str(elt).ljust(6) for elt in row]))[/php]

yields
```

F      B      13.27  12.138 28.102 32.624 11.816
F      O      17.594 14.836 34.618 39.036 15.632
M      B      14.842 11.718 32.014 36.81  13.35 
M      O      16.626 12.262 33.688 37.188 15.324
```


It appears R has some nice high-level functions that are probably missing from numpy/scipy. If you choose to use numpy/scipy, you may at times have to roll your own functions or use rpy.

You may also want to ask questions about Numpy on the numpy-discussion mailing list:
[http://mail.scipy.org/pipermail/numpy-discussion/](http://mail.scipy.org/pipermail/numpy-discussion/)
Those guys know a lot more about numpy than I do.

---

### Post by ahmatti on 2009-07-21
unutbu,
Many thanks for taking the time to write all of your code examples in this thread! It really makes the comparison of the two languages easier and I'm even more curious about Python than before.

I'll probably try to use it for the data analysis of my next paper, just learn it more. I think it is going to be useful to master Python even if I will probably stick with R as my main environment. I'll need to give Rpy a try as well.

---

### Post by gunksta on 2009-07-22
unutbu: How do you get syntax highlighting in your code snippets? My R syntax always comes out BLAH.

Sorry, not trying to hijack this thread.

---

### Post by gunksta on 2009-07-22
> **ahmatti said:**
> R is often blamed to have slow loops and is not therefore recommended for applications that require long loops. In interesting thread in the "Programming talk" - section gave a perfect opportunity to test it:

The thread has Python code that looks for the first 100 000 prime numbers in about 0.5 s on the authors computer and mine. I wrote the same code in R and it takes 15 s to accomplish the same task. *The Python solution for the specific task is therefore ~ 30 faster.*

Here is a link to the thread: [http://ubuntuforums.org/showthread.php?t=1215711](http://ubuntuforums.org/showthread.php?t=1215711) and my post with the R code [http://ubuntuforums.org/showpost.php?p=7647630&postcount=79](http://ubuntuforums.org/showpost.php?p=7647630&postcount=79).


I agree, that is definitely an interesting discussion but Python is NOT ~30x faster than R (at least not in this case). If you use loops, R will typically run slower than molasseses flowing up a hill. But, it is possible to vectorize the R code into something that will run a little faster. Python is still faster at this (although it's a terrible test for R) but my vectorized version runs much much faster than the looped version.

**EDIT:**  My original code for is.prime contained an error. It has been repaired in the current version of is.prime.

```

is.prime <- function(num){
  if (num==2) return(1) else {
    check <- 2:round(sqrt(num))
    min(num%%check)
  }
}
               
primes_in_range <- function(start, end){
  numbers <- start:end
  out <- lapply(numbers, is.prime)
  primes <- which(out==1)
  numbers[primes]
}
  

primes_in_range(0, 100000)

```

---

### Post by unutbu on 2009-07-22
gunksta, to get code highlighting: 

Select the code, then click the PHP button instead of the CODE (#) button.

The icon is the last one on the right. It looks like a little blue page with the word "php" written in the middle. (See attached).

Alternatively, you can write the [noparse][php]...[/php][/noparse] tags manually.

---

### Post by ahmatti on 2009-07-22
> **gunksta said:**
> I agree, that is definitely an interesting discussion but Python is NOT ~30x faster than R (at least not in this case). If you use loops, R will typically run slower than molasseses flowing up a hill. But, it is possible to vectorize the R code into something that will run a little faster. Python is still faster at this (although it's a terrible test for R) but my vectorized version runs much much faster than the looped version.


Thanks a lot for your vectorized version! It kind of proves the point I made earlier, but I couldn't think of a nice vectorized solution for this. Just shows that you can vectorize more often than you think and should always give it a try! Using your solution Python is about 13 faster than R on my PC. Makes me wonder though if there would a way to vectorize the code in Numpy to make the Python solution faster...

I'm going to repeat a point I made in the other thread too: Note though (well gunksta probably knows this, but maybe others don't) that lapply also has an internal loop, so it is not actual vectorization and can be in some cases even slower than a for loop. As the R inferno puts, *apply family functions are not loop-replacing, they are loop-hiding *(which is of course very convenient for saving human time even if they don't really save computer time). I tried replacing lapply in your with a loop and speed difference is about 0.2 s in favor of lapply this time.

Being a terrible test for R is maybe another way of saying that you don't want to use R if you have a task that requires a lot of loops. But yeah, I've never had the need of using this heavy loop in any practical data analysis task that I've done.

The time it takes to write the code is really more important for me, and this is something R usually really excels in. It also makes the code very readable when you have to go back to the analysis after some time :)

See gunksta's timing for the above code here: [http://ubuntuforums.org/showpost.php?p=7656417&postcount=99](http://ubuntuforums.org/showpost.php?p=7656417&postcount=99)

**EDIT:** I was able to speed up gunksta's code with a small change, Python is now ~8 faster. [http://ubuntuforums.org/showpost.php?p=7657150&postcount=100](http://ubuntuforums.org/showpost.php?p=7657150&postcount=100) Also my attempt to vectorize Python code using Numpy slowed it down about 20 x... 


P.S I'm really happy with the activity in this thread :)

P.P.S I'm actually on vacation and probably shouldn't sped my time playing with this stuff, but I can't help it :)

---

### Post by unutbu on 2009-07-22
ahmatti, for a nice example of a numpy implementation of the Sieve of Eratosthenes, 
check out [http://tommih.blogspot.com/2009/04/fast-prime-number-generator.html](http://tommih.blogspot.com/2009/04/fast-prime-number-generator.html)

Below I compare the numpy implementation (primes_ambi.py) with a plain python implementation (primes_ambi_plain.py). In the table below, N is the largest integer checked for primality.
```

                                  N
                  -----------------------------------
                  10000         100000        1000000

Numpy             0.238s        0.206s        1.316s       (primes_ambi.py)
Plain Python      0.030s        0.068s        4.267s       (primes_ambi_plain.py)

```

Importing the numpy module takes time. This may explain why the numpy version is slower 
for small values of N, but faster for large N.

primes_ambi.py:

[PHP]#!/usr/bin/env python
import numpy as np
import sys

__source__='http://tommih.blogspot.com/2009/04/fast-prime-number-generator.html'
__date__ = '$Date: 2009-07-20 $'

def ambi_sieve(n):
    s = np.arange(3, n, 2)
    for m in range(3, int(n ** 0.5), 2): 
        if s[(m-3)/2]: 
            s[(m*m-3)/2::m]=0
    return np.r_[2, s[s>0]]

n=int(sys.argv[1])
for prime in ambi_sieve(n):
    print prime[/PHP]


primes_ambi_plain.py:
[PHP]#!/usr/bin/env python
import sys

__source__='http://tommih.blogspot.com/2009/04/fast-prime-number-generator.html'
__date__ = '$Date: 2009-07-20 $'

def ambi_sieve(n):
    s = range(3, n, 2)
    for m in range(3, int(n ** 0.5), 2): 
        if s[(m-3)/2]: 
            for t in range((m*m-3)/2,(n>>1)-1,m):
                s[t]=0
    return [2]+[t for t in s if t>0]

n=int(sys.argv[1])
for prime in ambi_sieve(n):
    print prime[/PHP]

(I am not posting this in the "Prime Time: C, Lisp, and Python" thread [http://ubuntuforums.org/showthread.php?t=1215711](http://ubuntuforums.org/showthread.php?t=1215711) since those guys are trying to compare the same naive algorithm written in many languages.)

---

### Post by ahmatti on 2009-07-22
Thats interesting, thanks a lot! Maybe I'll try to implement the same in R to see how it compares. That is if gunksta doesn't beat me to it ;)

This thread is almost like a numpy tutorial now!

---

### Post by gunksta on 2009-07-22
Why would anyone want to move away from naive algorithms? I agree with unutbu, the procedure defined in the other thread is limited in how far it can be optimized without fundamentally changing the algorithm.

Of course, optimization involves a cost. Detailed optimizations often take more programming effort than a more direct "brute force" methodology. Which is more important - The programmer's time or the computer's? I don't write front-end applications, I write one-off analysis programs for research projects. My programming time is typically more important (to me) than the computer's. If a brute force method is easier to think through and code, I'm likely to do so, since the computer-time cost is essentially negligible for me. Obviously the opposite is often true when writing applications that will be used by others.

Implementing unutbu's logic in R is probably going to be a little tricky. ahmatti is right that lapply is logically hiding a loop rather than replacing it outright. I'd like to find a way to optimize the R code, by minimizing the number of iterations of the apply statements. So I thought about it all and realized that I needed to minimize when I use the loop. Obviously, any number evenly divisible by 2 is not prime. Equally obvious is that this is ~1/2 of N. It's easy to vectorize a test for even / odd in R, which is what I did. I also added in a test for evenly divisible by 5. It occurs once for ever 10 numbers, which is quite a few when you think about it. I also looked at 3 and 7 but they didn't really help much for this size of n, so I dropped them.

In the process of playing with this I discovered that my earlier is.prime() function was returning 0 (FALSE) for 2, which is incorrect. The following code corrects that mistake and makes the over-all function considerably faster, while not getting particularly complex.

[php]
is.prime <- function(num){
  if (num==2) return(1) else {
    check <- 2:round(sqrt(num))
    min(num%%check)
  }
}
               
primes_in_range <- function(start, end){
  numbers <- start:end
  out <- ifelse(numbers>2 & numbers%%2==0, 0, 1)
  out[out==1] <- ifelse(numbers[out==1]>5 & numbers[out==1]%%5==0, 0, 1)
  out[out==1] <- ifelse(numbers[out==1]>3 & numbers[out==1]%%3==0, 0, 1)
  out[out==1] <- lapply(numbers[out==1], is.prime)
  primes <- which(out==1)
  numbers[primes]
}
  

primes_in_range(0, 100000)
[/php]

Unfortunately, this code still runs slower (linearly) as N gets bigger. It's a better algorhithm but it's not exactly a good one.

Fortunately this is vastly different from what I normally do at work and I've enjoyed thinking about it all.

---

### Post by ahmatti on 2009-07-23
Nice work gunksta, I guess you could speed up even a little more by removing even numbers from the is.prime function ie. change the check vector to:
```
check <- seq.int(from = 3, to = round(sqrt(num)), by = 2)
```
And you're right trying to make programs faster is only waste of time for me too in most cases, but sometimes I just find quite entertaining :) I also find that implementing an algorithm written in language *a* with language *b* teaches you something about both.

---

### Post by unutbu on 2009-07-23
Is there a way to change the R program so that the value 100000
can be set at the command line instead of being hard-coded?

---

### Post by gunksta on 2009-07-23
**ahmatti:** I love the idea to speed up the is.prime() function. I'll play with that tonight.

**unutbu:** Umm.

Yes, No, and Yes.

R is a funky little beast. It's not meant to be a "general purpose" programming language like Python. Instead, R is meant to be a general purpose statistical analysis language. It's also generally used in either an interactive manner or through a pre-defined script that generates a report. 

The code ahmatti and I have been playing with defines two functions and then calls the functions to produce the output. From within R you could call the second function      primes_in_range(x,y)      with any two values of x and y desired. There is a way to run R commands from the command-line more directly (littleR?), but I'm not familiar with it simply because I've never needed to do so. Thus the "command"    R 1+1     does not equal 2, it throws an error and lands you at an R prompt.  :-)

---

### Post by ahmatti on 2009-08-02
I see the poll is really even! It would be nice to also see why people have voted as they have. So please write at least a few lines why you like R/Python.

---

### Post by unutbu on 2009-08-02
ahmatti, I just found out and thought you'd like to know that matplotlib provides a function called rec_groupby which is roughly equivalent to R's aggregate.

(See [http://matplotlib.sourceforge.net/api/mlab_api.html#matplotlib.mlab.rec_groupby](http://matplotlib.sourceforge.net/api/mlab_api.html#matplotlib.mlab.rec_groupby))

So instead of using combinations() and aggregate() as in post #12, you could use
mp.mlab.rec_groupby:

[PHP]import numpy as np
import matplotlib as mp
import matplotlib.mlab
fh=open('crabs.out')
fields=fh.readline().split()
crab=np.array([tuple(line.split()[1:]) for line in fh if line.strip()],
              dtype=np.dtype([('sp','|S1'),
                              ('sex','|S1'),
                              ('index','<i4'),
                              ('FL','<f4'),
                              ('RW','<f4'),
                              ('CL','<f4'),
                              ('CW','<f4'),
                              ('BD','<f4'),
                              ]))
agg=mp.mlab.rec_groupby(crab,('sex','sp'),(('FL',np.average,'avgFL'),
                                           ('RW',np.average,'avgRW'),
                                           ('CL',np.average,'avgCL'),
                                           ('CW',np.average,'avgCW'),
                                           ('BD',np.average,'avgBD'),
                                           ))
for row in agg:
    print(' '.join([('%s'%row[field]) for field in agg.dtype.names]))
[/PHP]
which yields

```
F B 13.2700024414 12.1379992676 28.1019995117 32.6240014648 11.8159985352
F O 17.5940002441 14.8360021973 34.6180029297 39.0359912109 15.6320007324
M B 14.8419995117 11.7180004883 32.013996582 36.8100024414 13.3499987793
M O 16.6259973145 12.2620007324 33.6880004883 37.1879956055 15.3240002441
```

---

### Post by ahmatti on 2009-08-03
**@unutbu**
you were right, I do like this information. Thanks a lot for posting :)

---

### Post by gunksta on 2009-08-03
I just stumbled onto [this]("http://www.dennogumi.org/projects/datamatrix"). It's an attempt to implement the data.frame structure in python. I haven't used it yet but it is certainly relevant to this discussion and I find it to be very very interesting. I doubt that python will ever have the diverse range of statistical tests that are part of R, but the basics are already very well covered. Having a data structure that is as flexible as the data.frame make python even more interesting.

---

### Post by ahmatti on 2009-08-04
Thanks gunksta, that looks really interesting. Data.frame structure really makes certain manipulations really easy so indeed this make Python even more appealing to me. I agree that it is really difficult to match R in the number of implemented analysis. CRAN [http://cran.r-project.org](http://cran.r-project.org) has at the moment over 1800 packages, so you can find practically everything. Even so I think that data frames are useful also in e.g. machine learning problems, an area where Python seems appealing to me - especially for large datasets. 

Although I find that R is very nice for machine learning I wouldn't mind speeding up feature selection in certain problems. I think I'll try to do an implementation in both R and Python for my next project and see if Python indeed is faster, maybe even give Cython a try. Any advice, Python voters?

---

### Post by ahmatti on 2009-09-18
I just came across [http://mathesaurus.sourceforge.net/](http://mathesaurus.sourceforge.net/), Thesaurus of Mathematical Languages, or MATLAB synonymous commands in Python/NumPy. The site provides an easy command reference on equivalent functions in Matlab, R and Python. Seems very helpful :)

---

### Post by purgatori on 2009-09-20
I'm pretty ignorant on the subject, I'm afraid, but I prefer R. Not being a programmer, R makes more sense to me.

---

### Post by Spike the Dingo on 2010-08-20
I'm always torn between the two, and really my answer depends on what I'm trying to accomplish (so, I didn't vote for one or the other).

I would say that I'm fluent in both R and Python, although I tend to use Python for heavier coding and R for scripts and interactive analysis. In other words, I like Python for the language and R for its tools (see below).

In short, as I sit here and think:

R:
[LIST]
[*]really really nice plotting
[*]awesome tool set and higher-level functions
[*]terrible for parsing files
[/LIST]

Python:
[LIST]
[*]Very nice and intuitive language (my coding language of choice)
[*]less developed tool set when compared to R
[*]plotting abilities strike me as a bit... "blunt" [ha - ha, get it?]
[*]much better for parsing and data processing/formatting
[/LIST]

So, my work flow usually looks something like:
==(data goes in)==>Processing and heavy lifting with Python ==(nice data ready for R)==> Analysis and plots with R

If Python could plot like R and had better higher-level tools and functions for statistics, I would prob switch from R. (but I still love you R)

---

### Post by gunksta on 2010-08-21
> **Spike the Dingo said:**
> 
[LIST]
[*]terrible for parsing files
[/LIST]
 I'm not sure I can completely agree with you there. I do like Python although I'm probably a little rusty right now because I'm spending so much time in R. There are extensions to parse things like XML in R although having never used the python equivalent  I can't really say which is easier. My point though is that you really must look on CRAN. There are so many useful extensions for R and these tend to be aimed at file formats and structures which I suspect aren't going to be easily parsed by Python.

For example - last week I wrote a script which opens a series of SPSS files and moves the data into a SQLite database. In the process, I made the format and structure of the datasets more similar, making it easier to work with.

Connecting Python and SQLite is easy. Connecting Python to a SPSS file -- is probably not real easy.

---

### Post by econobot on 2010-11-17
I came across this thread trying to answer this very question. From the R website ([http://cran.r-project.org/doc/manuals/R-data.html#Spreadsheet_002dlike-data):](http://cran.r-project.org/doc/manuals/R-data.html#Spreadsheet_002dlike-data):)

In general, statistical systems like R are not particularly well suited to manipulations of large-scale data.  Some other systems are better than R at this, and part of the thrust of this manual is to suggest that rather than duplicating functionality in R we can make another system do the work!  (For example Therneau & Grambsch (2000) comment that they prefer to do data manipulation in SAS and then use **survival** in S for the analysis.)  Several packages allow functionality developed in languages such as Java, perl and python to be directly integrated with R code, making the use of facilities in these languages even more appropriate.  (See the **SJava**, **RSPerl** and **RSPython** packages from the Omegahat project, [http://www.omegahat.org]("http://www.omegahat.org/"), and the **rJava** package from CRAN.)     


It is also worth remembering that R like S comes from the Unix tradition of small re-usable tools, and it can be rewarding to use tools such as awk and perl to manipulate data before import or after export.

---

### Post by ipstone on 2011-06-11
Hi Spike the Dingo

I have the similar thoughts as yours regarding this topic. But as I am new to python data processing, I am wondering if there's any tools can compare two different data set, and interacting with the user to choose the specifics in each set which to keep, in the process of merging  them ...

say dataframe A, and a slightly dataframe B
now I want to update those rows (say OutcomeA, outcomeA-date) with a newer date in (outcomeA, outcomeA-date) in B ...

I am thinking that I probably can do it in R, that I need to loop through the column, and loop through each rows to compare A, B and update

or is there a better way?

thanks

Best, Ipstone

---

### Post by pmb cana on 2011-07-11
At this time, R and Python used together give the highest power and possibilities. I think if we use both at this time, and then we could get rid of SAS, SPSS, MS Excel etc.

However, Excel (with VBA macros) remains a necessity at lower stratum especially in the businesses. For this stratum, I would imagine the day when I could replace Excel+VBA with LibreOffice’s Calc + Python.  

Python folks! Please streamline efforts within libs SciPy, NumPy and Matlibplot and merge it together. 

R and Python folks ! Please give **LibreOffice **a chance. 

Thanks

---

### Post by fikio3 on 2011-10-13
I read through all the posts here but am still unclear whether to learn R or Python.

I need to learn a general purpose programming language and have decided it would make sense to learn one thoroughly so that in the future I would be able to write whatever I want, rather than know a little in a few languages. I know SAS and will use it for statistical analysis. I am a fair user of MATLAB and really like its ability to handle matrices, but will need to learn something open source. Given that I do not need to do data analysis (unless it's something that can't be done in SAS), is Python or R better? 

I am more interested in saving time for myself while programming rather than the speed of how fast my programs will run. Some things I want to do now include basic NLP (for which I am actually learning some Perl) and downloading and reformatting data from the Internet. I also know SQL and would like a language that I can use to interact with SQL and get my data into an Oracle database.

Thanks for any input!

---

### Post by gunksta on 2011-10-14
The discussion in this thread was just a geeky (mostly irrelevant) comparison of Python and R between people who are primarily using both languages for data  analysis. It was not meant to be a resource for anyone trying to make an  informed decision regarding which language to learn. In other words - Don't read too much into anything you see here. :popcorn:

If you'd like to get a broader opinion, I recommend starting a new thread. My .02 is pretty simple. Python is the better "general purpose" language. R is an incredible tool / language for data analysis, but I wouldn't use it to write the next gen Twitter client. (For the record - I have no plans regarding any next gen Twitter client.) If you are going to use SAS for data analysis, R is probably less useful to you, although it is an incredible language for data analysis.

.

---

### Post by 3Miro on 2011-10-14
Can't compare R to Python, those are apples and oranges. Python is general, R is specifically oriented towards stats. I wouldn't use R for anything other than stats, while Python can be used for many things.

Having said that, I maintain that if you want to know general programming, you need to know C\C++.

---

### Post by euler_fan on 2011-10-16
To summarize up front: R is really good at what it is designed to do (facilitate data analysis) and explicitly expects the user to respect its limitations. By ``respect [R's] limitations", I mean to either accept them or learn to leverage R's ability to play well with other tools (C, FORTRAN, SQL) to get the job done.

More broadly . . . 

I generally agree that Python is better if one is looking to learn a general purpose language with lots of abilities is lots of areas. So many so, in fact, that it is [comical]("http://xkcd.com/353/"). 

If one needs to do lots of statistical analysis, then R is significantly better equipped out of the box to handle said tasks and *many* people have spent time putting together great tools on CRAN to do common things well.

As to the speed/optimization issues, I would say two things:

1) familiarity with the tools a language has makes a big difference--a good Python programmer can probably work around any limitations in Python's statistical abilities faster than they could learn to use R's tools effectively for the same task even if the R code nets out cleaner and vice versa.

2) R has some pretty explicit advice about problems that need to run fast or handle large datasets. In the former, write a package that uses C or FORTRAN code to do the heavy lifting. In the latter, someone above already mentioned the SQL package for R.

Finally, I would like to point out that except in well understood areas, just figuring out the correct approach to data analysis in a given problem area likely takes so long and is so important in comparison to learning any particular language well enough to write any custom software that the latter is of relatively minor significance.

---

