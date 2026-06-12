---
title: "Problem with Matlab in Ubuntu"
date: 2010-09-29
forum: Education &amp; Science
---

### Post by JCM_Pico on 2010-09-29
Hi there,

I recently installed Matlab in Ubuntu, and every thing went well. I change the permission of the folther ~/user/.matlab, using the command sudo chmod 777 .matlab, in order to be able to make some changes, I also plased a link in /usr/local/bin to the matlab executable (sudo ln -s /usr/local/matlabR2010a/bin/matlab /usr/local/bin)  to be able to execute it easily.

Every thing ok except that I can't add some folder to the Matlab path and save it.....
I even try using sudo matlab to run the program and add all the folders that I need to be in the Matlab path, but when I quit and start Matlab again they just disappear from the program path ...

Does anybody knows how to add a folder to matlab path? and keep it there?

---

### Post by perroazul on 2010-09-30
did you try using the menu file>save path?
I'm not sure that I really understand what is your problem.

---

### Post by MartijnBangor on 2010-10-05
Hi,

I had exactly the same problem, and probably you're only 2steps away from happy MatLabbing. My guess is that you will have to change the permission of pathdef.m

1)Open Terminal & go to the directory where pathdef.m lives
In  most cases you will have to type type: 

cd usr/local/matlabR2009a/toolbox/local

IMPORTANT: I'm using matlab version R2009a. However, you should check  your version to obtain the correct path name. For example, if you have  version R2010b you will have to type: cd  usr/local/matlabR2010b/toolbox/local

2) chmod pathde.m. Just type:

sudo chmod 777 pathdef.m


Cheers,

Martijn

---

### Post by freefaling on 2012-05-11
> **MartijnBangor said:**
> Hi,

I had exactly the same problem, and probably you're only 2steps away from happy MatLabbing. My guess is that you will have to change the permission of pathdef.m

1)Open Terminal & go to the directory where pathdef.m lives
In  most cases you will have to type type: 

cd usr/local/matlabR2009a/toolbox/local

IMPORTANT: I'm using matlab version R2009a. However, you should check  your version to obtain the correct path name. For example, if you have  version R2010b you will have to type: cd  usr/local/matlabR2010b/toolbox/local

2) chmod pathde.m. Just type:

sudo chmod 777 pathdef.m


Cheers,

Martijn

That did it!

I was having the exact same problem, i.e. MATLAB won't let me save changes to the pathdef.m file via pathtool saying I don't have write access or the folder is read-only. And this did it! Now I am a happy MATLABer :)

---

