---
title: "Cannot write to preference file &quot;matlab.prf&quot; in &quot;/user/.matlab/R2012a&quot;."
date: 2014-10-13
forum: Education &amp; Science
---

### Post by souraklis on 2014-10-13
I have installed matlab. I am trying to compile some .c files from matlab in order to run a matlab code (which use those files). 
```
mex -O resize.cc
mex -O reduce.cc
mex -O dt.cc
mex -O features.cc

% use one of the following depending on your setup
% 1 is fastest, 3 is slowest 

% 1) multithreaded convolution using blas
mex -O fconvblas.cc -lmwblas -o fconv
``` 

However I am getting the following error :Cannot write to preference file "matlab.prf" in "/home/krishtosh/.matlab/R2012a".
Check file permissions. The problem is that this dir doesnt exist matlab has been installed in other directory. What have to od in oder to compile normally the code?

---

### Post by Sef on 2014-10-13
Moved to Education & Science.

---

### Post by steeldriver on 2014-10-13
I don't think the *installation *directory should affect where matlab tries to save user-related config files - what does

```

ls -l ~/.matlab

```

say about the directory and its permissions?

---

