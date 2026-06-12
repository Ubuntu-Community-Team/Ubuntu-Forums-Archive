---
title: "Vegastrike Compiling Error"
date: 2005-10-23
forum: Gaming &amp; Leisure
---

### Post by subatomicdog on 2005-10-23
Everytime I attempt to compile the latest CVS of Vegastrike I get this error:

  Compiling vegastrike...
make  all-recursive
make[1]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike'
Making all in src
make[2]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/s rc'
Making all in cmd
make[3]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/s rc/cmd'
Making all in ai
make[4]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/s rc/cmd/ai'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT comm_ai.o -MD -MP -MF ".deps/comm_ai.Tpo" -c -o comm_ai.o  comm_ai.cpp; \
then mv -f ".deps/comm_ai.Tpo" ".deps/comm_ai.Po"; else rm -f ".deps/comm_ai.Tpo "; exit 1; fi
comm_ai.cpp: In function ‘void GetMadAt(Unit*, Unit*, int)’:
comm_ai.cpp:123: warning: converting to ‘int’ from ‘float’
comm_ai.cpp: In function ‘int InList(std::string, Unit*)’:
comm_ai.cpp:203: warning: converting to ‘int’ from ‘float’
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT docking.o -MD -MP -MF ".deps/docking.Tpo" -c -o docking.o  docking.cpp; \
then mv -f ".deps/docking.Tpo" ".deps/docking.Po"; else rm -f ".deps/docking.Tpo "; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT communication.o -MD -MP -MF ".deps/communication.Tpo" -c -o communication.o communication.cpp; \
then mv -f ".deps/communication.Tpo" ".deps/communication.Po"; else rm -f ".deps /communication.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT communication_xml.o -MD -MP -MF ".deps/communication_xml. Tpo" -c -o communication_xml.o communication_xml.cpp; \
then mv -f ".deps/communication_xml.Tpo" ".deps/communication_xml.Po"; else rm - f ".deps/communication_xml.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT event_xml.o -MD -MP -MF ".deps/event_xml.Tpo" -c -o event _xml.o event_xml.cpp; \
then mv -f ".deps/event_xml.Tpo" ".deps/event_xml.Po"; else rm -f ".deps/event_x ml.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT flybywire.o -MD -MP -MF ".deps/flybywire.Tpo" -c -o flyby wire.o flybywire.cpp; \
then mv -f ".deps/flybywire.Tpo" ".deps/flybywire.Po"; else rm -f ".deps/flybywi re.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT navigation.o -MD -MP -MF ".deps/navigation.Tpo" -c -o nav igation.o navigation.cpp; \
then mv -f ".deps/navigation.Tpo" ".deps/navigation.Po"; else rm -f ".deps/navig ation.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT ikarus.o -MD -MP -MF ".deps/ikarus.Tpo" -c -o ikarus.o ik arus.cpp; \
then mv -f ".deps/ikarus.Tpo" ".deps/ikarus.Po"; else rm -f ".deps/ikarus.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT fire.o -MD -MP -MF ".deps/fire.Tpo" -c -o fire.o fire.cpp ; \
then mv -f ".deps/fire.Tpo" ".deps/fire.Po"; else rm -f ".deps/fire.Tpo"; exit 1 ; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT fireall.o -MD -MP -MF ".deps/fireall.Tpo" -c -o fireall.o  fireall.cpp; \
then mv -f ".deps/fireall.Tpo" ".deps/fireall.Po"; else rm -f ".deps/fireall.Tpo "; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT hard_coded_scripts.o -MD -MP -MF ".deps/hard_coded_script s.Tpo" -c -o hard_coded_scripts.o hard_coded_scripts.cpp; \
then mv -f ".deps/hard_coded_scripts.Tpo" ".deps/hard_coded_scripts.Po"; else rm  -f ".deps/hard_coded_scripts.Tpo"; exit 1; fi
In file included from ../../../src/boost129/boost/config.hpp:35,
                 from ../../../src/boost129/boost/python/detail/config.hpp:15,
                 from ../../../src/boost129/boost/python/detail/prefix.hpp:14,
                 from ../../../src/boost129/boost/python/object.hpp:9,
                 from ../../../src/python/python_class.h:22,
                 from hard_coded_scripts.cpp:1:
../../../src/boost129/boost/config/compiler/gcc.hpp:92:7: warning: #warning "Unk nown compiler version - please run the configure tests and report the results"
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT order_comm.o -MD -MP -MF ".deps/order_comm.Tpo" -c -o ord er_comm.o order_comm.cpp; \
then mv -f ".deps/order_comm.Tpo" ".deps/order_comm.Po"; else rm -f ".deps/order _comm.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT order.o -MD -MP -MF ".deps/order.Tpo" -c -o order.o order .cpp; \
then mv -f ".deps/order.Tpo" ".deps/order.Po"; else rm -f ".deps/order.Tpo"; exi t 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT aggressive.o -MD -MP -MF ".deps/aggressive.Tpo" -c -o agg ressive.o aggressive.cpp; \
then mv -f ".deps/aggressive.Tpo" ".deps/aggressive.Po"; else rm -f ".deps/aggre ssive.Tpo"; exit 1; fi
aggressive.cpp: In member function ‘bool Orders::AggressiveAI::ProcessCurrentFgD irective(Flightgroup*)’:
aggressive.cpp:831: warning: converting to ‘int’ from ‘float’
aggressive.cpp:834: warning: converting to ‘int’ from ‘double’
aggressive.cpp:971: warning: converting to ‘int’ from ‘float’
aggressive.cpp:974: warning: converting to ‘int’ from ‘double’
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT script.o -MD -MP -MF ".deps/script.Tpo" -c -o script.o sc ript.cpp; \
then mv -f ".deps/script.Tpo" ".deps/script.Po"; else rm -f ".deps/script.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT missionscript.o -MD -MP -MF ".deps/missionscript.Tpo" -c -o missionscript.o missionscript.cpp; \
then mv -f ".deps/missionscript.Tpo" ".deps/missionscript.Po"; else rm -f ".deps /missionscript.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT tactics.o -MD -MP -MF ".deps/tactics.Tpo" -c -o tactics.o  tactics.cpp; \
then mv -f ".deps/tactics.Tpo" ".deps/tactics.Po"; else rm -f ".deps/tactics.Tpo "; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT turretai.o -MD -MP -MF ".deps/turretai.Tpo" -c -o turreta i.o turretai.cpp; \
then mv -f ".deps/turretai.Tpo" ".deps/turretai.Po"; else rm -f ".deps/turretai. Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT warpto.o -MD -MP -MF ".deps/warpto.Tpo" -c -o warpto.o wa rpto.cpp; \
then mv -f ".deps/warpto.Tpo" ".deps/warpto.Po"; else rm -f ".deps/warpto.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT flykeyboard.o -MD -MP -MF ".deps/flykeyboard.Tpo" -c -o f lykeyboard.o flykeyboard.cpp; \
then mv -f ".deps/flykeyboard.Tpo" ".deps/flykeyboard.Po"; else rm -f ".deps/fly keyboard.Tpo"; exit 1; fi
In file included from ../../../src/boost129/boost/config.hpp:35,
                 from ../../../src/boost129/boost/shared_ptr.hpp:18,
                 from ../../../src/networking/netclient.h:29,
                 from flykeyboard.cpp:9:
../../../src/boost129/boost/config/compiler/gcc.hpp:92:7: warning: #warning "Unk nown compiler version - please run the configure tests and report the results"
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT firekeyboard.o -MD -MP -MF ".deps/firekeyboard.Tpo" -c -o  firekeyboard.o firekeyboard.cpp; \
then mv -f ".deps/firekeyboard.Tpo" ".deps/firekeyboard.Po"; else rm -f ".deps/f irekeyboard.Tpo"; exit 1; fi
In file included from ../../../src/boost129/boost/config.hpp:35,
                 from ../../../src/boost129/boost/python/detail/config.hpp:15,
                 from ../../../src/boost129/boost/python/detail/prefix.hpp:14,
                 from ../../../src/boost129/boost/python/object.hpp:9,
                 from ../../../src/python/python_class.h:22,
                 from ../../../src/cmd/unit.cpp:49,
                 from ../../../src/cmd/unit.h:267,
                 from ../../../src/cmd/planet.h:10,
                 from firekeyboard.cpp:13:
../../../src/boost129/boost/config/compiler/gcc.hpp:92:7: warning: #warning "Unk nown compiler version - please run the configure tests and report the results"
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT flyjoystick.o -MD -MP -MF ".deps/flyjoystick.Tpo" -c -o f lyjoystick.o flyjoystick.cpp; \
then mv -f ".deps/flyjoystick.Tpo" ".deps/flyjoystick.Po"; else rm -f ".deps/fly joystick.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT input_dfa.o -MD -MP -MF ".deps/input_dfa.Tpo" -c -o input _dfa.o input_dfa.cpp; \
then mv -f ".deps/input_dfa.Tpo" ".deps/input_dfa.Po"; else rm -f ".deps/input_d fa.Tpo"; exit 1; fi
rm -f libai.a
ar cru libai.a comm_ai.o docking.o communication.o communication_xml.o event_xml .o flybywire.o navigation.o ikarus.o fire.o fireall.o hard_coded_scripts.o order _comm.o order.o aggressive.o script.o missionscript.o tactics.o turretai.o warpt o.o flykeyboard.o firekeyboard.o flyjoystick.o input_dfa.o
ranlib libai.a
rm -f libaiserver.a
ar cru libaiserver.a comm_ai.o docking.o communication.o communication_xml.o eve nt_xml.o flybywire.o navigation.o ikarus.o fire.o fireall.o hard_coded_scripts.o  order_comm.o order.o aggressive.o script.o missionscript.o tactics.o turretai.o  warpto.o
ranlib libaiserver.a
make[4]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/sr c/cmd/ai'
Making all in script
make[4]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/s rc/cmd/script'
Making all in c_alike
make[5]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/s rc/cmd/script/c_alike'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../../..   -I/usr/local/include  -I/usr/incl ude/python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../../src/boost129  -I. ./../../../src  -DBISON -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 - falign-functions=2  -pthread -pipe -MT c_alike.tab.o -MD -MP -MF ".deps/c_alike. tab.Tpo" -c -o c_alike.tab.o c_alike.tab.cpp; \
then mv -f ".deps/c_alike.tab.Tpo" ".deps/c_alike.tab.Po"; else rm -f ".deps/c_a like.tab.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../../..   -I/usr/local/include  -I/usr/incl ude/python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../../src/boost129  -I. ./../../../src  -DBISON -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 - falign-functions=2  -pthread -pipe -MT lex.yy.o -MD -MP -MF ".deps/lex.yy.Tpo" - c -o lex.yy.o lex.yy.cpp; \
then mv -f ".deps/lex.yy.Tpo" ".deps/lex.yy.Po"; else rm -f ".deps/lex.yy.Tpo"; exit 1; fi
rm -f libc_alike.a
ar cru libc_alike.a c_alike.tab.o lex.yy.o
ranlib libc_alike.a
make[5]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/sr c/cmd/script/c_alike'
make[5]: Entering directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/s rc/cmd/script'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT mission.o -MD -MP -MF ".deps/mission.Tpo" -c -o mission.o  mission.cpp; \
then mv -f ".deps/mission.Tpo" ".deps/mission.Po"; else rm -f ".deps/mission.Tpo "; exit 1; fi
In file included from ../../../src/boost129/boost/config.hpp:35,
                 from ../../../src/boost129/boost/python/detail/config.hpp:15,
                 from ../../../src/boost129/boost/python/detail/prefix.hpp:14,
                 from ../../../src/boost129/boost/python/object.hpp:9,
                 from ../../../src/python/python_class.h:22,
                 from mission.cpp:49:
../../../src/boost129/boost/config/compiler/gcc.hpp:92:7: warning: #warning "Unk nown compiler version - please run the configure tests and report the results"
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT mission_script.o -MD -MP -MF ".deps/mission_script.Tpo" - c -o mission_script.o mission_script.cpp; \
then mv -f ".deps/mission_script.Tpo" ".deps/mission_script.Po"; else rm -f ".de ps/mission_script.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../..   -I/usr/local/include  -I/usr/include /python2.4 -DHAVE_PYTHON=1  -DUSE_BOOST_131=1 -I../../../src/boost129  -I../../. ./src   -pipe  -O2 -ffast-math -falign-loops=2 -falign-jumps=2 -falign-functions =2  -pthread -pipe -MT pythonmission.o -MD -MP -MF ".deps/pythonmission.Tpo" -c -o pythonmission.o pythonmission.cpp; \
then mv -f ".deps/pythonmission.Tpo" ".deps/pythonmission.Po"; else rm -f ".deps /pythonmission.Tpo"; exit 1; fi
In file included from ../../../src/boost129/boost/config.hpp:35,
                 from ../../../src/boost129/boost/python/detail/config.hpp:15,
                 from ../../../src/boost129/boost/python/detail/prefix.hpp:14,
                 from ../../../src/boost129/boost/python/args.hpp:9,
                 from ../../../src/boost129/boost/python.hpp:12,
                 from ../../../src/python/init.h:10,
                 from pythonmission.cpp:7:
../../../src/boost129/boost/config/compiler/gcc.hpp:92:7: warning: #warning "Unk nown compiler version - please run the configure tests and report the results"
pythonmission.cpp: In destructor ‘virtual PythonMissionBaseClass::~PythonMission BaseClass()’:
pythonmission.cpp:19: error: cast from ‘PythonMissionBaseClass*’ to ‘unsigned in t’ loses precision
make[5]: *** [pythonmission.o] Error 1
make[5]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/sr c/cmd/script'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/sr c/cmd/script'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/sr c/cmd'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike/sr c'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/subatomicdog/vegastrike_cvs_head/vegastrike'
make: *** [all] Error 2
Error running 'make'




Anyone have any suggestions - I will post this to the Vegastrike forums when they are back up again.

Thank you,

subatomicdog

---

