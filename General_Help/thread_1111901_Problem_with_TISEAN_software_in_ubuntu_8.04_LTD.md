---
title: "Problem with TISEAN software in ubuntu 8.04 LTD"
date: 2009-03-31
forum: General Help
---

### Post by Adriens on 2009-03-31
Hello all!

I need to use the TISEAN software. I have download on my desktop on the address: [http://www.mpipks-dresden.mpg.de/~tisean/Tisean_3.0.1/index.html](http://www.mpipks-dresden.mpg.de/~tisean/Tisean_3.0.1/index.html)
So, I have unzip the file TISEAN_3.0.1.tar.gz
I go inside the file TISEAN_3.0.1. and I've try to double click on configure then I have launch that on the terminal but something happen very quickly, then I have launch install.sh in the terminal something happen very quickly too...But the softeware don't work.
So I have try the solution for the installation of the developers by doing:
./configure
make
make install

in the terminal, but nothing right happen.

So, How can I install this software on Ubuntu 8.04 LTD? It is compatible with ubuntu?

Thank you for your attention and your help.

---

### Post by Spaarkplug on 2009-03-31
Wow.
I was just googling what TISEAN was.
Anyways, it seems this package/app is super old man. December 2000!
I undestand you got to use this, but can you not use Matlab?
I wonder if this ubuntu supports this package.
When you type make, its compiling to make the .so file for ubuntu kernel. Which I doubt is not working, and only reason i can think of is maybe its not supported, or your kernel has issues or perhaps, you should try an older and stable distro like debian or something.

Could there be any updates to this? Most likely not.
I read [http://www.mpipks-dresden.mpg.de/~tisean/TISEAN_2.1/](http://www.mpipks-dresden.mpg.de/~tisean/TISEAN_2.1/)

Sorry, for not being much help here. Only my comments.


-Spaark

---

### Post by Adriens on 2009-03-31
Hey Spaarkplug,

the version that you see is very old decembre 2000, but the 3.0.1 version was from december 2007. So it was not so long. But I can understand how to install this .tar.gz it is the main problem.

thanks for your help!

---

### Post by Adriens on 2009-03-31
IT'S OK!

I HAVE SOLVE THAT MYSELF... I'M BEGINNER BUT ABDUCTIVE BEGINNER.
So how I have done? Maybe it's a total in-interesting but I will explain.
-first you download the .tar.gz
-then you open the transfert the .tar.gz in the /usr/local/src place
-here, you 're. So you have to use your terminal or to gunzip yourself your tisean .tar.gz
-Once the .tar.gz open you write on the terminal :
cd /usr/local/src 'for indicate the way to your computer
./configure 'to configure your application see well the future place of your program on your computer. It can be use full to remove cleanly TISEAN
make 'here the software begin to show you a chance of success
make install 'because the classical and clean sudo checkinstall have never work with me

and then you can if you have installed gnuplot celebrate your investment in time...because you'll be able to compute lyapunov exponent, stationarity test, correlation dimension and other exciting statistics!!!

YEAH!!!!!!!!!!!!!!!!!!!!

---

### Post by abhinav.gaur13@gmail.com on 2011-03-31
Hello..
I have installed it in ubuntu 10.10. I used the following:
steps:
a) become super user

b) My machine did not have g77. Instead it had gfortran. so I had to use export.
export FC=gfortran
It will be better to put this line in your bashrc file so that you dont have to write this everytime you log off.

c)extract the tar.gz file using the command given on the TISEAN website.

d)Then as usual, ./configure, make, make install

Try this, I think this should work.

abhinav

---

