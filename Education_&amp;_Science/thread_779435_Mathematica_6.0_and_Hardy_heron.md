---
title: "Mathematica 6.0 and Hardy heron"
date: 2008-05-02
forum: Education &amp; Science
---

### Post by anu7df on 2008-05-02
I recently upgraded to hardy (clean install) and since then I have been having a few problems with mathematica 6.0. The graphics display looks horrible and the label texts are unreadable. Also running mathematica from terminal gives a segmentation fault even though it continues to run after that and everything appears fine except for this graphics bug. I thought initially that this might be a font problem, so I downloaded the latest fonts from the mathematica website and added it to my font path but that didn't make a difference. Combing through the forums, I find a few other bug reports about invisible texts etc but nothing like what I am facing. has any one noticed such issues? I have attached an image with this post of a simple plot showing the problem.
Thanks 
Anu

---

### Post by BaffledMollusc on 2008-05-03
I had font problems and solved them by running mathematica with the -defaultvisual option. You could try that - it might help.

---

### Post by anu7df on 2008-05-03
> **BaffledMollusc said:**
> I had font problems and solved them by running mathematica with the -defaultvisual option. You could try that - it might help.

I had tried this already. It didn't help. I am guessing this is not just a font problem, as the font is visible, only with less "fidelity". 
Thanks
Anu

---

### Post by ravenon on 2008-05-05
On Launchpad 
[https://bugs.launchpad.net/bugs/197163](https://bugs.launchpad.net/bugs/197163)
A recent post suggests that the QT4 libraries supplied by Wolfram are incompatible with Hardy. It suggests removing

/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Libraries/Linux/libQtCore.so.4
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Libraries/Linux/libQtGui.so.4

Linux replaced with Linux-x86-64 on 64bit systems.

Starting with the usual command mathematica (as opposed to mathematica -defaultvisual) now provides perfect rendering of fonts in a notebook. I have reported this to Wolfram's support group.

---

### Post by aroch1 on 2008-05-20
Had this problem too, thanks a lot!

---

### Post by mikesf on 2008-05-28
after deleting libQtCore.so.4 and libQtGui.so.4 from mathematica directory, don't forget to install the libQt4Core and libQtGui4 from the repos (i.e. using apt-get or synaptic)
this fix works like a charm... i have beautiful fonts now!!! thanx for your help on this....

---

### Post by eldivertido on 2008-05-28
FWIW - deleting/replacing the Qt libs is not the best idea - Mathematica uses the commercial versions of the libraries, which may differ from the open source versions...

---

### Post by erdos on 2008-06-01
I think this type of problem can be overcome by using matlab.. If you are not familiar with matlab, then read online help of mathematica.. Hope you can rectify your problem..

=====
erdos

Put The Message Where It Matters! A New Way To Advertise On Social Networks! [http://www.widecircles.com]("http://www.widecircles.com")

---

### Post by PhDP on 2008-06-01
> **erdos said:**
> I think this type of problem can be overcome by using matlab.. If you are not familiar with matlab, then read online help of mathematica.. Hope you can rectify your problem..

=====
erdos

Put The Message Where It Matters! A New Way To Advertise On Social Networks! [http://www.widecircles.com]("http://www.widecircles.com")

To be fair, MatLab and Mathematica are very different program.

---

### Post by eotakos on 2008-07-01
for me the "-defaultvisual" option worked just fine! thank you very much BaffledMollusc!!

---

### Post by paolini on 2008-10-03
> **eotakos said:**
> for me the "-defaultvisual" option worked just fine! thank you very much BaffledMollusc!!

Hello I am using a Debian lenny and I have the same problems with fonts.
If I use mathematica -defaultvisual, the things work fine. But
if I remove the libQtCore.so.4 and libQtGui.so.4 from the Mathematica path
I get an error like this:

QObject: Do not delete object, 'unnamed', during its event handler!

and I have these libraries in the /usr/lib/.

I know that is not a Debian forum, but if someone has any idea I would be
thanks.

---

### Post by paulnation on 2008-10-06
I know that in Mathematica 6.03 the fonts/display issues in Ubuntu have been fixed.  If you can, get your hands on the update then everything will be worked out.  Not a fix but I hope it helps.

---

