---
title: "Problem with Matlab figures disappearing in Ubuntu 14.04"
date: 2014-09-02
forum: Education &amp; Science
---

### Post by wthurt on 2014-09-02
Hello,

I have Matlab R2104b installed on my machine running Ubuntu 14.04. I've been using Matlab a lot for the past few weeks with no problems. I can start a figure window with a Matlab command like Fig = figure(1). When I then try to display an image, the figure window disappears. According to the Matlab icon on the Unity launcher, the figure exists; I just can't select it or view it. Any thoughts?

---

### Post by cturnes on 2014-10-15
This is an interesting issue.  What version of MATLAB are you using?  And how are you displaying the image (that is, with what functions)?  

After you display the image, if you do 
```
>> figure(gcf); 
```
do you then see the image?

---

### Post by cturnes on 2014-10-15
Also, try launching MATLAB with the 

```
$ matlab -softwareopengl
```

startup flag.  That will use the software version of OpenGL instead of the hardware version (this tends to resolve a lot of graphics issues).

---

### Post by lucasnogueira on 2015-06-15
> **cturnes said:**
> Also, try launching MATLAB with the 

```
$ matlab -softwareopengl
```

startup flag.  That will use the software version of OpenGL instead of the hardware version (this tends to resolve a lot of graphics issues).

I am facing the same problem as the op. Unfortunately, using the suggested flag did not work :(

---

### Post by anasiri-chemproceng on 2015-07-28
I had the same problem with Matlab 2015. the same script ran with no problems in 2014(unlike your case), however when I use "drawnow" code under ''figure'' inside the script, the problem solved. may this one also work for u?

---

