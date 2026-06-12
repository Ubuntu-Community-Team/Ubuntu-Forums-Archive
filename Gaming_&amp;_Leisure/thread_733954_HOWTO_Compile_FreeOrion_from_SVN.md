---
title: "HOWTO: Compile FreeOrion from SVN"
date: 2008-03-24
forum: Gaming &amp; Leisure
---

### Post by Achetar on 2008-03-24
**WARNING: THE LATEST SVN WILL NOT COMPILE ON UBUNTU. There is thread on the FreeOrion forums where you can get static linux builds of the latest release (3.8,39.4.0,etc). Please go there.**

Okay, this is one sore area for an otherwise great project. It is nearly impossible to compile FreeOrion from SVN. I finally (after 3 weeks) figured it out. Here is a guide for it.

First you need to install some dependencies through synaptic:

Gutsy:
```
sudo apt-get install python scons libfreetype6-dev bcp libdevil-dev libsdl1.2-dev libsdl-mixer1.2-dev graphviz-dev liblog4cpp4 liblog4cpp4-dev libogre-dev libois-dev libopenal-dev

```Hardy:
```

sudo apt-get install python scons libfreetype6-dev bcp libdevil-dev libsdl1.2-dev libsdl-mixer1.2-dev graphviz-dev liblog4cpp5 liblog4cpp5-dev libogre-dev libois-dev libopenal-dev

```Next, you need to download the SVN of FreeOrion from Sourceforge.
```
svn co https://freeorion.svn.sourceforge.net/svnroot/freeorion/trunk freeorion

```It will ask you if you want to accept a key, **accept it or FreeOrion will not download**.

After that, go into the directory where you downloaded Freeorion (usually just ~/freeorion). You need to go into the FreeOrion/GG subdirectory in order to compile GG
```

cd ./freeorion/FreeOrion/GG

```Enter the following command:
```

scons

```If the configuration says it will not compile one of the components, immediately stop the compilation with Ctrl+4 so you can find and install any missing dependencies. If you have to stop it at that point you will have to run the following to reconfigure before attempting again.
```

scons configure

```After it finishes compiling, use the following command to install it.
```

sudo scons install

```Enter your password and continue.

Next go back to the FreeOrion directory using this command:
```

cd ..

```Then we need to edit the UI/TechTreeWnd.cpp file. Unfortunately this has to be done every time you run 'svn update'. Add the following lines right after the #include <algorithm> line:
```

#ifndef M_PI
#define M_PI      3.14159265358979323846
#endif

#ifndef PI
#define PI      M_PI
#endif

#define POINTS_PER_INCH   72
#define POINTS(f_inch)   (ROUND((f_inch)*POINTS_PER_INCH))
#define PS2INCH(ps)      ((ps)/(double)POINTS_PER_INCH)

```Then exit the editor and go back to the FreeOrion directory
Run the following command:
```

scons

```The GiGiSDL >= 0.6.0 check always comes out to no, no matter what you do. Ignore it.

Once again, if any other checks come out to no, immediately stop the compile with Ctrl+4 and install any missing dependencies. After stopping it with Ctrl+4 you have to run the following command before attempting again:
```

scons compile

```After awhile it will error out when trying to compile to the output file 'freeoriond'. Use the following command to make freeoriond compile.
```

g++ -o freeoriond -pthread combat/Combat.o Empire/Empire.o Empire/EmpireManager.o Empire/ResourcePool.o network/Message.o network/MessageQueue.o network/Networking.o network/boost/error_code.o UI/StringTable.o universe/Building.o universe/Condition.o universe/ConditionParser1.o universe/ConditionParser2.o universe/ConditionParser.o universe/Effect.o universe/EffectParser.o universe/Enums.o universe/Fleet.o universe/Meter.o universe/ParserUtil.o universe/Planet.o universe/PopCenter.o universe/Predicates.o universe/ResourceCenter.o universe/Ship.o universe/ShipDesign.o universe/Special.o universe/System.o universe/Tech.o universe/TopLevelParsers.o universe/UniverseObject.o universe/ValueRef.o universe/ValueRefParser.o util/DataTable.o util/GZStream.o util/MultiplayerCommon.o util/OptionsDB.o util/Order.o util/OrderSet.o util/Process.o util/Random.o util/Serialize.o util/SitRepEntry.o util/VarText.o util/Version.o util/binreloc.o util/Directories.o util/XMLDoc.o combat/CombatSystem-server.o network/ServerNetworking-server.o server/SaveLoad-server.o server/ServerApp-server.o server/ServerFSM-server.o server/dmain-server.o universe/Universe-server.o util/AppInterface-server.o -L/usr/lib -L/usr/lib/lib -lpython2.5 -lboost_serialization -lboost_iostreams -lboost_python -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lSDL -lpthread -lz -lfreetype -lIL -lILU -lILUT -lalut -lopenal -lvorbisfile -lvorbis -lm -logg -lgvc -lgraph -lcdt -llog4cpp -lnsl -llog4cpp -lGiGi -lGiGiSDL

```(DO NOT try to type that all out, copy and paste it)

Then run the following command:
```

scons freeorionca

```After awhile it will error out, use this command to make it compile:
```

g++ -o freeorionca -pthread combat/Combat.o Empire/Empire.o Empire/EmpireManager.o Empire/ResourcePool.o network/Message.o network/MessageQueue.o network/Networking.o network/boost/error_code.o UI/StringTable.o universe/Building.o universe/Condition.o universe/ConditionParser1.o universe/ConditionParser2.o universe/ConditionParser.o universe/Effect.o universe/EffectParser.o universe/Enums.o universe/Fleet.o universe/Meter.o universe/ParserUtil.o universe/Planet.o universe/PopCenter.o universe/Predicates.o universe/ResourceCenter.o universe/Ship.o universe/ShipDesign.o universe/Special.o universe/System.o universe/Tech.o universe/TopLevelParsers.o universe/UniverseObject.o universe/ValueRef.o universe/ValueRefParser.o util/DataTable.o util/GZStream.o util/MultiplayerCommon.o util/OptionsDB.o util/Order.o util/OrderSet.o util/Process.o util/Random.o util/Serialize.o util/SitRepEntry.o util/VarText.o util/Version.o util/binreloc.o util/Directories.o util/XMLDoc.o client/ClientApp-ai.o client/ClientFSMEvents-ai.o client/AI/AIClientApp-ai.o client/AI/camain-ai.o network/ClientNetworking-ai.o universe/Universe-ai.o util/AppInterface-ai.o AI/AIInterface-ai.o AI/PythonAI-ai.o python/PythonEnumWrapper-ai.o python/PythonUniverseWrapper-ai.o python/PythonEmpireWrapper-ai.o python/PythonLoggingWrapper-ai.o -L/usr/lib -L/usr/lib/lib -lpython2.5 -lboost_serialization -lboost_iostreams -lboost_python -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lSDL -lpthread -lz -lfreetype -lIL -lILU -lILUT -lalut -lopenal -lvorbisfile -lvorbis -lm -logg -lgvc -lgraph -lcdt -llog4cpp -lnsl -llog4cpp -lGiGi -lGiGiSDL

```Then, finally, run the following command:
```

scons freeorion

```This will error out with far more errors than either of the previous ones. Use the following command to make it compile:
```

g++ -o freeorion -pthread combat/Combat.o Empire/Empire.o Empire/EmpireManager.o Empire/ResourcePool.o network/Message.o network/MessageQueue.o network/Networking.o network/boost/error_code.o UI/StringTable.o universe/Building.o universe/Condition.o universe/ConditionParser1.o universe/ConditionParser2.o universe/ConditionParser.o universe/Effect.o universe/EffectParser.o universe/Enums.o universe/Fleet.o universe/Meter.o universe/ParserUtil.o universe/Planet.o universe/PopCenter.o universe/Predicates.o universe/ResourceCenter.o universe/Ship.o universe/ShipDesign.o universe/Special.o universe/System.o universe/Tech.o universe/TopLevelParsers.o universe/UniverseObject.o universe/ValueRef.o universe/ValueRefParser.o util/DataTable.o util/GZStream.o util/MultiplayerCommon.o util/OptionsDB.o util/Order.o util/OrderSet.o util/Process.o util/Random.o util/Serialize.o util/SitRepEntry.o util/VarText.o util/Version.o util/binreloc.o util/Directories.o util/XMLDoc.o client/ClientApp-human.o client/ClientFSMEvents-human.o client/human/HumanClientFSM-human.o client/human/HumanClientApp-human.o client/human/HumanClientAppSoundOpenAL-human.o client/human/chmain-human.o network/ClientNetworking-human.o UI/About-human.o UI/BuildDesignatorWnd-human.o UI/ClientUI-human.o UI/CUIControls-human.o UI/CUIDrawUtil-human.o UI/CUIStyle-human.o UI/CUIWnd-human.o UI/FleetButton-human.o UI/FleetWnd-human.o UI/GalaxySetupWnd-human.o UI/InGameMenu-human.o UI/InfoPanels-human.o UI/IntroScreen-human.o UI/LinkText-human.o UI/CombatWnd-human.o UI/MapWnd-human.o UI/MultiplayerLobbyWnd-human.o UI/OptionsWnd-human.o UI/DesignWnd-human.o UI/ProductionWnd-human.o UI/ResearchWnd-human.o UI/ServerConnectWnd-human.o UI/SidePanel-human.o UI/SitRepPanel-human.o UI/SystemIcon-human.o UI/TechTreeWnd-human.o UI/TurnProgressWnd-human.o universe/Universe-human.o util/AppInterface-human.o UI/EncyclopediaDetailPanel-human.o -L/usr/lib -L/usr/lib/lib -lpython2.5 -lboost_serialization -lboost_iostreams -lboost_python -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lSDL -lpthread -lz -lfreetype -lIL -lILU -lILUT -lalut -lopenal -lvorbisfile -lvorbis -lm -logg -lgvc -lgraph -lcdt -llog4cpp -lnsl -llog4cpp -lGiGi -lGiGiSDL

```Running 'sudo scons install' will not work because it tries to recompile freeoriond, freeorionca, and freeorion with the original non-working commands.

To run freeorion, use the following command:
```

./freeorion

```I tested this guide on an Ubuntu Hardy Beta i386 computer.

Hope this helps!

---

### Post by BlackBoots on 2008-03-29
Thank you very much for the great post.  It has gotten me farther than any other walk through/Help I have tried.  But when i get to the point of  running scons, this is what I get.
```

-linux:~/freeorion/FreeOrion$ scons
scons: Reading SConscript files ...
Using previous successful configuration; if you want to re-run the configuration step, run "scons configure".
scons: done reading SConscript files.
scons: Building targets ...
scons: `freeoriond' is up to date.
scons: `freeorionca' is up to date.
g++ -o UI/TechTreeWnd-human.o -c -pthread -g -O2 -Wall -D_GNU_SOURCE=1 -D_REENTRANT -DFREEORION_LINUX -DENABLE_BINRELOC -DFREEORION_BUILD_HUMAN -DGL_GLEXT_PROTOTYPES -I/usr/include/python2.5 -I/usr/local/include -I/usr/include/SDL -I/usr/include/graphviz -Inetwork UI/TechTreeWnd.cpp
g++ -o freeorion -pthread combat/Combat.o Empire/Empire.o Empire/EmpireManager.o Empire/ResourcePool.o network/Message.o network/MessageQueue.o network/Networking.o network/boost/error_code.o UI/StringTable.o universe/Building.o universe/Condition.o universe/ConditionParser1.o universe/ConditionParser2.o universe/ConditionParser.o universe/Effect.o universe/EffectParser.o universe/Enums.o universe/Fleet.o universe/Meter.o universe/ParserUtil.o universe/Planet.o universe/PopCenter.o universe/Predicates.o universe/ResourceCenter.o universe/Ship.o universe/ShipDesign.o universe/Special.o universe/System.o universe/Tech.o universe/TopLevelParsers.o universe/UniverseObject.o universe/ValueRef.o universe/ValueRefParser.o util/DataTable.o util/GZStream.o util/MultiplayerCommon.o util/OptionsDB.o util/Order.o util/OrderSet.o util/Process.o util/Random.o util/Serialize.o util/SitRepEntry.o util/VarText.o util/Version.o util/binreloc.o util/Directories.o util/XMLDoc.o client/ClientApp-human.o client/ClientFSMEvents-human.o client/human/HumanClientFSM-human.o client/human/HumanClientApp-human.o client/human/HumanClientAppSoundOpenAL-human.o client/human/chmain-human.o network/ClientNetworking-human.o UI/About-human.o UI/BuildDesignatorWnd-human.o UI/ClientUI-human.o UI/CUIControls-human.o UI/CUIDrawUtil-human.o UI/CUIStyle-human.o UI/CUIWnd-human.o UI/FleetButton-human.o UI/FleetWnd-human.o UI/GalaxySetupWnd-human.o UI/InGameMenu-human.o UI/InfoPanels-human.o UI/IntroScreen-human.o UI/LinkText-human.o UI/CombatWnd-human.o UI/MapWnd-human.o UI/MultiplayerLobbyWnd-human.o UI/OptionsWnd-human.o UI/DesignWnd-human.o UI/ProductionWnd-human.o UI/ResearchWnd-human.o UI/ServerConnectWnd-human.o UI/SidePanel-human.o UI/SitRepPanel-human.o UI/SystemIcon-human.o UI/TechTreeWnd-human.o UI/TurnProgressWnd-human.o universe/Universe-human.o util/AppInterface-human.o UI/EncyclopediaDetailPanel-human.o -L/usr/lib -L/usr/local/lib -lpython2.5 -lGiGiSDL -lIL -lILU -lGiGi -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lfreetype -lz -lSDL -lboost_serialization -lboost_iostreams -lboost_python -lalut -lopenal -lvorbisfile -lvorbis -lm -logg -lgraph -lcdt -lgvc -llog4cpp -lnsl -llog4cpp
client/human/HumanClientApp-human.o: In function `HumanClientApp::HandleSystemEvents()':
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:477: undefined reference to `GG::SDLGUI::HandleSystemEvents()'
client/human/HumanClientApp-human.o: In function `~HumanClientApp':
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:137: undefined reference to `GG::SDLGUI::~SDLGUI()'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:137: undefined reference to `GG::SDLGUI::~SDLGUI()'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:137: undefined reference to `GG::SDLGUI::~SDLGUI()'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:137: undefined reference to `GG::SDLGUI::~SDLGUI()'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:137: undefined reference to `GG::SDLGUI::~SDLGUI()'
client/human/HumanClientApp-human.o:/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:137: more undefined references to `GG::SDLGUI::~SDLGUI()' follow
client/human/HumanClientApp-human.o: In function `HumanClientApp':
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:105: undefined reference to `GG::SDLGUI::SDLGUI(int, int, bool, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:134: undefined reference to `GG::SDLGUI::~SDLGUI()'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:105: undefined reference to `GG::SDLGUI::SDLGUI(int, int, bool, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/shawn/freeorion/FreeOrion/client/human/HumanClientApp.cpp:134: undefined reference to `GG::SDLGUI::~SDLGUI()'
client/human/HumanClientApp-human.o: (.rodata._ZTV14HumanClientApp[vtable for HumanClientApp]+0x6c): undefined reference to `GG::SDLGUI::Ticks() const'
client/human/HumanClientApp-human.o: (.rodata._ZTV14HumanClientApp[vtable for HumanClientApp]+0x70): undefined reference to `GG::SDLGUI::AppWidth() const'
client/human/HumanClientApp-human.o: (.rodata._ZTV14HumanClientApp[vtable for HumanClientApp]+0x74): undefined reference to `GG::SDLGUI::AppHeight() const'
client/human/HumanClientApp-human.o: (.rodata._ZTV14HumanClientApp[vtable for HumanClientApp]+0x9c): undefined reference to `GG::SDLGUI::RenderEnd()'
client/human/HumanClientApp-human.o: (.rodata._ZTV14HumanClientApp[vtable for HumanClientApp]+0xa0): undefined reference to `GG::SDLGUI::Run()'
client/human/HumanClientApp-human.o: (.rodata._ZTI14HumanClientApp[typeinfo for HumanClientApp]+0x18): undefined reference to `typeinfo for GG::SDLGUI'
client/human/HumanClientAppSoundOpenAL-human.o:(.rodata._ZTV25HumanClientAppSoundOpenAL[vtable for HumanClientAppSoundOpenAL]+0x6c): undefined reference to `GG::SDLGUI::Ticks() const'
client/human/HumanClientAppSoundOpenAL-human.o:(.rodata._ZTV25HumanClientAppSoundOpenAL[vtable for HumanClientAppSoundOpenAL]+0x70): undefined reference to `GG::SDLGUI::AppWidth() const'
client/human/HumanClientAppSoundOpenAL-human.o:(.rodata._ZTV25HumanClientAppSoundOpenAL[vtable for HumanClientAppSoundOpenAL]+0x74): undefined reference to `GG::SDLGUI::AppHeight() const'
client/human/HumanClientAppSoundOpenAL-human.o:(.rodata._ZTV25HumanClientAppSoundOpenAL[vtable for HumanClientAppSoundOpenAL]+0x9c): undefined reference to `GG::SDLGUI::RenderEnd()'
client/human/HumanClientAppSoundOpenAL-human.o:(.rodata._ZTV25HumanClientAppSoundOpenAL[vtable for HumanClientAppSoundOpenAL]+0xa0): undefined reference to `GG::SDLGUI::Run()'
client/human/chmain-human.o: In function `main':
/home/shawn/freeorion/FreeOrion/client/human/chmain.cpp:83: undefined reference to `GG::SDLGUI::operator()()'
UI/DesignWnd-human.o: In function `DesignWnd::BaseSelector::DoLayout()':
/home/shawn/freeorion/FreeOrion/UI/DesignWnd.cpp:959: undefined reference to `GG::TabWnd::CurrentWndIndex() const'
collect2: ld returned 1 exit status
scons: *** [freeorion] Error 1
scons: building terminated because of errors.
```


I then try running the commands scons freeorion and then the long one after that and i receive the same error.

I am running on Gutsy and GiGi compiled fine

Any help would be appreciated.

thanks.

---

### Post by Achetar on 2008-05-16
Unfortunately the latest SVN is now broken on Linux and I havent gotten it to recompile yet. I geuss I should tell people that. Unfortunately I don't know what revision I built at. THere is a guy who has a static build of v3.9 on the FreeOrion forums. It works well. I would recommend downloading that. But I'm just working on the AI so I don't need to be able to build the source because the AI is python.

---

