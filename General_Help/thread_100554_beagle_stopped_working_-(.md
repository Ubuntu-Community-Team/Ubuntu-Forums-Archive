---
title: "beagle stopped working :-("
date: 2005-12-07
forum: General Help
---

### Post by Trab on 2005-12-07
beagle worked perfectly for like 2 days... 

and now it doesnt :-/

best is started (sitting in the system tray) but searches return no hits... it says no results found... im searching for things i KNOW should have results...

beagled is running...

any help?

i tryined reinstalling from synaptic...

could it be a problem if sessions starts beagle on start up?

thanks

-Trab

ps it gives no error saying the daemon isnt running...


pps i killed beagled and tried best... it said daemon not running... i told it to start it... task manager says its started, but beagle disagress...

please help?

---

### Post by Appolusionist on 2005-12-08
[quote=Trab]beagle worked perfectly for like 2 days... 
 
and now it doesnt :-/
 
best is started (sitting in the system tray) but searches return no hits... it says no results found... im searching for things i KNOW should have results...
 
beagled is running...
 
any help?
 
i tryined reinstalling from synaptic...
 
could it be a problem if sessions starts beagle on start up?
 
thanks
 
-Trab
 
ps it gives no error saying the daemon isnt running...
 
 
pps i killed beagled and tried best... it said daemon not running... i told it to start it... task manager says its started, but beagle disagress...
 
please help?[/quote]
 
From Beagle's [website]("http://beaglewiki.org/Main_Page")...maybe this will help you out to check the logs or the output that is thrown out to see what is going on.
 
> Starting the Daemon
The daemon cannot be run with root, it is intended to run from your user account. To start a daemon in the background: 
$ beagledA daemon started in the background will log its progress to ~/.beagle/Log. 
You can also start a daemon in the foreground: 
$ beagled --fg --debugThis gives you some nice debugging output. 


---

