---
title: "How to call MATLAB from terminal?"
date: 2015-11-19
forum: Education &amp; Science
---

### Post by milenko-markovic on 2015-11-19
I have installed MATLAB and then I have export the path.

milenko@milenko-HP-Compaq-6830s:~$ echo $PATH
/home/milenko/anaconda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/lib:/usr/local/proc_mt/bin:/home/milenko/usr/local/matlab2015a/bin:/home/milenko/usr/local/matlab2015a/bin:/usr/local/matlab2015a/bin

When I type matlab 
matlab: command not found

What should I change?

---

### Post by slickymaster on 2015-11-19
Go to the bin folder in your Matlab installation directory and execute it from there:```
cd /usr/local/MATLAB/.../bin
./matlab
```
For reference: [How do I launch MATLAB on Linux?]("http://www.mathworks.com/matlabcentral/answers/93739-how-do-i-launch-matlab-on-linux")

---

