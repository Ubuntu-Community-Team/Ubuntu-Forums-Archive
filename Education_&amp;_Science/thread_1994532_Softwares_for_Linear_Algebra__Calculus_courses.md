---
title: "Softwares for Linear Algebra / Calculus courses"
date: 2012-06-02
forum: Education &amp; Science
---

### Post by guilleing on 2012-06-02
Hi, im new in Ubuntu. I am taking courses on Calculus and Linear Algebra. I know there are several softwares to graph funcions, like Kalgebra, but i would like to know if there is any software that can be usefull for some basic Linear Algebra (i.e. to graph things like vectors and planes).
Do you know any software that can be used for both courses?

I've been checking this list: [http://en.wikipedia.org/wiki/Comparison_of_computer_algebra_systems](http://en.wikipedia.org/wiki/Comparison_of_computer_algebra_systems)

I've tested Maxima, but i think it was a little bit "overkill" for my needs.

I know some python, so if it uses python syntax, its not a problem.

Thank you!!

P.D: excuse me for my poor english!

---

### Post by Penguinnerd on 2012-06-02
I know you're looking for downloadable software, but I think this applet is quite good.

[http://web.monroecc.edu/manila/webfiles/calcNSF/JavaCode/CalcPlot3D.htm](http://web.monroecc.edu/manila/webfiles/calcNSF/JavaCode/CalcPlot3D.htm)

---

### Post by pissedoffdude on 2012-06-02
Have you tried wolfram alpha?  Best website ever.  It's been able to do most of the calculations I've asked it to.  You just have to fiddle with the way you input whatever you want to do.  [http://www.wolframalpha.com/]("http://www.wolframalpha.com/")

---

### Post by Redblade20XX on 2012-06-02
Take a look at gnu octave it's like the free ware version of matlab.
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

-Red

---

### Post by PC_load_letter on 2012-06-02
For what you ask, I think nothing beats SAGE from [www.sagemath.org](www.sagemath.org)
Version 5.0 has been recently released, and now they have an Ubuntu PPA.
The syntax is Python or very close to that, you use your browser as a GUI, will probably need to install Oracle's Java to do 3D plots, but that's not too bad. I'd say for what you asked, SAGE is a perfect fit.

**EDIT:** You can even install it as a Chrome browser plugin from the [Chrome web store]("https://chrome.google.com/webstore/detail/dckejpjjnjaagdahkdgighlejbckajak") (for free of course), but then it does all the processing on some remote server so it's going to be considerably slower but for simple stuff, you probably will not notice it.

---

### Post by guilleing on 2012-06-05
Thanks to all of you for your time!!

I will try SAGE. Where can i install it from the repositories?

I downloaded the Binary from their website but i'm scared of messing something up with the path and/or directories if i just follow **[this tutorial]("http://www.sagemath.org/doc/installation/binary.html#linux-and-os-x")** haha

Consider im totally new to linux, i'm reading **[this]("http://http://code.google.com/edu/tools101/linux/basics.html#copy_file_into_directory")** in order to gain some confidence in the linux world!

thanks

---

### Post by PC_load_letter on 2012-06-05
Go to the SAGE web site, then click on download, or simply click:
[http://www.sagemath.org/download-linux.html](http://www.sagemath.org/download-linux.html)

Now scroll down, and you will see that they have an Ubuntu PPA, copy it or simply do the following:
1- Open a terminal window, and type the following (copy/paste).
```
sudo apt-add-repository -y ppa:aims/sagemath
```
2- Enter your password.
2.5- Confirm the addition of the PPA by hitting ENTER.
3- At the terminal prompt, type:
```
sudo apt-get update && sudo apt-get install sagemath-upstream-binary
```
4- Hit ENTER when you're asked to confirm the installation.
5- Start SAGE by simply typing **sage** in the terminal. You'll be prompted to enter a new password, then your default browser will open, have fun :D

---

### Post by guilleing on 2012-06-07
It worked, thank you very much!!

---

### Post by PC_load_letter on 2012-06-08
One thing you might wanna test is 3D plots. Start a SAGE session in your default browser and in a cell type:
```
x, y = var('x,y')
plot3d(x^2 + y^2, (x,-2,2), (y,-2,2))
```
Then click 'evaluate' or hit ALT + ENTER.

If the Jmol applet starts and you see a paraboloid then it works, if not, then you simply need to install Oracle Java instead of the Open JDK that comes by default with Ubuntu.

---

