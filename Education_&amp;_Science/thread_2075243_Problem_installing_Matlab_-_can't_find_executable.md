---
title: "Problem installing Matlab - can't find executable"
date: 2012-10-23
forum: Education &amp; Science
---

### Post by Moneyperson on 2012-10-23
So I was trying to install Matlab from the software centre, I've tried several times and it keeps stopping halfway and bringing up a window asking for the location of the Matlab executable file, which doesn't seem to be anywhere in my file system. Any ideas?

---

### Post by lykeion on 2012-10-23
Check the troubleshooting section of this page: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

Hope that it helps

---

### Post by Moneyperson on 2012-10-25
Ah, I see what the problem is now, basically the download from the software centre doesn't install Matlab, it just makes it run a little better on Ubuntu, also I'm a big numpty. Apologies.

---

### Post by zdqe on 2012-10-30
I have the r2006a and at first I couldn´t install it, so i did some google research and I found that, [i]("http://www.treathemorrhoidsguide.com/")n order to install Matlab, you have to disable the Aerio graphic mode to the classical windows mode, so we´ll be able to install the thing...

---

### Post by redeagleye on 2012-10-30
What you have to do is to use a MATLAB Unix version.
Install it and run it by his BIN file.
hope that helps

---

### Post by El Tito on 2012-11-17
As @redeagleye says, you need the unix version.
Once you mount the image or the cd, you only need to execute the install file.
You will be prompted for a serial key, then it will install and after that you would need your license file (the path). After that you may have a minor problem at the start (an error message about desktop configuration if I recall correctly). This is due to a permission problem (the program can't write the configuration). Give 'w' permission to the folder and enjoy!

---

### Post by El Tito on 2012-11-17
The problem with desktop config I mentioned above, is solved after and including version 2011a.

---

