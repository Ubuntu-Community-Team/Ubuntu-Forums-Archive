---
title: "Cantera CVS, Sundials and ubuntu 64 9.04"
date: 2009-07-21
forum: Education &amp; Science
---

### Post by vancheese on 2009-07-21
Hi people 

I was wondering if people have managed to install Cantera 1.7 from CVS on 64bit ubuntu. I've seen the problems in [http://ubuntuforums.org/showthread.php?t=1089975](http://ubuntuforums.org/showthread.php?t=1089975) and my problems are listed below

With the sundial option enabled I get the following error. (sundial is happily installed using checkinstall)

CVodesIntegrator.cpp: In constructor ‘Cantera::CVodesIntegrator::CVodesIntegrator()’:
CVodesIntegrator.cpp:111: error: ‘CV_SS’ was not declared in this scope
CVodesIntegrator.cpp: In member function ‘virtual void Cantera::CVodesIntegrator::setTolerances(double, int, double*)’:
CVodesIntegrator.cpp:153: error: ‘CV_SV’ was not declared in this scope
CVodesIntegrator.cpp: In member function ‘virtual void Cantera::CVodesIntegrator::setTolerances(double, double)’:
CVodesIntegrator.cpp:166: error: ‘CV_SS’ was not declared in this scope
CVodesIntegrator.cpp: In member function ‘void Cantera::CVodesIntegrator::sensInit(double, Cantera::FuncEval&)’:
CVodesIntegrator.cpp:233: error: ‘CVodeSensMalloc’ was not declared in this scope
CVodesIntegrator.cpp:238: error: ‘CV_SS’ was not declared in this scope
CVodesIntegrator.cpp:238: error: ‘CVodeSetSensTolerances’ was not declared in this scope
CVodesIntegrator.cpp: In member function ‘virtual void Cantera::CVodesIntegrator::initialize(double, Cantera::FuncEval&)’:
CVodesIntegrator.cpp:254: error: ‘CV_SV’ was not declared in this scope
CVodesIntegrator.cpp:264: error: ‘CV_SV’ was not declared in this scope
CVodesIntegrator.cpp:267: error: ‘CVodeMalloc’ was not declared in this scope
CVodesIntegrator.cpp:272: error: ‘CVodeMalloc’ was not declared in this scope
CVodesIntegrator.cpp:311: error: ‘CVodeSetFdata’ was not declared in this scope
CVodesIntegrator.cpp: In member function ‘virtual void Cantera::CVodesIntegrator::reinitialize(double, Cantera::FuncEval&)’:
CVodesIntegrator.cpp:343: error: ‘CV_SV’ was not declared in this scope
CVodesIntegrator.cpp:346: error: cannot convert ‘int (*)(realtype, _generic_N_Vector*, _generic_N_Vector*, void*)’ to ‘realtype’ for argument ‘2’ to ‘int CVodeReInit(void*, realtype, _generic_N_Vector*)’
CVodesIntegrator.cpp:351: error: cannot convert ‘int (*)(realtype, _generic_N_Vector*, _generic_N_Vector*, void*)’ to ‘realtype’ for argument ‘2’ to ‘int CVodeReInit(void*, realtype, _generic_N_Vector*)’
CVodesIntegrator.cpp: In member function ‘virtual void Cantera::CVodesIntegrator::integrate(double)’:
CVodesIntegrator.cpp:394: error: cannot convert ‘double’ to ‘realtype*’ for argument ‘2’ to ‘int CVodeGetSens(void*, realtype*, _generic_N_Vector**)’
make[2]: *** [CVodesIntegrator.o] Error 1



Being a Cantera newbie, I've not any experience in solving this problem and the online help is rather fragmented

Do people have any suggestions?

Andy

---

### Post by Anusiya on 2009-08-26
Hi vancheese,

Sorry for the delayed reply, but did you set all the parameters right in preconfig file? Also, if you had installed sundials through the repository, you have to pass additional compiler linkers like -I/usr/include/sundials and -L/usr/lib. Let me know if you need more help.

Anusiya

---

