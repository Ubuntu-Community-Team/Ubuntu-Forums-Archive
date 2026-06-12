---
title: "Help with OpenCascade 6.2 on ubuntu hardy"
date: 2008-08-21
forum: Education &amp; Science
---

### Post by dheevatsa on 2008-08-21
Hi

I managed to install open cascade 6.2 on my unbuntu with the seetup.jar installer. Also I was able to run the configure and succesfull make the library (after adding the -ffriend-injection and -fpermissive options to CXX flags)

But now that I have done all this, I want to use this library to write a simple program (just for starters.)

code: 
------------------------------------------------------------------------
#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <STEPControl_Reader.hxx>
#include <TopoDS_Shape.hxx>
#include <BRepTools.hxx>
#include <XSControl_Reader.hxx>
#include <TopTools_SequenceOfShape.hxx>
#include <Handle_Standard_Transient.hxx>
#include <TColStd_SequenceOfTransient.hxx>


int main () {


STEPControl_Reader reader;

IFSelect_ReturnStatus stat = reader.ReadFile("screw.stp");


return 0;

}
-------------------------------------------------------------------------
to just to check the functionality !!

I am not able to to compile this code !!!

can anyone please tell me the how my makefile should look for this ??
what all should use as the include directories, which libraries I should be linking....??

can anyone please help me out with this...thanks a lot !!

---

