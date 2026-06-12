---
title: "error building kicad (ubuntu 8.04)"
date: 2009-02-03
forum: General Help
---

### Post by garuhhh on 2009-02-03
hi all! i'm building kicad, using cmake 2.6.0-5, installed all dependencies, and i keep on getting this error..

> garu@garu-laptop:~/downloads/kicad$ fakeroot debian/rules binary
/usr/bin/make -C /home/garu/downloads/kicad/build/kicad
make[1]: Entering directory `/home/garu/downloads/kicad/build/kicad'
make[2]: Entering directory `/home/garu/downloads/kicad/build/kicad'
make[3]: Entering directory `/home/garu/downloads/kicad/build/kicad'
make[3]: Leaving directory `/home/garu/downloads/kicad/build/kicad'
make[3]: Entering directory `/home/garu/downloads/kicad/build/kicad'
[  0%] Building CXX object 3d-viewer/CMakeFiles/3d-viewer.dir/3d_aux.cpp.o
In file included from /usr/include/boost/ptr_container/ptr_sequence_adapter.hpp:20,
                 from /usr/include/boost/ptr_container/ptr_vector.hpp:20,
                 from /home/garu/downloads/kicad/kicad/include/board_item_struct.h:9,
                 from /home/garu/downloads/kicad/kicad/include/pcbstruct.h:9,
                 from /home/garu/downloads/kicad/kicad/3d-viewer/3d_viewer.h:29,
                 from /home/garu/downloads/kicad/kicad/3d-viewer/3d_aux.cpp:23:
/usr/include/boost/ptr_container/detail/reversible_ptr_container.hpp:38:48: error: boost/serialization/split_member.hpp: No such file or directory
In file included from /usr/include/boost/ptr_container/ptr_sequence_adapter.hpp:20,
                 from /usr/include/boost/ptr_container/ptr_vector.hpp:20,
                 from /home/garu/downloads/kicad/kicad/include/board_item_struct.h:9,
                 from /home/garu/downloads/kicad/kicad/include/pcbstruct.h:9,
                 from /home/garu/downloads/kicad/kicad/3d-viewer/3d_viewer.h:29,
                 from /home/garu/downloads/kicad/kicad/3d-viewer/3d_aux.cpp:23:
/usr/include/boost/ptr_container/detail/reversible_ptr_container.hpp:610: error: expected ‘;’ before ‘}’ token
/usr/include/boost/ptr_container/detail/reversible_ptr_container.hpp:610: error: expected `;' before ‘}’ token
In file included from /home/garu/downloads/kicad/kicad/include/board_item_struct.h:9,
                 from /home/garu/downloads/kicad/kicad/include/pcbstruct.h:9,
                 from /home/garu/downloads/kicad/kicad/3d-viewer/3d_viewer.h:29,
                 from /home/garu/downloads/kicad/kicad/3d-viewer/3d_aux.cpp:23:
/usr/include/boost/ptr_container/ptr_vector.hpp:70: error: expected ‘;’ before ‘}’ token
/usr/include/boost/ptr_container/ptr_vector.hpp:70: error: expected `;' before ‘}’ token
make[3]: *** [3d-viewer/CMakeFiles/3d-viewer.dir/3d_aux.cpp.o] Error 1
make[3]: Leaving directory `/home/garu/downloads/kicad/build/kicad'
make[2]: *** [3d-viewer/CMakeFiles/3d-viewer.dir/all] Error 2
make[2]: Leaving directory `/home/garu/downloads/kicad/build/kicad'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/garu/downloads/kicad/build/kicad'
make: *** [build-arch-stamp] Error 2
garu@garu-laptop:~/downloads/kicad$ 



by the way, i'm following this [page]("http://kicad.sourceforge.net/wiki/index.php/Build_System").

thanks for any help.

---

### Post by garuhhh on 2009-02-04
richard burton (the one who maintains the Debian build source and builds the official Debian packages) responded to me, and told me to install libboost-serialization-dev.
> 
Try installing package libboost-serialization-dev. libboost-dev
depends on it on Debian, but for some unknown reason does not depend
on it on ubuntu.

and it worked!! haha

i have now a newly compiled kicad :D

---

