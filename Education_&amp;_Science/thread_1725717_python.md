---
title: "python"
date: 2011-04-10
forum: Education &amp; Science
---

### Post by Mosabama on 2011-04-10
I started to learn python.. I ran into something made me crazy..

look at this:

```
File Edit Options Buffers Tools Python Help                                                                                                                
import sys
import os
#import time                                                                                                                                               
#Define dorange function                                                                                                                                   
def dorange(y):

    x=range(y+1)
#    print len(x)                                                                                                                                          
    for i in x:
        print i,
        if len(x)==i+1:
            pass
        else:
            print ',',

#print sys.argv                                                                                                                                            
var = raw_input("Enter a number: ")

#print var                                                                                                                                                 
try:
    int(var)
except ValueError:
    print "this is NOT int"
    sys.exit()

dorange(int(var))
#print "444444444444444444444"                                                                                                                             
#print """The program is done                                                                                                                              
#Thank you for using pyhton"""                                                                                                                             
#print var                                                                                                                                                 
#time.sleep(1)                                                                                                                                             
#if var >= 5:                                                                                                                                              
os.system("ls -l /home/mosab/Desktop/")
#else:                                                                                                                                                     
#    print "NOOO"     
```

why in heavens name os.system (the last statement) gets executed before dorange(int(var)) ???

---

### Post by Amente on 2011-04-10
I tried the code. Indeed the os.sytem statement out put comes first.But If you try changing  the parameter given to 'dorange' function to 

dorange(var)

then The raw_input statement executes,then When you enter a Number, (test.py is the code)the interpreter raises Type error saying 
Traceback (most recent call last):
  File "test.py", line 27, in <module>
    dorange(var)
  File "test.py", line 8, in dorange
    x=range(y+1)
TypeError: cannot concatenate 'str' and 'int' objects

from this I can say the dorange function executed first.

---

### Post by Mosabama on 2011-04-10
but what about the output?

when I change os.system with something like print "hello" it gets fixed ...

but in that case the output of os.system comes out first .. Why?

bug?

---

### Post by Amente on 2011-04-10
> **Mosabama said:**
> but what about the output?

when I change os.system with something like print "hello" it gets fixed ...

but in that case the output of os.system comes out first .. Why?

bug?

I don't think it is a bug.It is unlikely.I am also a python newbie so I have to read on this.

---

### Post by FreeTheBee on 2011-04-10
This looked strange to me as well. It seems the comma not only removes the \n at the end of the line. It seems more like it stays kinda open, waiting for more things, that should go on the same line. If you remove the commas everything prints in the right order. An empty print statement without comma after all the others, to end the line works as well.

For example this,

print 'a',
os.system('uname')
print 'b'
os.system('uname -r')
print 'c',
print 'd'
os.system('uname -o')

generate this output,

Linux
a b
2.6.35-28-generic
c d
GNU/Linux

---

### Post by Mosabama on 2011-04-10
weird !!

---

### Post by sam123 on 2011-04-10
Try using "sys.stdout.flush()" before the os.system call. That will fix it.

print uses the python interpreter's I/O streams and os.system spawns another process which has its own I/O streams. The latter ends first and is flushed. 

Read the documentation of sys.stdout at [http://docs.python.org/library/sys.html](http://docs.python.org/library/sys.html)

It is a slightly odd case, I agree.

---

### Post by Mosabama on 2011-04-11
thanks it works now ... and thanks for the info now I understand why :)

---

### Post by LemursDontExist on 2011-04-11
You might consider using [subprocess.Popen]("http://docs.python.org/library/subprocess.html") in the future.  Generally, the subprocess module is a better choice since it doesn't have th weird behavior and side effects of os.system.

---

### Post by Mosabama on 2011-04-11
> **LemursDontExist said:**
> You might consider using [subprocess.Popen]("http://docs.python.org/library/subprocess.html") in the future.  Generally, the subprocess module is a better choice since it doesn't have th weird behavior and side effects of os.system.

Thanks, that works great too :)

---

