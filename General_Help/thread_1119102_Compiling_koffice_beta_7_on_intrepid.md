---
title: "Compiling koffice beta 7 on intrepid"
date: 2009-04-07
forum: General Help
---

### Post by lykwydchykyn on 2009-04-07
Has anyone successfully compiled koffice 2 beta 7 on Kubuntu intrepid?  I have all the build dependencies installed, but it dies during compilation with this error:
```

[ 46%] Building CXX object krita/image/CMakeFiles/kritaimage.dir/brushengine/kis_paint_information.o
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc:23: error: ‘EIGEN_MAKE_ALIGNED_OPERATOR_NEW’ does not name a type
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc: In constructor ‘KisPaintInformation::KisPaintInformation(const QPointF&, double, double, double, KisVector2D, double, double)’:
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc:43: error: ‘struct KisPaintInformation::Private’ has no member named ‘pos’
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc: In member function ‘const QPointF& KisPaintInformation::pos() const’:
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc:99: error: ‘struct KisPaintInformation::Private’ has no member named ‘pos’
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc: In member function ‘void KisPaintInformation::setPos(const QPointF&)’:
/home/alanm/packages/koffice-1.9.98.7/krita/image/brushengine/kis_paint_information.cc:104: error: ‘struct KisPaintInformation::Private’ has no member named‘pos’
make[2]: *** [krita/image/CMakeFiles/kritaimage.dir/brushengine/kis_paint_information.o] Error 1
make[1]: *** [krita/image/CMakeFiles/kritaimage.dir/all] Error 2
make: *** [all] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

