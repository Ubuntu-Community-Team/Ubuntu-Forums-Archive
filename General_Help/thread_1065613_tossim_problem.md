---
title: "tossim problem"
date: 2009-02-10
forum: General Help
---

### Post by ki_ha1984 on 2009-02-10
hi 
i am new in linux and i have to work on it because i am doing my post graduste project in w.s.n.   and tinyos  .

i install the tinyos like this [tutorial]("http://ubuntuforums.org/showthread.php?t=866248")  and when i run the tossim simulator  it tells the it successfuly (and the tossim cant create the main.exe file to run the gui )but i have this result : 

chairi@chairi-desktop:/opt/tinyos-2.1.0/apps/Blink$ make micaz simmkdir -p simbuild/micaz
placing object files in simbuild/micaz
writing XML schema to app.xml
compiling BlinkAppC to object file sim.o
ncc -c -shared -fPIC -o simbuild/micaz/sim.o -g -O0 -tossim -fnesc-nido-tosnodes=1000 -fnesc-simulate -fnesc-nido-motenumber=sim_node\(\) -Wall -Wshadow -Wnesc-all -target=micaz -fnesc-cfile=simbuild/micaz/app.c -board=micasb -DDEFINED_TOS_AM_GROUP=0x22 --param max-inline-insns-single=100000 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"chairi\" -DIDENT_HOSTNAME=\"chairi-desktop\" -DIDENT_USERHASH=0xbd195242L -DIDENT_TIMESTAMP=0x4990b98fL -DIDENT_UIDHASH=0x2293eefaL -Wno-nesc-data-race BlinkAppC.nc -fnesc-dump=components -fnesc-dump=variables -fnesc-dump=constants -fnesc-dump=typedefs -fnesc-dump=interfacedefs -fnesc-dump=tags -fnesc-dumpfile=app.xml
compiling Python support and C libraries into pytossim.o, tossim.o, and c-support.o
g++ -c -shared -fPIC -o simbuild/micaz/pytossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"chairi\" -DIDENT_HOSTNAME=\"chairi-desktop\" -DIDENT_USERHASH=0xbd195242L -DIDENT_TIMESTAMP=0x4990b98fL -DIDENT_UIDHASH=0x2293eefaL /opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx -I/usr/include/python2.5 -I/opt/tinyos-2.1.0/tos/lib/tossim -DHAVE_CONFIG_H
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_numVariables_set(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:1999: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2000: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_numVariables_get(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2066: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2067: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_variableNames_set(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2134: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2135: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_variableNames_get(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2202: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2203: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_variableTypes_set(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2270: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2271: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_variableTypes_get(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2338: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2339: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_variableArray_set(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2406: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2407: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_nesc_app_t_variableArray_get(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2474: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2475: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_delete_nesc_app_t(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2554: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2555: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_new_Mote(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2698: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2699: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx: In function ‘PyObject* _wrap_new_Tossim(PyObject*, PyObject*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2997: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx:2998: warning: deprecated conversion from string constant to ‘char*’
g++ -c -shared -fPIC -o simbuild/micaz/tossim.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"chairi\" -DIDENT_HOSTNAME=\"chairi-desktop\" -DIDENT_USERHASH=0xbd195242L -DIDENT_TIMESTAMP=0x4990b98fL -DIDENT_UIDHASH=0x2293eefaL /opt/tinyos-2.1.0/tos/lib/tossim/tossim.c -I/usr/include/python2.5 -I/opt/tinyos-2.1.0/tos/lib/tossim
/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c: In member function ‘variable_string_t Variable::getData()’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c:116: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c:117: warning: deprecated conversion from string constant to ‘char*’
/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c: In member function ‘Variable* Mote::getVariable(char*)’:
/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c:169: warning: deprecated conversion from string constant to ‘char*’
g++ -c -shared -fPIC -o simbuild/micaz/c-support.o -g -O0 -DIDENT_APPNAME=\"BlinkAppC\" -DIDENT_USERNAME=\"chairi\" -DIDENT_HOSTNAME=\"chairi-desktop\" -DIDENT_USERHASH=0xbd195242L -DIDENT_TIMESTAMP=0x4990b98fL -DIDENT_UIDHASH=0x2293eefaL /opt/tinyos-2.1.0/tos/lib/tossim/hashtable.c -I/usr/include/python2.5 -I/opt/tinyos-2.1.0/tos/lib/tossim
linking into shared object ./_TOSSIMmodule.so
g++ -shared -fPIC simbuild/micaz/pytossim.o simbuild/micaz/sim.o simbuild/micaz/tossim.o simbuild/micaz/c-support.o -lstdc++ -o _TOSSIMmodule.so
copying Python script interface TOSSIM.py from lib/tossim to local directory

*** Successfully built micaz TOSSIM library.
chairi@chairi-desktop:/opt/tinyos-2.1.0/apps/Blink$




any help ?

---

