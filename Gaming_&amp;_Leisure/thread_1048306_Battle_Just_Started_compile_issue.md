---
title: "Battle Just Started compile issue"
date: 2009-01-23
forum: Gaming &amp; Leisure
---

### Post by GoofusGreen on 2009-01-23
Hey everyone.

I tried compiling Battle Just Started, the tank game, and it's complaining about this line **std::auto_ptr<Model> mModel;** in the .h and **mModel = std::auto_ptr<Model>( new Model() );** in the .cpp

The compile instructions from readme are:
"make -s -k depend" which returns a bunch of missing .h files warnings
"make idl" is fine
"make -s" fails with a bunch of errors from the model_loader .h and .cpp files

```
 $ make -s
In file included from /usr/include/c++/4.3/ext/hash_map:64,
                 from ./src/common/hash_hack.h:10,
                 from src/common/model/model_loader.h:8,
                 from src/common/model/model_loader.cpp:1:
/usr/include/c++/4.3/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
In file included from src/common/model/model_loader.cpp:1:
src/common/model/model_loader.h:101: error: ISO C++ forbids declaration of ‘auto_ptr’ with no type
src/common/model/model_loader.h:101: error: invalid use of ‘::’
src/common/model/model_loader.h:101: error: expected ‘;’ before ‘<’ token
src/common/model/model_loader.cpp: In member function ‘Model* ModelLoader::loadModel(const std::string&)’:
src/common/model/model_loader.cpp:39: error: ‘mModel’ was not declared in this scope
src/common/model/model_loader.cpp:39: error: ‘auto_ptr’ is not a member of ‘std’
src/common/model/model_loader.cpp:39: error: expected primary-expression before ‘>’ token
make: *** [src/common/model/model_loader.o] Error 1

```

---

