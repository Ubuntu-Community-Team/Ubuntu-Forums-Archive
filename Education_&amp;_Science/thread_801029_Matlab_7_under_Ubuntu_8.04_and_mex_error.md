---
title: "Matlab 7 under Ubuntu 8.04 and mex error"
date: 2008-05-20
forum: Education &amp; Science
---

### Post by anaGP on 2008-05-20
Hello!!
Work with matlab 7 (R14) under linux and the distribution kubuntu of linux (ubuntu 8.04 kernel 2.6.24-16-generic). Matlab does not recognize mex -setup (to see underneath and to see matlabrc.m), but in line of command of linux works correctly  ¿can help me with this error?
Thank you very much,
 
AnaGP
 
 
////// Error  Message //////
Bienvenidos. A trabajar con TrueTime.

Espere por favor ...

Todo bien hasta aca ...

Warning: Unrecognized MATLAB option "setup".


License Manager Error -2.

Invalid license file syntax

Feature:       MATLAB

License path:  /usr/local/matlab7/bin/mex

FLEXlm error:  -2,413

For further information, refer to the FLEXlm End User Manual,

available at "www.macrovision.com".
 

Check the MATLAB INCREMENT line in your license file,

or make sure you have a USE_SERVER line instead

of INCREMENT lines.  Also check to be sure there is

a carriage return at the end of the USE_SERVER line.


For more information, see The MathWorks Support page at

[http://www.mathworks.com/support](http://www.mathworks.com/support) and search for

"license manager error -2"

??? Error using ==> mex

Unable to complete successfully


Error in ==> matlabrc at 197

mex -setup


/////// Lines added at the end of matlabrc so that Matlab recognizes a bookstore called Truetime   //////

disp('Bienvenidos. A trabajar con TrueTime.')
disp('Espere por favor ...')
addpath([getenv('TTKERNEL')])
init_truetime;
disp('Todo bien hasta aca ...');

mex -setup

make_truetime;

---

### Post by mips on 2008-06-03
You might get a better response in the Education & Science forum, [http://ubuntuforums.org/forumdisplay.php?f=169](http://ubuntuforums.org/forumdisplay.php?f=169)

---

### Post by Sef on 2008-06-03
> You might get a better response in the Education & Science forum, [http://ubuntuforums.org/forumdisplay.php?f=169](http://ubuntuforums.org/forumdisplay.php?f=169)

Agreed, so moved.

If you do find a post that you believe is in the wrong forum, just report it please.  Better than having an OP open a duplicate post.

---

### Post by mips on 2008-06-04
Edit: Never mind.

---

