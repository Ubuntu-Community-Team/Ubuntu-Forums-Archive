---
title: "Saving mixed data in scientific python"
date: 2009-01-19
forum: Education &amp; Science
---

### Post by Glenn Jones on 2009-01-19
Hi,

So I've recently moved away from using matlab to use scientific python using predominantly pylab, numpy and scipy. I am however having difficultie in saving a mixed data format of the following structure:

# Header 1
# Header 2
x(1)   y(1)   z(1)
 .      .      .
 .      .      .
 .      .      .
x(N)   y(N)   z(N)

I can save the header files quite easily using the following:
```

f=open('myfile.txt','w')
f.write('#Header1\n#Header2)
f.close

```

When I more myfile.txt I get
#Header1
#Header2


The difficultie I'm having is storing the array below the header. The x,y,z data is stored as a numpy.ndarray called XYZ. I have tried pickling the data but I must admit I'm not sure what I'm doing.  

Can any of you guys help? Are there any numpy/scipy modules I can use?

Cheers

---

### Post by sjbaugh on 2009-01-19
Glenn,

I don't know scientific python/Pylab etc but the write statement you have in normal python will only write what you are getting.

You may try:


```
f=open('myfile.txt','w')
f.write('#Header1\n#Header2)
f.write(XYZ)
f.close
```

and see if the output is useful to you. Other wise if nobody can find a library routine to help you may have to iterate through the array with for statements and write each element individually.

Hope this helps,

Steve

---

### Post by ssam on 2009-01-20
there are some examples at [http://www.scipy.org/Cookbook/InputOutput](http://www.scipy.org/Cookbook/InputOutput) that may help you.

---

