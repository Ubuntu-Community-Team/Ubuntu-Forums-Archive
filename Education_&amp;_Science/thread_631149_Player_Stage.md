---
title: "Player Stage"
date: 2007-12-04
forum: Education &amp; Science
---

### Post by Princegiri on 2007-12-04
Alrite .... i hope someone can help me out of my misery here....

i sucessfully installed player stage from the .deb packages available on soundforge..... i ran the couple of examples too.. alls good.......

BUT i cant seem to compile any of the client codes...... 
there is a usr/share/player/examples/libplayerc++/laserobstacleavoid.cc

i cd'd to this directory
i tried to compile it as 
**$ g++ -o output laserobstacleavoid.cc **

the first error that pops out is
**laserobstacleavoid.cc:9:36: error: libplayerc++/playerc++.h: No such file or directory**

the includes in the code are
[B]
#include <libplayerc++/playerc++.h>
#include <iostream>[/B]

*i tried editing the code and  rewriting the includes as*
[B]
#include "usr/include/player-2.0/libplayerc++/playerc++.h"
#include <iostream>[/B]

this returns more problems with 
in file included from "usr//include/player-2.0/libplayerc++/playerc++.h" the following headers not  found
boost/signal.hpp>
boost/bind.hpp>
boost/thread/mutex.hpp>
boost/thread/thread.hpp>
boost/thread/xtime.hpp>

i have installed the BOOST C++
they have installed into the directory
usr/local/include/boost-1_34_1/boost
but the same problem persists.... 
none of the boost headers are detected

so here it is : im an absolute newbie.,...
i would appreciate any help on 'how-to-compile-anything'.... tutorials, pdfs anything.... 

i need to compile the client program and then try my hand at compiling one of my own client program in order for my project to proceed....

---

### Post by Sef on 2007-12-04
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by EXCiD3 on 2007-12-04
Do you need to use gmakemake in the folder to compile? Here is something i found in a Player/Stage FAQ:

> If you are developing code in C/C++ that must compile and link against the Player libraries, **and** you use gmakemake to generate your makefiles, you will need a copy of the header.mak file containing the compiling and linking flags.  From the directory in which you intend to run gmakemake:  cp /usr/local/pub/zjb/playerstage/header.mak ./header.mak
Looks like you need to execute that command and then run gmakemake in the folder the source is in. Info is taken from: [http://www.cs.rit.edu/usr/local/pub/FAQ/PlayerStage%20Setup.html]("http://www.cs.rit.edu/usr/local/pub/FAQ/PlayerStage%20Setup.html")

---

### Post by EXCiD3 on 2007-12-04
This looks helpful also: [http://playerstage.sourceforge.net/wiki/Player_and_Automake](http://playerstage.sourceforge.net/wiki/Player_and_Automake)

Sorry I couldnt find it earlier ;)

---

### Post by mgaut on 2008-05-07
Hi I am having this error when I try to compile some client code for playerstage

In file included from /usr/local/include/boost/signals/connection.hpp:13,
                 from /usr/local/include/boost/signals/signal_template.hpp:18,
                 from /usr/local/include/boost/signals/signal0.hpp:24,
                 from /usr/local/include/boost/signal.hpp:19,
                 from /usr/include/player-2.0/libplayerc++/playerclient.h:15,
                 from /usr/include/player-2.0/libplayerc++/playerc++.h:42,
                 from perception/Sensors.h:7,

.....
/usr/local/include/boost/signals/detail/signals_common.hpp:26: error: expected identifier before ‘protected’
/usr/local/include/boost/signals/detail/signals_common.hpp:26: error: expected unqualified-id before ‘protected’


Can anybody interpret this error and tell what the problem might be here?

---

