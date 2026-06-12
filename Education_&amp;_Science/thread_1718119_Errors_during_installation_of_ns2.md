---
title: "Errors during installation of ns2"
date: 2011-03-30
forum: Education &amp; Science
---

### Post by houss on 2011-03-30
**Errors during installation of ns2** 			
 			 			 		   		 		 		Hi all

I am new to linux and Im trying to install ns2.27  on my latop. I got the following error messages once i installed and  could not complete the process. Pleases suggest me on how to go from  here

============================================================
* Build Tclcl-1.15
============================================================
/include -I/home/houssem/ns-allinone-2.27-oolsr-0.99.15/include -o Tcl.o Tcl.cc
Tcl.cc: In member function ‘void Tcl::eval(char*)’:
Tcl.cc:180: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In member function ‘int TclObject::traceVar(const char*, TclObject*)’:
Tcl.cc:419: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In static member function ‘static int TclClass::create_shadow(void*, Tcl_Interp*, int, const char**)’:
Tcl.cc:507: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc:509: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In static member function ‘static int TclClass::dispatch_instvar(void*, Tcl_Interp*, int, const char**)’:
Tcl.cc:564: error: invalid conversion from ‘const char*’ to ‘char*’
Tcl.cc:569: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In member function ‘virtual void TclClass::bind()’:
Tcl.cc:601: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc:603: warning: deprecated conversion from string constant to ‘char*’
make: *** [Tcl.o] Error 1
tclcl-1.15 make failed! Exiting ...
See [http://www.isi.edu/nsnam/ns/ns-problems.html](http://www.isi.edu/nsnam/ns/ns-problems.html) for problems

---

