---
title: "cvDestroyWindow in mex makes MATLAB crash"
date: 2009-06-03
forum: Education &amp; Science
---

### Post by Stoikheion on 2009-06-03
Hi all,

I'm using an installation of OpenCV in 32-bit 9.04 (as prescribed by [[COLOR="Blue"]http://gijs.pythonic.nl/blog/2009/may/3/getting-video-io-working-opencv-and-ubuntu-jaunty-/]("http://gijs.pythonic.nl/blog/2009/may/3/getting-video-io-working-opencv-and-ubuntu-jaunty-/")[/COLOR]) with MATLAB R2008a, and I'm trying to make a mex file with a C++ program written with OpenCV libraries. I'm using OpenCV HighGUI to open a window, display an image, then close it using cvDestroyWindow(), but when I compile the mex file with MATLAB and try to run the program, both the OpenCV window and MATLAB freeze at the cvDestroyWindow() part of the program.
It may be a larger problem with MATLAB interacting with HighGUI in general, I'm just not sure if anyone else has had this problem and if I should avoid using HighGUI in general. It's also possible my installation is bad if other people can use OpenCV windows with MATLAB, so any feedback would be appreciated. Thanks!

---

### Post by zeynab on 2009-06-11
I have another question from u:
how do you change mxarray to cvmat for using matrix in opencv function?
Thanks

---

### Post by Stoikheion on 2009-06-11
For converting from mxarrays to other formats (any input will be an mxarray), the most useful function that I've seen is mxGetPr ([http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/apiref/mxgetpr.html]("http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/apiref/mxgetpr.html")). Depending on what data type is in the mxarray (which MATLAB provides many functions for figuring out), you can access the elements of the mxarray by casting it to an array, such as a double* or a float*.
In the case of cvMat, you may have to navigate it opposite of mxArray (rows by columns vs. columns by rows), but once you use mxGetPr you can probably test it pretty easily from there.

If you can get the code to compile, you can also try this: [http://www.mathworks.com/matlabcentral/fileexchange/20927]("http://www.mathworks.com/matlabcentral/fileexchange/20927")

---

### Post by zeynab on 2009-06-13
thanks for your consideration:)
I couldn't run the example in mathwork site:(
If you can plz help me
there isn't any goog document...

---

### Post by Stoikheion on 2009-06-13
Which example did you try to run, the downloadable source code, or examples from the API on mxGetPr()?
If you can extract data from the mxArray, then putting it into an OpenCV data structure just depends on what kind of program you're making. I'm also new to OpenCV and MATLAB, so the best advice I can give you is to just make some intelligible output by using mxGetPr() on your mxArray, and try to figure out a pattern. If your mxArray represents an image, for example, then in general the functions in the MathWorks API will help you figure out if you're reading input correctly.

---

### Post by zeynab on 2009-06-14
> **Stoikheion said:**
> Which example did you try to run, the downloadable source code, or examples from the API on mxGetPr()?.
I try the downloadable source code
> **Stoikheion said:**
> If you can extract data from the mxArray, then putting it into an OpenCV data structure just depends on what kind of program you're making.I'm also new to OpenCV and MATLAB, so the best advice I can give you is to just make some intelligible output by using mxGetPr() on your mxArray, and try to figure out a pattern. 
At first I want to do this, but when I extarct data from mxarray by mxGetPr() I don't know how putting that into opencv data type!! could you give me piece of code about it?
At last how do you make opencv, matlab and visualc++ ready to work with each other? I use this document:
[http://www.mathworks.com/matlabcentral/fileexchange/21818](http://www.mathworks.com/matlabcentral/fileexchange/21818)
Thanks
Zeynab

---

### Post by sayok on 2009-11-24
Hi Stoikheion

I'm just having the same problem that you describe. As I use the cvDestroyWindow, both the opencv window and matlab crash. Have you found a workaround for ths issue?

Regards,

Sayok

---

