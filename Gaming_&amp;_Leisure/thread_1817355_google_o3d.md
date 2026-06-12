---
title: "google o3d"
date: 2011-08-03
forum: Gaming &amp; Leisure
---

### Post by serghov on 2011-08-03
Hi. I am trying to install google o3d plugin on my ubuntu 11.04. 
I have tryed to build it, but I get this error 
```
breakpad/src/common/linux/file_id.cc: In member function ‘bool google_breakpad::FileID::ElfFileIdentifier(uint8_t*)’:
breakpad/src/common/linux/file_id.cc:132:20: error: ‘fstat’ was not declared in this scope
make[1]: *** [o3d/build/out/Debug/obj.target/breakpad_client/breakpad/src/common/linux/file_id.o] Error 1
make[1]: Leaving directory `/home/serg/o3d'
make: *** [all] Error 2
Traceback (most recent call last):
  File "/home/serg/o3d/o3d/gypbuild.py", line 291, in <module>
    main(sys.argv)
  File "/home/serg/o3d/o3d/gypbuild.py", line 288, in main
    GypBuilder(args[1:])
  File "/home/serg/o3d/o3d/gypbuild.py", line 270, in __init__
    func(targets, options)
  File "/home/serg/o3d/o3d/gypbuild.py", line 193, in Dobuild
    self.Execute(['make', '-f', solution])
  File "/home/serg/o3d/o3d/gypbuild.py", line 52, in Execute
    self.builder.Execute(args)
  File "/home/serg/o3d/o3d/gypbuild.py", line 282, in Execute
    raise RuntimeError("FAILED: " + " ".join(args))
RuntimeError: FAILED: make -f o3d_all.Makefile

```
can anyone tell me how to fix this problem?
or where to get the ready .deb package?

---

