---
title: "Matlab and Java version incompatibility"
date: 2009-07-16
forum: Education &amp; Science
---

### Post by karyisdead on 2009-07-16
Hi,
I am using Hardy with compiz and Matlab 7.4. I have 
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.14/jre/
```in my /opt/matlab/bin/matlab. Matlab runs normally but has two problems.

1. When I click any button on a figure window it reports:

java.lang.NullPointerException
    at com.mathworks.jmi.bean.MatlabBeanInterface.addCallback(MatlabBeanInterface.java:680)
    at com.mathworks.jmi.bean.MatlabCallbackInterface.addCallback(MatlabCallbackInterface.java:128 )

2. Sometimes while working (especially with figures), my title bars disapear (along with the close, minimize, maximize buttons) so I restart gdm because I don't know how else to fix it.

I am rather new to Ubuntu (6 months or so) and I work with matlab alot, so any help will be greatly appreciated.

---

### Post by Choose on 2009-07-16
Hi,this thread might be of some help to you [http://ubuntuforums.org/showthread.php?t=635142]("http://ubuntuforums.org/showthread.php?t=635142") good luck ;-)

---

