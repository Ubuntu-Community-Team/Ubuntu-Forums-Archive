---
title: "problem while running gazebo on ubuntu"
date: 2010-11-07
forum: Education &amp; Science
---

### Post by mizo_hazem_2 on 2010-11-07
**Hi**, 

I **have** a problem running gazebo 
I **have** completed building  gazebo, and everything was done  successfully according to the following link
[http://sourceforge.net/apps/mediawik...bot_Simulation]("http://sourceforge.net/apps/mediawiki/arsproject/index.php?title=Main_Page#ARS_-_Autonomous_Robot_Simulation")
, but when I tried to invoke  gazebo using the command "gazebo   /usr/local/share/gazebo/worlds/pioneer2dx.world" it returns the   following error 


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////  
**helkheer**@**helkheer**:~/gazebo-0.10.0$ gazebo  /usr/local/share/gazebo/worlds/pioneer2dx.world 
Gazebo multi-robot simulator, version 0.10.0 

Part of the Player/Stage Project [[**http**://playerstage.sourceforge.net]("http://playerstage.sourceforge.net/")].  
Copyright (C) 2003 Nate Koenig, Andrew **Howard**, and contributors. 
Released under the GNU General Public License. 

[/**home**/**helkheer**/gazebo-0.10.0/server/GazeboConfig.cc:103] 
  Gazebo Path[/usr/local/share/gazebo] 
[/**home**/**helkheer**/gazebo-0.10.0/server/GazeboConfig.cc:115] 
  Ogre Path[/usr/lib/OGRE] 
*** glibc detected *** gazebo: malloc(): memory corruption: 0x087e9b28  *** 
======= Backtrace: ========= 
/lib/libc.so.6(+0x6c501)[0x2482501] 
/lib/libc.so.6(+0x6f2fc)[0x24852fc] 
/lib/libc.so.6(__libc_malloc+0x63)[0x2486f33] 
/usr/lib/nvidia-current/libGL.so.1(+0x7e5e0)[0x85525e0]
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
I noticed that this error is appeared after installing NVIDIA  acceleraled graphics driver (version 173) 

while before installing it , running the command returns the following 
//////////////////////////////////////////////////////////////////////////////////////  

gazebo /usr/local/share/gazebo/worlds/pioneer2dx.world 
Gazebo multi-robot simulator, version 0.10.0 

Part of the Player/Stage Project [[**http**://playerstage.sourceforge.net]("http://playerstage.sourceforge.net/")].  
Copyright (C) 2003 Nate Koenig, Andrew **Howard**, and contributors. 
Released under the GNU General Public License. 

[/**home**/**helkheer**/gazebo-0.10.0/server/GazeboConfig.cc:103] 
  Gazebo Path[/usr/local/share/gazebo] 
[/**home**/**helkheer**/gazebo-0.10.0/server/GazeboConfig.cc:115] 
  Ogre Path[/usr/lib/OGRE] 
*** glibc detected *** gazebo: malloc(): memory corruption: 0x096a13e8  *** 
======= Backtrace: ========= 
/lib/libc.so.6(+0x6c501)[0x21ac501] 
/lib/libc.so.6(+0x6f2fc)[0x21af2fc] 
/lib/libc.so.6(__libc_malloc+0x63)[0x21b0f33] 
/usr/lib/libstdc++.so.6(_Znwj+0x29)[0x66b5619] 
/usr/lib/libstdc++.so.6(_Znaj+0x1d)[0x66b574d] 
gazebo(_ZN8Fl_Menu_4copyEPK12Fl_Menu_ItemPv+0x23)[0x807356d] 
/usr/local/lib/libgazebo_gui.so.0.10.0(_ZN6gazebo8MainMenuC1Eiiii   Pc+0x203)[0x96ea83] 
/usr/local/lib/libgazebo_gui.so.0.10.0(_ZN6gazebo3GuiC1EiiiiRKSs+   0x1f1)[0x965ff1] 
/usr/local/lib/libgazebo_server.so.0.10.0(_ZN6gazebo9Simulator4Lo   adERKSsj+0x40d)[0x87156d] 
gazebo(main+0x160)[0x805f650] 
/lib/libc.so.6(__libc_start_main+0xe7)[0x2156ce7] 
gazebo[0x805ee91] 
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
I'm using ubuntu  version 10.10
so can anyone **helping** me solving this problem 
thanks

---

