---
title: "Makefile Error?"
date: 2009-06-19
forum: General Help
---

### Post by DedicatedOT on 2009-06-19
```

CFLAGS = -I. -I/usr/include/libxml2 -I/usr/include/lua5.1 -Werror -Wall -O1

LIBLINK = -L/usr/lib -lxml2 -lpthread -llua5.1 -lgmp -lmysqlclient -lboost_regex -lsqlite3 -llua5.1-sql-mysql -llua5.1-sql-sqlite -ldl -lboost_system

FLAGS = -D_THREAD_SAFE -D_REENTRANT -D__NO_HOMEDIR_CONF__ -D__USE_MYSQL__ -D__USE_SQLITE__

OBJ = account.o actions.o admin.o allocator.o ban.o baseevents.o beds.o creature.o creatureevent.o chat.o combat.o commands.o condition.o configmanager.o connection.o container.o cylinder.o database.o databasemysql.o databasesqlite.o depot.o exception.o fileloader.o game.o gui.o house.o housetile.o ioguild.o iologindata.o iomap.o iomapserialize.o inputbox.o item.o items.o logger.o luascript.o mailbox.o map.o md5.o monster.o monsters.o movement.o networkmessage.o npc.o otserv.o outfit.o outputmessage.o party.o player.o playerbox.o position.o protocol.o protocolgame.o protocollogin.o protocolold.o quests.o raids.o rsa.o scheduler.o scriptmanager.o server.o sha1.o spawn.o spells.o status.o talkaction.o tasks.o teleport.o textlogger.o thing.o tile.o tools.o trashholder.o vocation.o waitlist.o weapons.o 

**[COLOR=#a020f0]all:[/COLOR]** forgottenserver

**[COLOR=#a020f0]clean:[/COLOR]**
	rm -rf *.o

**[COLOR=#a020f0]forgottenserver:[/COLOR]** $(**[COLOR=#5f9ea0]OBJ[/COLOR]**)
	g++ $(**[COLOR=#5f9ea0]CFLAGS[/COLOR]**) $(**[COLOR=#5f9ea0]FLAGS[/COLOR]**) -o ./TheForgottenServer $(**[COLOR=#5f9ea0]OBJ[/COLOR]**) $(**[COLOR=#5f9ea0]LIBLINK[/COLOR]**)

    %.o:%.cpp
	g++ $(**[COLOR=#5f9ea0]CFLAGS[/COLOR]**) $(**[COLOR=#5f9ea0]FLAGS[/COLOR]**) -c $+

```

Then I get this error

```

root@vps:/sources/OTServ/0.2.3# make
g++ -I. -I/usr/include/libxml2 -I/usr/include/lua5.1 -Werror -Wall -O1 -D_THREAD     _SAFE -D_REENTRANT -D__NO_HOMEDIR_CONF__ -D__USE_MYSQL__ -D__USE_SQLITE__ -c adm     in.cpp
cc1plus: warnings being treated as errors
In file included from ./boost/asio/detail/select_interrupter.hpp:24,
                 from ./boost/asio/detail/epoll_reactor.hpp:42,
                 from ./boost/asio/impl/io_service.ipp:25,
                 from ./boost/asio/io_service.hpp:517,
                 from ./boost/asio/basic_io_object.hpp:20,
                 from ./boost/asio/basic_socket.hpp:20,
                 from ./boost/asio/basic_datagram_socket.hpp:25,
                 from ./boost/asio.hpp:18,
                 from connection.h:25,
                 from admin.cpp:24:
./boost/asio/detail/pipe_select_interrupter.hpp: In member function 'void boost:     :asio::detail::pipe_select_interrupter::interrupt()':
./boost/asio/detail/pipe_select_interrupter.hpp:74: error: ignoring return value      of 'ssize_t write(int, const void*, size_t)', declared with attribute warn_unus     ed_result
make: *** [admin.o] Error 1

```

Can you help please!

This is for Open Tibia server. Which can be found here:
[http://svn.otland.net/public/viewvc.cgi/tags/0.2.3/?root=forgottenserver](http://svn.otland.net/public/viewvc.cgi/tags/0.2.3/?root=forgottenserver)

---

### Post by 123456789123456789123456 on 2009-06-19
did you properly configure first?
./config

when building code, the frist steps are usually
./config
./make
make install

though make install sometimes are not needed
should be in documentation as which is actually needed
you also need to check all the dependences, the packages that the program may need in place and installed before the code can be complied and created to an executable install  program, and installed.
that is the problem with manually configuring source on Ubuntu.
look for all dependant files needed, get them installed first, by either apt-get install, or synaptic

---

### Post by DedicatedOT on 2009-06-19
When I say ./config or ./configure it says there's no such file.

But now I'm getting this

```


root@vps:/sources/OTServ/0.2.3# make
g++ -I. -I/usr/include/libxml2 -I/usr/include/lua5.1 -Werror -Wall -O1 -D_THREAD_SAFE -D_REENTRANT -D__NO_HOMEDIR_CONF__ -D__USE_MYSQL__ -o ./TheForgottenServer account.o actions.o admin.o allocator.o ban.o baseevents.o beds.o creature.o creatureevent.o chat.o combat.o commands.o condition.o configmanager.o connection.o container.o cylinder.o database.o databasemysql.o databasesqlite.o depot.o exception.o fileloader.o game.o gui.o house.o housetile.o ioguild.o iologindata.o iomap.o iomapserialize.o inputbox.o item.o items.o logger.o luascript.o mailbox.o map.o md5.o monster.o monsters.o movement.o networkmessage.o npc.o otserv.o outfit.o outputmessage.o party.o player.o playerbox.o position.o protocol.o protocolgame.o protocollogin.o protocolold.o quests.o raids.o rsa.o scheduler.o scriptmanager.o server.o sha1.o spawn.o spells.o status.o talkaction.o tasks.o teleport.o textlogger.o thing.o tile.o tools.o trashholder.o vocation.o waitlist.o weapons.o  -L/usr/lib -lxml2 -lpthread -llua5.1 -lgmp -lmysqlclient -lboost_regex -llua5.1-sql-mysql -ldl -lboost_system

```

---

### Post by DedicatedOT on 2009-06-19
And after I say make install, it creates:

TheForgottenServer, but when I say sh TheForgottenServer it says

```


root@vps:/sources/OTServ/0.2.3# TheForgottenServer
bash: TheForgottenServer: command not found
root@vps:/sources/OTServ/0.2.3# sh TheForgottenServer
TheForgottenServer: TheForgottenServer: cannot execute binary file


```

---

