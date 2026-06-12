---
title: "How to incude octave-image in Octave?"
date: 2013-02-06
forum: Education &amp; Science
---

### Post by satyamM on 2013-02-06
Hi, I am using Ubuntu 12.04 and just installed Octave as I've to do a bit of image processing.

I also installed **Octave-image **package/add-on from software center. 

I** don't know how to include this package/add-on in octave **or does it get included by itself in it as soon as it is installed?

I tried to produce complement of a image by following command after installing octave-image: ```
h = imcomplement(f)
```But this produced following error:

```
error: `imcomplement' undefined near line 11 column 5
```.

Please help anyone.

---

### Post by satyamM on 2013-02-06
I need some urgent help fellas. Please help as soon as you can.
Your help is much appreciated.


And sorry for the spelling error in "include" in main subject.

---

### Post by satyamM on 2013-02-06
To add more information about my problem, I am executing one octave script.

My octave script reads like: 
[B]
I=imread('b.jpg'); 
imshow(I) 
J=imcomplement(I); 
figure, imshow(J) 
[/B]
It is saved in a file named "a.m". 

Now whenever I want to execute this a.m script  I type on octave terminal:   a 
It gets executed but produces following error: 
[B]
octave-3.2.4:13> a 
error: `imcomplement' undefined near line 5 column 3 
error: called from: 
error:   /home/satyam/Desktop/a.m at line 5, column 2 
octave-3.2.4:13> [/B]


So what's the problem, Do i need to include octave-image in Octave? 
How?

---

### Post by steeldriver on 2013-02-06
by default it appears to get loaded automatically, but it will depend on your /etc/octave3.2.conf and/or local rc files I think

You should be able to check what packages are loaded with

```
octave> pkg list
```and if necessary load manually with

```
octave> pkg load image
```

---

### Post by satyamM on 2013-02-06
@steeldriver:

octave>pkg list produces:
```

satyam@ubuntu:~$ octave > pkg list
error: no such file, `list'
error: source: error sourcing file `list'
satyam@ubuntu:~$
```

octave > pkg load image produces:

```

satyam@ubuntu:~$ octave > pkg load image
error: no such file, `load'
error: source: error sourcing file `load'
satyam@ubuntu:~$ 
```


Now what?

---

### Post by steeldriver on 2013-02-06
sorry I meant to type 'pkg list' at the octave prompt - not the bash shell prompt

```
steeldriver@vm~ $ octave
.
.
.
octave:2> pkg list
Package Name  | Version | Installation directory
--------------+---------+-----------------------
       image *|  1.0.14 | /usr/share/octave/packages/3.2/image-1.0.14
octave:3> version
ans = 3.2.4
octave:4> 

```

---

### Post by satyamM on 2013-02-06
Mine one says something like following:


octave-3.2.4:14> pkg list
Package Name  | Version | Installation directory
--------------+---------+-----------------------
       image  |  1.0.14 | /usr/share/octave/packages/3.2/image-1.0.14

octave-3.2.4:15> version
ans = 3.2.4
octave-3.2.4:16> 

now what?

---

### Post by steeldriver on 2013-02-06
did you try ```
pkg load image
```

you can get help on the pkg command (including auto loading options) by typing ```
help pkg
```

---

### Post by satyamM on 2013-02-06
@steeldriver:

I was not doing "pkg load image" at octave prompt, thus image package was not loading.

I did it as you said, now my code is compiling and producing desired output.
Thank you  steeldriver.

---

