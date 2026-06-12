---
title: "Dolphin-emu build problems"
date: 2011-12-04
forum: Emulators
---

### Post by kung fu buntu on 2011-12-04
I'm trying to build it, but I'm having problems because I have cg installed at a non-default dir.

How can I edit CMakeLists.txt to instead of doing:
> check_lib(CG Cg Cg/cg.h)
check_lib(CGGL CgGL Cg/cgGL.h)
do something like this:
> add_include_dirs(/usr/local/nvidia-cg/include)
add_library_dirs(/usr/local/nvidia-cg/lib64)


I would also like to know if it's possible to have dolphin-emu to use a secondary GPU for computation instead of the main one.
Why?
Because I have 2 GPUs installed on my desktop and the one assigned to X is the least powerful one.

Thanks



EDIT: I'm using Debian so using the Ubuntu builds is not much of an option.
And in any case, solving this would make me understand more about cryptic cmake.




EDIT2: I solved this problem with env variables CMAKE_INCLUDE_PATH and CMAKE_LIBRARY_PATH

---

### Post by kung fu buntu on 2011-12-04
I'm now having another problem.

The link step fails:
> Linking CXX executable ../../../Binaries/dolphin-emu
/usr/bin/ld: cannot find -lCg
collect2: ld returned 1 exit status
make[2]: *** [Binaries/dolphin-emu] Error 1
make[1]: *** [Source/Core/DolphinWX/CMakeFiles/dolphin-emu.dir/all] Error 2
make: *** [all] Error 2
If I do it with make VERBOSE=1 I can see that cmake is not passing the appropriate -L path in the link command.
How can I do this?

---

### Post by thatguruguy on 2011-12-17
Is there a reason you want to build it rather than install it from a ppa?

---

