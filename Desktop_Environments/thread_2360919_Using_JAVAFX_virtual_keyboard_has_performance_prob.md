---
title: "Using JAVAFX virtual keyboard has performance problem on ubuntu 14.04"
date: 2017-05-09
forum: Desktop Environments
---

### Post by darkkmj on 2017-05-09
Hello, 

I have a problem about using JAVAFX virtual keyboard function on ubuntu 14.04.

I run very simple test program that is developed using JAVAFX.
And I run this program with VM-option for using JAVAFX virtual keyboard.
The VM-option is same below.
  -Dcom.sun.javafx.isEmbedded=true
  -Dcom.sun.javafx.touch=true
  -Dcom.sun.javafx.virtualKeyboard=javafx
  -Dcom.sun.javafx.vk.adjustwindow=true

But, When I clicked edit box, the virtual keyboard is shown slowly.
And if I put any character using virtual keyboard, then it is operated slowly.

My test platform is shown as below.
  CPU: Intel J1900 bay-trail chip (2.0GHz)
  RAM: DDR3 4GB
  DISK: SSD 32GB

On windows 7 and CentOS, it is operated normally.
Please, share any simillar experience and suggest any solution.

Thank you

---

### Post by QIII on 2017-05-09
Hello!

Are you running CentOS and Windows on the same machine?  Do you have the same applications running in the background?

We don't know what your code looks like, so it would be difficult to make much beyond wild guesses.

---

### Post by darkkmj on 2017-05-10
Yes, I run same application on the same machine (Windows, CentOS).
And also, there doesn't exist any background application except test application.
The test application is very simple.
It is a simple GUI program that is made by using JAVAFX.
It has only edit box for input data from user using virtual keyboard.

---

### Post by QIII on 2017-05-10
Is this a touch-screen or kiosk type application?

---

### Post by darkkmj on 2017-05-10
A touch-screen application. But, a wireless keyboard and mouse can be used on target platform.

---

### Post by QIII on 2017-05-10
And you are using plain Ubuntu with Unity on that 10w Celeron with fairly low-spec, on-die Intel graphics?

Unity is very resource hungry -- that's how it gets to be so slick and pretty.  But it might not be the best choice for your overall application.

Have you tried a lighter flavor such as Xubuntu or Lubuntu?

---

### Post by darkkmj on 2017-05-10
Ok. I think that your advise is reasonable.
So, I will try to test on the Kubuntu and Xubuntu.
Thank you for your advise.

---

### Post by QIII on 2017-05-10
Avoid Kubuntu.  It can be heavy, too.  Xubuntu or Lubuntu would be best.

---

### Post by darkkmj on 2017-05-10
I solved problem by using the Xubuntu.
My application is operated successfully on the Xubuntu.
Thank you very much for your help.

---

### Post by QIII on 2017-05-10
No problem!

You're welcome.

---

