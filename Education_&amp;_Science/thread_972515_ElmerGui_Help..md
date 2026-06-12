---
title: "ElmerGui Help."
date: 2008-11-05
forum: Education &amp; Science
---

### Post by GAMF on 2008-11-05
Hi there, 

I was wondering if any of you could compile ElmerGui.pro in ubuntu,if so could you help me out?

keen regards

---

### Post by Hyperion_1984 on 2008-12-03
I'm working on compiling ElmerGUI. I'll post it here if I find a way.

---

### Post by Hyperion_1984 on 2008-12-05
Hello, here's what I get when I try to compile ElmerGUI:

```
$ make
Makefile:8094: attention : écrasement des commandes pour la cible « meshtype.o »
Makefile:951: attention : anciennes commandes ignorées pour la cible « meshtype.o »
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Icad -Inetgen/libsrc/interface -Iplugins -Isrc -Ivtkpost -Imatc/src/elmer -Imatc/src -Imatc -Inetgen/libsrc/include -Inetgen/libsrc/csg -Inetgen/libsrc/linalg -Inetgen/libsrc/general -Inetgen/libsrc/gprim -Inetgen/libsrc/geom2d -Inetgen/libsrc/meshing -Inetgen/libsrc/stlgeom -Inetgen/libsrc/opti -I. -I. -o cadview.o cad/cadview.cpp
In file included from cad/cadview.cpp:44:
cad/cadview.h:51:28: error: TopoDS_Shape.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:46:24: error: QVTKWidget.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:47:25: error: vtkRenderer.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:48:29: error: vtkRenderWindow.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:49:22: error: vtkActor.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:50:23: error: vtkPoints.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:51:25: error: vtkTriangle.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:52:30: error: vtkDataSetMapper.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:53:32: error: vtkPolyDataNormals.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:54:29: error: vtkFeatureEdges.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:55:25: error: vtkProperty.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:56:27: error: vtkPropPicker.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:57:32: error: vtkCallbackCommand.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:58:31: error: vtkPolyDataMapper.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:59:31: error: vtkAppendPolyData.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:60:27: error: vtkFloatArray.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:61:30: error: vtkCleanPolyData.h: Aucun fichier ou dossier de ce type
cad/cadview.cpp:63:28: error: BRep_Builder.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:65:25: error: BRepTools.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:66:41: error: TopTools_HSequenceOfShape.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:67:24: error: BRepMesh.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:68:31: error: TopExp_Explorer.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:69:27: error: TopoDS_Face.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:70:22: error: TopoDS.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:71:25: error: BRep_Tool.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:72:34: error: Poly_Triangulation.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:73:33: error: GeomLProp_SLProps.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:74:34: error: STEPControl_Reader.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:75:34: error: IGESControl_Reader.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:76:23: error: Bnd_Box.hxx: Aucun fichier ou dossier de ce type
cad/cadview.cpp:77:26: error: BRepBndLib.hxx: Aucun fichier ou dossier de ce type
In file included from cad/cadview.cpp:44:
cad/cadview.h:94: erreur: ‘TopoDS_Shape’ does not name a type
cad/cadview.h:95: erreur: ‘TopoDS_Shape’ does not name a type
cad/cadview.h:96: erreur: ‘TopoDS_Shape’ does not name a type
cad/cadview.cpp:81: erreur: variable or field ‘pickEventHandler’ declared void
cad/cadview.cpp:81: erreur: ‘vtkObject’ was not declared in this scope
cad/cadview.cpp:81: erreur: ‘caller’ was not declared in this scope
cad/cadview.cpp:81: erreur: expected primary-expression before ‘unsigned’
cad/cadview.cpp:82: erreur: expected primary-expression before ‘void’
cad/cadview.cpp:82: erreur: expected primary-expression before ‘void’
make: *** [cadview.o] Erreur 1

```

It seems there's some problem to access the VTK librairy

---

### Post by baksiidaa on 2009-01-09
I just compiled the whole Elmer setup with only a couple problems in Intrepid 64.  I don't know if I can be of any help, but I wanted to let you know that it is possible.

---

### Post by Hyperion_1984 on 2009-02-24
> **baksiidaa said:**
> I just compiled the whole Elmer setup with only a couple problems in Intrepid 64.  I don't know if I can be of any help, but I wanted to let you know that it is possible.

Are you able to use OpenCASCADE with it?

---

### Post by aktawa on 2009-04-17
Hi,

I ran into the same problem.

After  I changed the line in the file ElmerGUI.pri:
```

OCC_INCLUDEPATH = /usr/include/opencascade

```

and qmake, make sequence, it compiled fine and opencascade import worked.

---

