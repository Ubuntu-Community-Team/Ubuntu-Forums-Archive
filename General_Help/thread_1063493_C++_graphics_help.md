---
title: "C++ graphics help"
date: 2009-02-07
forum: General Help
---

### Post by yosef on 2009-02-07
In university I am taking a class in C++.  I, ofcourse, use linux, specifically UNR 8.04 on a Sylvania G Meso.  My prof uses Visual C++ 2005 Express Edition to check our assignments.  This means that whatever sourcecode I write on Linux must also compile and run on Windows.  I am using gedit to write and g++ to compile... I need some kinds of graphics library that will compile on Linux and on Windows...  or some other suggestion...  all I really need is some very simple lines and shepes to be drawn, nothing fancy...  Anybody able to help me out here?

---

### Post by yosef on 2009-02-08
I am sorry, I should have posted this in Programming Talk.  But anyway... no suggestions?

---

### Post by mb_webguy on 2009-02-08
What about [wxWidgets]("http://www.wxwidgets.org/")?  It's in the repositories.  Just search Synaptic for wxwidgets.  There are multiple packages you'll need, though if you've already installed a C++ IDE of some sort, you may already have them installed.

---

### Post by yosef on 2009-02-08
So if I write something using wxwidgets classes, how do I then go about turning in an assignment that my prof can compile and run on windows?  Other than my source code what exactly do I need to give him?

---

### Post by gfulton on 2009-02-08
I would use opengl, it comes with linux and you need to link against only one or two libraries. Search for NeHe opengl tutorials and that should get you started with what you asked about in about 10 minutes. 

I assume you are using make to build your projects, if your professor is using this in VC Express you will be fine - otherwise you will have to convert your makefiles to whatever VC Express uses. You could install VC Express in wine or something perhaps, and check before handing in your assignments. 

-gf

---

### Post by mb_webguy on 2009-02-08
You just need to find out what libraries your professor has installed.  There are several cross-platform widget libraries available.  I think wxWidgets is easier to work with if you're just making a standard GUI app.  OpenGL is designed more towards 2D and 3D animation, but it's certainly an option.  Both are fairly common libraries to which your prof *may* have access.

---

### Post by yosef on 2009-02-11
Thank you for your help, I really appreciate the responses.  I am going to try for wxwidgets and I will install c++ express 2005 in wine so I can test my code as well.

---

