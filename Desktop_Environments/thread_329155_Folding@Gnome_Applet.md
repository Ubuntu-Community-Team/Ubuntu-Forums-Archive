---
title: "Folding@Gnome Applet"
date: 2007-01-01
forum: Desktop Environments
---

### Post by ruudiculus on 2007-01-01
Hi there,

I wrote a Folding@Gnome Applet (GTK2) to graphically view the folding process and to manage your preferences (such as name, team etc.).

Since it is the first time I wrote an applet (a Bonobo-component to be exact) and I'm not a programming expert, some bugs may remain. Please mail me those bugs/strange behaviour or post a message on this very thread.

There's a [wiki]("https://help.ubuntu.com/community/FoldingAtHome") (and [this guide]("http://ubuntuforums.org/showthread.php?t=101817&highlight=Folding%40Home")) for installing the Folding@Home executable and join the Ubuntu Folding@Home team. However if you install the Folding@Home executable as proposed it may not work together with the Folding@Gnome Applet, since the applet tries to execute an already running Folding@Home. Such situations remain to be tested. (It will NEVER screw up your computer, but if it makes you feel more safe, save a copy of the Folding@Home "client.cfg" file after you first configured things)

Anyway, if you download Folding@Gnome, there's my own small howto as well that you can use that should work fine. (The Ubuntu Folding team number should be copied from the wiki above). Furthermore this applet will not work for PPC and amd64, since I haven't yet compiled it for PPC and since there's no Folding@Home core for amd64 (the SMP core doesn't work...). So, it is an i386 Applet only for now.

As you can see on my [website]("http://www.ruudbeukema.nl") I keep a "to-do" list of features that aren't implemented yet. If you have any suggestions regarding these or new features I would be glad to read them! Again: post them here or mail me!

Well, that's all I think... Hmm, yes some other thing: the source code. It is under GNU/GPL license and I will put the source code on the website for downloading after I reorganise the code a bit (Something went wrong during the Unified Process I guess :D : or should I say I'm still iterating...).

That's all for now! The current version is "1.0 (testing)". Any updates will be announced here... Have fun folding!

Btw: you can download it [here]("http://www.ruudbeukema.nl/index.php?page=fag_applet").

---

### Post by smbm on 2007-01-06
Hi

First of all thanks for taking the time to write an applet for this.

I do have a couple of (possibly very silly, please excuse my ignorance) questions though:

In your readme file you mention to:

"3.	The first line of the [email]Folding@Gnome.conf[/email] file should point to the path you
	put this applet in (So, excluding the executable)."

This file doesn't seem to be included as standard though. Do I need to create it? If so is that the only line that needs to be in it?

In the above post you also mention that:

"if you install the Folding@Home executable as proposed it may not work together with the Folding@Gnome Applet"

Does this mean that if I install via the method mentioned in the wiki that the chances are your applet won't work? If so can you explain how I would go about getting things running again?

Thanks again for taking the time to write this, sorry to be taking some of it up with these questions.

---

### Post by ruudiculus on 2007-01-11
Hi smbm,

I indeed forgot to add the FoldingAtGnome.conf file. It is in the tar.gz package now. Sorry for that confusion.

The problem you can get with that wiki is that the Folding@Home executable is started during boot time. When launching the Folding@Gnome applet it tries to run the Folding@Home executable (that already runs since boot time).

What I expect is that the first Folding@Home will keep on running, while the second will not proceed and stops with a warning (not visible to the user) like "There's a Folding@Home already running, I will not proceed". Apart from that the Folding@Gnome applet will still read the Folding@Home files, so the progress should still be monitored.

I haven't thoroughly checked this situation however, so what might happen is that the applet quits immediately. You will however never harm the Folding@Home files nor your system.

I will automatically check on running Folding@Home processes in a next Folding@Gnome release, but that'll could take a while since I currently am very busy with school. ;) 

If you have more ideas, please don't hesitate and post them here.

Ruud

---

### Post by ruudiculus on 2007-01-11
Folding@Gnome 1.16 can be downloaded now. Changes compared to 1.15:
[LIST=1]
[*]Folding@Home executable is restarted with new settings after changing (and saving) them
[*]Folding@Home executable stops running when Folding@Gnome applet does
[/LIST]

For an updated Folding@Gnome todo-list  look at my website. If you have more ideas, please let me know...

---

### Post by jpkotta on 2007-01-19
> **ruudiculus said:**
> 
What I expect is that the first Folding@Home will keep on running, while the second will not proceed and stops with a warning (not visible to the user) like "There's a Folding@Home already running, I will not proceed". Apart from that the Folding@Gnome applet will still read the Folding@Home files, so the progress should still be monitored.


I am the author of the wiki scripts (which I'm calling fah_install).  I had to go out of my way to make sure there are no other clients running, and in fact I do different tests to see.  You can see what I do to check in the init script.  You can run as many clients as you want, but it is recommended that you only run as many as physical CPUs (as in CPU cores, not chips) because faster results are more useful.  This is why I tried to associate the client to the machine rather than a user, because there may be more than one user logged in.

---

### Post by ruudiculus on 2007-01-20
At the moment I have the problem of not being able to run the applet anymore. I don't know why; could be some Bonobo error (since V1.15 doesn't work either). When I have fixed that I will read your scripts and intergrate some things.

What I question is if you can run multiple instances of the F@H-Core. When, some months ago, I tried to run a second instance of F@H-Core (Version 504) it said it had detected a second process running and wouldn't continue. Maybe running more than one instance IS possible when putting each executable in it's own folder, so that it has its own work folder. Well, I haven't experimented with this, so I'm probably wrong. In that case my applet should be a bit more dynamic, so that it can display multiple progress bars :) 

I'll let you know when I've read your scripts!

P.S. Anyone else experiencing a failure in running the applet? (I don't know if I did some relevant update lately)

---

### Post by jpkotta on 2007-01-20
> **ruudiculus said:**
> 
What I question is if you can run multiple instances of the F@H-Core. 


In my experience, yes, albeit indirectly.  FahCore is lauched by FAH502-Linux.  Usually, there are 4 Cores launched.  I think these are different threads, with one thread handling the folding and the others doing other less important tasks.  You can run FAH502-Linux several times as long as you give each instance a different machineid.  I think this implies different configuration files for each one.  I remember having problems when I ran FAH502-Linux several times, and it probably shouldn't be done without different machineids.

---

### Post by ruudiculus on 2007-01-21
OK, so this means currently my applet doesn't support monitoring multiple folding processes.  I added the idea to support monitoring multiple folding processes to the to-do list.

Now it is only a matter of time for me to have time :) 

Regarding the *not being able to run the applet anymore*-problem:
There was a bug in the applet, which will be corrected in V1.17. It concerned the client.cfg file, which suddenly had a new parameter called **local=** ](*,) . While parsing this file things went wrong. V1.17 should be downloadable a few moments from now.

* zipping, copying... *

---

### Post by ruudiculus on 2007-01-22
V1.18 is downloadable now: saving the settings from applet to *client.cfg* file of course had the same bug as parsing the file. This is now fixed.

---

### Post by ruudiculus on 2007-01-26
The Folding@Home executable (504) runs properly on my x86_64 system. This is why I compiled a Folding@Gnome Applet for amd64, that is able to monitor the Folding@Home progress done by the 32-bit Folding@Home executable.

Enjoy, 64-bit users...
:guitar:

---

### Post by ruudiculus on 2007-02-09
The next Folding@Gnome version (V 1.19) will be ready for download somewhere in the week of Feb 12. It will (at least) include:

1. bug-fixes
2. auto-installer script
3. A button to open your personal statistics page in your default web browser.
4. It will be able to detect an already running Folding@Home process

Monitoring multiple Folding@Home processes will not yet be implemented (maybe in V1.20). V.1.19 will be available for x86 and x86_64.

Happy Folding!

---

### Post by ruudiculus on 2007-02-16
Folding@Gnome version 1.19 can now be downloaded from [www.ruudbeukema.nl](www.ruudbeukema.nl)!!

The issues in the previous post are implemented in this version: nothing more nothing less. You can now independently run Folding@Home and the Folding@Gnome applet if you want, as long as you have not more than one Folding@Home process to monitor.

Since monitoring multiple Folding@Home processes basically means writing the applet again from ground up, this could take a while.

Enjoy!

---

### Post by tomplast on 2007-02-20
Nice app though when I tried to add the applet my gnome-panel crashes (and reappears after a few seconds) and when I close the bugreporting dialog that comes up gnome-panel crashes again :/. I have had the same problem before so perhaps your applet may have something todo with it *-).


You got any ideas how to fix it (I don't want to create a new profile as I did last time). Thank you for any assistance.


EDIT:

I solved it by simple deleting the folder where I installed it :).

---

### Post by ruudiculus on 2007-02-20
Ah fine!

Currently, the applet can only run and monitor one Folding@Home process. When you have two or more Folding@Home executables on your system with the same version (5.04), yet in different directories it could be that the applet can't properly choose one. Same holds for the applet: keep only one Folding@Gnome executable on your system.

---

### Post by ruudiculus on 2007-02-23
Folding@Gnome V1.20 is out! ([www.ruudbeukema.nl](www.ruudbeukema.nl))

No new features, only some improvements on stability.

Have fun watching the progress...
:popcorn:

---

### Post by D!mon on 2007-02-24
Hi!

I've just tried to install your applet but without any success :(
I'm running F@H SMP (maybe that's the reason?) on my AMD 64 x2 4200 (Folding@Gnome V1.20 (x86_64) version, Ubuntu 6.10_64) and when I try to add F@G applet to panel it says 
The panel encountered a problem while loading "OAFIID:GNOME_FoldingAtGnome".

---

### Post by ruudiculus on 2007-02-24
I'm not able to test it on SMP machines so F@G currently only supports F@H 5.04, not the SMP client (5.91?)

I could make it work for you (and other SMP users), if you give me the name of the F@H executable you use. I can't discover the name because the installer (fah5) doesn't work here. It would also be nice if you and/or other SMP users would volunteer in testing future SMP F@G's. Please [mail me]("http://www.ruudbeukema.nl/index.php?page=mailme") for that.

Running multiple instances of F@H isn't supported yet,  so you can't run F@G together with 2 F@H's. If you want to run F@G on your SMP machine immediately, you could try to rename the F@H-executable to **FAH504-Linux.exe** and run only one. Maybe that way you can fool F@G to monitor your F@H progress. (Doing this actually is the same as installing the non-SMP 5.04 F@H executable)

SMP users, please let me know if you want to test a F@G executable every once in a while...

---

### Post by D!mon on 2007-03-07
Haven't time to look at this topic before.. I will give you the name of executable once I'll get to my home computer (possibly will email you)
But actually it is one from 5.91 archive (fah5 as I remember)
I don't think that running 5.04 version and waste SMP power is a good idea; but having SMP F@G monitoring will be great!

---

### Post by D!mon on 2007-03-09
F@H is started with the following commands on my computer:
sudo sh -c "cd /home/dimon/Folding@Home/FAH_SMP_Linux; ./fah5 -local -forceasm -verbosity 9"
Actually this is the same as 5.04 non-SMP version isn't it?

---

### Post by ruudiculus on 2007-03-09
Well not exactly. I also 'cd' to the right directory and then execute **./FAH504-Linux.exe** instead of **./fah5**

If you want to use the F@G applet to monitor just one folding process I can alter the program relatively easy, but when you have multiple folding processes running on your SMP you'll have to wait until I have time to implement the monitoring of multiple folding processes.

Let me know how you use F@H on your SMP machine so that I may change things...

Cheers,

---

### Post by D!mon on 2007-03-09
hm, I don't have another F@H executables except fah5;
The way I use it is that I just start it with the command from my previous post and then it is running:)
There are 4 F@H processes in ps -ef output

---

### Post by ruudiculus on 2007-03-11
OK, that's the info I needed :) 

F@H indeed starts 4 subprocesses called FahCore here. But for me the **fah5** is most important...

I'll come back here when I have a SMP version of F@G

---

### Post by jcwinnie on 2007-03-17
Since I have been unable to understand how to get it to work, how do I remove the applet from the choices provided for the Gnome panel?

---

### Post by ruudiculus on 2007-03-18
Hi jcwinnie,

A pitty that it didn't work for you. In order for me to learn from you, you could provide me with a little story about why it didn' t work, what you have tried etc. and maybe you can send me the F@G log-file. Nevertheless below is how to remove F@G from your system.

(I' m on a non-Linux PC right now, so I' ll answer as best as I can)

For the applet to be unloaded from your panel, you can click the option 'remove from panel'. In order to completely get rid of the F@G applet you'll have to remove files in the following locations:

You' ll have three locations containing F@G files:
[LIST=1]
[*]Its icon will be in the **/usr/share/pixmaps** directory
[*]The program itself will be in a directory known to you (since you put it there)
[*]The applet script file (Named something like GNOME_Factory_FoldingAtGnome) will be located in **/usr/lib/bonobo/servers**
[/LIST]

---

### Post by dmoney on 2007-03-27
The i386 version crashes gnome-panel. Here's the output. It crashes, outputs a bug report, reload gnome-panel and crashes, ad infinitum. Had to chmod -x the applet executable to stop the cycle. 
```
Memory status: size: 18735104 vsize: 0 resident: 18735104 share: 0 rss: 6955008 rss_rlim: 0
CPU usage: start_time: 1175019357 rtime: 0 utime: 9 stime: 0 cutime:8 cstime: 0 timeout: 1 it_real_value: 0 frequency: 17

Backtrace was generated from '/usr/libexec/The Folding@Gnome Applet'

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1224967808 (LWP 30012)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb74a4323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f581b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb73bb1b1 in fwrite () from /lib/tls/i686/cmov/libc.so.6
#5  0x0804ab6a in initApplet () at main.c:113
#6  0x0804aee0 in fahApplet (applet=0x809e000, 
    iid=0x80bd560 "OAFIID:GNOME_FoldingAtGnome", data=0x0) at main.c:264
#7  0xb7f987fe in panel_applet_marshal_BOOLEAN__STRING ()
   from /usr/lib/libpanel-applet-2.so.0
#8  0xb75df79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#9  0xb7671d84 in bonobo_closure_invoke_va_list ()
   from /usr/lib/libbonobo-2.so.0
#10 0xb7671fec in bonobo_closure_invoke () from /usr/lib/libbonobo-2.so.0
#11 0xb7f974a6 in panel_applet_add_preferences ()
   from /usr/lib/libpanel-applet-2.so.0
#12 0xb75ecb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#13 0xb75df79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#14 0xb75efb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#15 0xb75f10b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#16 0xb75f1279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#17 0xb7eb086b in bonobo_control_add_listener ()
   from /usr/lib/libbonoboui-2.so.0
#18 0xb7674bc1 in _ORBIT_skel_small_Bonobo_Control_setFrame ()
   from /usr/lib/libbonobo-2.so.0
#19 0xb759eb07 in IOP_start_profiles () from /usr/lib/libORBit-2.so.0
#20 0xb75a4c75 in ORBit_OAObject_invoke () from /usr/lib/libORBit-2.so.0
#21 0xb7591dbc in ORBit_small_invoke_adaptor () from /usr/lib/libORBit-2.so.0
#22 0xb75a2916 in ORBit_recv_buffer_return_sys_exception ()
   from /usr/lib/libORBit-2.so.0
#23 0xb75a2fc2 in ORBit_recv_buffer_return_sys_exception ()
   from /usr/lib/libORBit-2.so.0
#24 0xb75a3a33 in ORBit_skel_class_register () from /usr/lib/libORBit-2.so.0
#25 0xb75a4e12 in ORBit_handle_request () from /usr/lib/libORBit-2.so.0
#26 0xb758e077 in giop_connection_handle_input ()
   from /usr/lib/libORBit-2.so.0
#27 0xb75aba1d in link_connection_state_changed ()
   from /usr/lib/libORBit-2.so.0
#28 0xb75ae9ce in link_io_add_watch_fd () from /usr/lib/libORBit-2.so.0
#29 0xb74d6802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#30 0xb74d97df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#31 0xb74d9b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#32 0xb765fa23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
#33 0xb765dc89 in bonobo_generic_factory_main_timeout ()
   from /usr/lib/libbonobo-2.so.0
#34 0xb765dd13 in bonobo_generic_factory_main ()
   from /usr/lib/libbonobo-2.so.0
#35 0xb7f93ad1 in panel_applet_factory_main_closure ()
   from /usr/lib/libpanel-applet-2.so.0
#36 0xb7f93bb5 in panel_applet_factory_main ()
   from /usr/lib/libpanel-applet-2.so.0
#37 0x0804b0c1 in main (argc=-1219931872, argv=0xb7495120) at main.c:304

Thread 1 (Thread -1224967808 (LWP 30012)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74a4323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f581b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb73bb1b1 in fwrite () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0x0804ab6a in initApplet () at main.c:113
No locals.
#6  0x0804aee0 in fahApplet (applet=0x809e000, 
    iid=0x80bd560 "OAFIID:GNOME_FoldingAtGnome", data=0x0) at main.c:264
	systray_icon = <value optimized out>
	event_box = <value optimized out>
#7  0xb7f987fe in panel_applet_marshal_BOOLEAN__STRING ()
   from /usr/lib/libpanel-applet-2.so.0
No symbol table info available.
#8  0xb75df79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb7671d84 in bonobo_closure_invoke_va_list ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#10 0xb7671fec in bonobo_closure_invoke () from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#11 0xb7f974a6 in panel_applet_add_preferences ()
   from /usr/lib/libpanel-applet-2.so.0
No symbol table info available.
#12 0xb75ecb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb75df79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb75efb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb75f10b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb75f1279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb7eb086b in bonobo_control_add_listener ()
   from /usr/lib/libbonoboui-2.so.0
No symbol table info available.
#18 0xb7674bc1 in _ORBIT_skel_small_Bonobo_Control_setFrame ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#19 0xb759eb07 in IOP_start_profiles () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#20 0xb75a4c75 in ORBit_OAObject_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#21 0xb7591dbc in ORBit_small_invoke_adaptor () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#22 0xb75a2916 in ORBit_recv_buffer_return_sys_exception ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#23 0xb75a2fc2 in ORBit_recv_buffer_return_sys_exception ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#24 0xb75a3a33 in ORBit_skel_class_register () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#25 0xb75a4e12 in ORBit_handle_request () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#26 0xb758e077 in giop_connection_handle_input ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#27 0xb75aba1d in link_connection_state_changed ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#28 0xb75ae9ce in link_io_add_watch_fd () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#29 0xb74d6802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#30 0xb74d97df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#31 0xb74d9b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#32 0xb765fa23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#33 0xb765dc89 in bonobo_generic_factory_main_timeout ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#34 0xb765dd13 in bonobo_generic_factory_main ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#35 0xb7f93ad1 in panel_applet_factory_main_closure ()
   from /usr/lib/libpanel-applet-2.so.0
No symbol table info available.
#36 0xb7f93bb5 in panel_applet_factory_main ()
   from /usr/lib/libpanel-applet-2.so.0
No symbol table info available.
#37 0x0804b0c1 in main (argc=-1219931872, argv=0xb7495120) at main.c:304
	program = (GnomeProgram *) 0x80507ec
	retval = <value optimized out>
#0  0xffffe410 in __kernel_vsyscall ()

```

---

### Post by ruudiculus on 2007-03-29
:confused: 

Do you mean that when you '**chmod +x**'-ed te F@G executable the applet DID appear on the panel after all?

---

### Post by chewearn on 2007-04-09
hi
I have installed F@H using the fah_install method; FAH502-Linux.exe began to run without problem.

Then, I installed fag_appletv1.20.  Installation also completed without problem, but when I tried to add the applet on the Gnome Panel, I got this error message:
The panel encountered a problem while loading "OAFIID:GNOME_FoldingAtGnome".

---

### Post by ruudiculus on 2007-04-09
Today would be a good day to get behind my computer and take a look at the problem you have. However, since Debian Etch is out, I'll be busy installing and configuring a new system.

What I'll do for now is send you a link to F@G Version 1.19, maybe that fixes things for you for the time being. V1.19 is on my other computer so not within reach now. I'll put it on my website this afternoon...

Happy Easter!

P.S. Could you send me the F@G log file? It may be of any help tracking the bug

---

### Post by ruudiculus on 2007-04-09
> **ruudiculus said:**
> What I'll do for now is send you a link to F@G Version 1.19, maybe that fixes things for you for the time being. V1.19 is on my other computer so not within reach now. I'll put it on my website this afternoon...

Sorry, I haven't got any earlier versions of F@G and V1.20 should run fine. Please send me your F@G log file (its in the F@G directory, together with the executable)

What kind of system do you have? 32-bit / 64-bit / 64-bit SMP? And what kind of F@H are you using? (an executable name would be nice)

---

### Post by chewearn on 2007-04-09
It's a 32-bit generic 6.10 Edgy on a 5-year-old Celeron system.  I mentioned the executable "FAH502-Linux.exe" in my previous post, but let me reconfirm that. :)

Currently, I am away from the system, will get back to you with the F@G log tomorrow.

It's not urgent. I am currently using a simple shell script to show the F@H logs (it runs "sudo ./foldingathome status" and output via a zenity info window).  But I just thought I help feedback on F@G.

---

### Post by chewearn on 2007-04-10
Ok, I have confirmed the F@H executable is "FAH502-Linux.exe".

I could find the log for F@G.  I installed it in /opt/foldingatgnome directory.  There are four files in it:
> myuser@myuser-desktop:/opt/foldingatgnome$ ls -l
total 152
-rwxr-xr-x 1 root root 135643 2007-04-09 13:52 fah_applet
-rwxr-xr-x 1 root root   1509 2007-04-09 13:52 FoldingAtGnome_22x22.png
-rw-r--r-- 1 root root     20 2007-04-09 13:52 [email]Folding@Gnome.conf[/email]
-rw-r--r-- 1 root root   1270 2007-04-09 13:52 GNOME_FoldingAtGnome_Factory.server
myuser@myuser-desktop:/opt/foldingatgnome$ 


---

### Post by ruudiculus on 2007-04-10
Hmm, there should be a *.log file in that directory. It seems that F@G isn't started at all.

The **GNOME_FoldingAtGnome_Factory.server** file in that directory is a copy of the one that is copied to */usr/lib/bonobo/servers* directory, so you could check if the **location** parameter points to your **/opt/foldingatgnome** directory (or maybe **/opt/foldingatgnome/fah_applet**; I'm at work, so I can not tell for sure now).

If this isn't the case you could change it to **/opt/foldingatgnome** or **/opt/foldingatgnome/fah_applet**

Let me know if this makes any sense... :)

---

### Post by chewearn on 2007-04-10
It's correct.  Here is the content of
 */usr/lib/bonobo/servers/*GNOME_FoldingAtGnome_Factory.server

> 
<oaf_info>
    <oaf_server iid="OAFIID:GNOME_FoldingAtGnome_Factory" type="exe"
            location="/opt/foldingatgnome/fah_applet">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:Bonobo/GenericFactory:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="Folding@Gnome Applet"/>
        <oaf_attribute name="description" type="string" value="The Folding@Gnome applet"/>
    </oaf_server>

    <oaf_server iid="OAFIID:GNOME_FoldingAtGnome" type="factory"
            location="OAFIID:GNOME_FoldingAtGnome_Factory">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
                <item value="IDL:Bonobo/Control:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="Folding@Gnome Applet"/>
        <oaf_attribute name="description" type="string" value="Folding@Gnome Applet"/>
        <oaf_attribute name="panel:category" type="string" value="Bio-Informatics"/>
        <oaf_attribute name="panel:icon" type="string" value="FoldingAtGnome_48x48.png"/>
    </oaf_server>
</oaf_info>

Now, the situation has gotten worst; when I tried to add the applet to the panel, I got the Bug Buddy window; which keep reappearing (I have to kill gnome-panel to recover).  Not sure if it would help, but I attach the Bug Buddy error file.

---

### Post by ruudiculus on 2007-04-10
The bug report doesn't make any sense to me unfortunately. I only know that the first thing F@G does during execution is making a log-file. Have you set all permissions right? I guess you run F@G as a normal user. Is your **/opt/foldingatgnome** directory accessable for a normal user? - you could try and install foldingatgnome in your home directory. If it's not an permission issue it shouldn't run then either...

Else I'm out of ideas really :(

---

### Post by chewearn on 2007-04-11
Ok, thanks anyway.  Installed F@G using root/sudo.  Will try it using normal user when I got the chance.

---

### Post by blackwell on 2007-04-11
i got this same problem i got error when i try to add to panel your applet :(

in [email]Folding@Gnome.log[/email] i got only this:
"[Folding@Gnome log]
Info:"

---

### Post by richardjennings on 2007-04-17
I tried installing. I currently trying to get out of a seemiongly infinate bug report loop. Here is the bug report:

Memory status: size: 53088256 vsize: 0 resident: 53088256 share: 0 rss: 11456512 rss_rlim: 0
CPU usage: start_time: 1176827930 rtime: 0 utime: 30 stime: 0 cutime:28 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1224972624 (LWP 8380)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb767d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f751b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7565770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7566ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7781122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7781159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77811d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7855790 in ORBit_RootObject_duplicate_T ()
   from /usr/lib/libORBit-2.so.0
#11 0xb785f5d8 in CORBA_any__freekids () from /usr/lib/libORBit-2.so.0
#12 0xb785a7da in CORBA_exception__copy () from /usr/lib/libORBit-2.so.0
#13 0xb785a867 in CORBA_exception_free () from /usr/lib/libORBit-2.so.0
#14 0xb785a90c in CORBA_exception_set () from /usr/lib/libORBit-2.so.0
#15 0xb785a9d3 in CORBA_exception_set_system () from /usr/lib/libORBit-2.so.0
#16 0xb785744d in ORBit_small_invoke_stub () from /usr/lib/libORBit-2.so.0
#17 0xb785753e in ORBit_small_invoke_stub_n () from /usr/lib/libORBit-2.so.0
#18 0xb7863d32 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
#19 0xb7e50cbe in Bonobo_Control_getProperties ()
   from /usr/lib/libbonobo-2.so.0
#20 0xb7eeac0f in bonobo_control_frame_get_control_property_bag ()
   from /usr/lib/libbonoboui-2.so.0
#21 0x08085802 in panel_applet_frame_sync_menu_state ()
#22 0xb7e396e1 in bonobo_moniker_util_parse_name ()
   from /usr/lib/libbonobo-2.so.0
#23 0xb7e39a1f in bonobo_moniker_resolve_async_default ()
   from /usr/lib/libbonobo-2.so.0
#24 0xb78560d1 in ORBit_small_invoke_async () from /usr/lib/libORBit-2.so.0
#25 0xb784fcd8 in giop_invoke_async () from /usr/lib/libORBit-2.so.0
#26 0xb7853166 in giop_connection_handle_input ()
   from /usr/lib/libORBit-2.so.0
#27 0xb7870a1d in link_connection_state_changed ()
   from /usr/lib/libORBit-2.so.0
#28 0xb78739ce in link_io_add_watch_fd () from /usr/lib/libORBit-2.so.0
#29 0xb7778802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#30 0xb777b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#31 0xb777bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#32 0xb7b7a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#33 0x08061d8c in main ()

Thread 1 (Thread -1224972624 (LWP 8380)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb767d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f751b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7565770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7566ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7781122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7781159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77811d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7855790 in ORBit_RootObject_duplicate_T ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#11 0xb785f5d8 in CORBA_any__freekids () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#12 0xb785a7da in CORBA_exception__copy () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#13 0xb785a867 in CORBA_exception_free () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#14 0xb785a90c in CORBA_exception_set () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#15 0xb785a9d3 in CORBA_exception_set_system () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#16 0xb785744d in ORBit_small_invoke_stub () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#17 0xb785753e in ORBit_small_invoke_stub_n () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#18 0xb7863d32 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#19 0xb7e50cbe in Bonobo_Control_getProperties ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#20 0xb7eeac0f in bonobo_control_frame_get_control_property_bag ()
   from /usr/lib/libbonoboui-2.so.0
No symbol table info available.
#21 0x08085802 in panel_applet_frame_sync_menu_state ()
No symbol table info available.
#22 0xb7e396e1 in bonobo_moniker_util_parse_name ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#23 0xb7e39a1f in bonobo_moniker_resolve_async_default ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#24 0xb78560d1 in ORBit_small_invoke_async () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#25 0xb784fcd8 in giop_invoke_async () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#26 0xb7853166 in giop_connection_handle_input ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#27 0xb7870a1d in link_connection_state_changed ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#28 0xb78739ce in link_io_add_watch_fd () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#29 0xb7778802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#30 0xb777b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#31 0xb777bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#32 0xb7b7a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by ruudiculus on 2007-04-17
Astalavista, RichardJennings and blackwell...

What version of Ubuntu (or other) are you using? I've stepped to Debian since they released Etch, so I can only say for sure that F@G worked on my last Ubuntu configuration (which was Dapper Drake 6.06 on i686). With Debian things are fine, out of the box...

---

### Post by chewearn on 2007-04-18
hi ruudiculus
I'm running Ubuntu Edgy Eft 6.10.

hi richardjennings
Previously when I faced the same problem as you do, I managed to get out of it by killing the process called "gnome-panel".

---

### Post by Megaqwerty on 2007-04-19
> **blackwell said:**
> i got this same problem i got error when i try to add to panel your applet :(

in [email]Folding@Gnome.log[/email] i got only this:
"[Folding@Gnome log]
Info:"

I am also experiencing the same problem, have used chmod and chown on the installed directory (~/foldingatgnome) but the panel crashes when I add it. It continues to crash and reload until I delete the ~/foldingatgnome directory, at which point it tells me that the applet doesn't work (clearly because I deleted it's files ;) ) and asks me if I want to delete it. I do, and can use my panel again.

Any ideas?

-Megaqwerty

---

### Post by ruudiculus on 2007-04-20
I have a guess of what the problem might be. I take look at it this weekend...

---

### Post by blackwell on 2007-04-22
i use 6.06 Dapper  :(

---

### Post by TimJBart on 2007-04-23
I followed the instructions exactly, and everything seem to go well. 

I added the Folding@home icon to one of my panels, then BOOM...all my panels have disappeared and I don't really know how to get them back!  They've just gone!

This happened to anyone else?

By the way, I'm running Feisty.  I also have an AMD 64 but am running the 32bit version of ubunutu so used your 32bit install script.

Also, stupid question, but I haven't installed folding@home, your script does this doesn't it?

---

### Post by Megaqwerty on 2007-04-23
Yes, just look at page 4 ;) . Anyway, to fix your panel, you need to delete the folder you installed Folding@Gnome in, and then start gnome-panel. If you don't have access to a terminal due to your lack of panel, you can just reboot your computer. It will then tell you that Folding@Gnome doesn't work anymore, and will ask you if you want to delete it from the panel. Say yes.
  	
ruudiculus thinks he may know the problem, which since he made the applet, he can fix. So we just have to wait for him to fix it before we can use his applet.

---

### Post by TimJBart on 2007-04-23
Yeh I managed to fix it by following his instructions and removing everything.  I'll just wait for an update :)

---

### Post by axcairns on 2007-04-27
If your gnome panel dies, you can launch stuff by right-clicking on your desktop and selecting "Create launcher". I created two launchers (firefox and gnome-terminal) which allowed me to find the solution in this thread, rename my directory and restart my panel.

Looking forward to a F@G that doesn't crash ;-)

Allan

---

### Post by ruudiculus on 2007-04-27
Hi,

I've started writing a new F@G which should be able to monitor multiple folding processes and should be started just as Amarok or Rhythmplayer (hiding in the system tray, instead of being an applet). This way the icon will be really transparent and you don't have problems with Bonobo (which will get obsolete as I've heared) anymore.

Furthermore, the whole GUI will be a bit different. Auto-detection of F@H-executables will not be possible anymore, but you can manually add as much processes to monitor as you like.

Sadly I have little time at the moment, and since it is getting summer I'm a little less often behind the PC :) 

I don't think no F@G V2.x will appear for a while...

---

### Post by TimJBart on 2007-04-27
just to repeat my earlier question.  Am I right in thinking this app that ruudiculus created installs both the f@homeclient AND a graphical interface.

Or do I have to download and install f@home first, then install folding@GNOME ?

Thanks

---

### Post by ruudiculus on 2007-04-27
Jep, seperately download and install F@H first, then run my installer script!

---

### Post by skoona on 2007-04-27
Take a look at what I have already done and then let's decide whats next.  All my code is GPL and can be easily reused, also I would welcome Graphics, Documentation, and packaging help.

GFHCM as a package contains a standalone monitor, and a client/server (gfhcmc/gfhcmd)  monitor.  These are written with C & GTK2/GLIB/GConf.   

GKrellFah2 is a set of plugins for GKrellm2, and contains the same set of functions(standalone, client/server) with a reduced feature set.

I originally wrote a true GNOME applet; but then KDE and other users complained that icons and other key features didn't work for them.  Now the programming model is based on FreeDesktop.org's common GUI models.

Links are in my signature.


James,

---

### Post by Nick75 on 2007-04-27
i got it to install, dont know if its correct but didnt get any errors... but it doesnt run

new to linux, any help will be gladly appreciated

thx,
Nick

---

### Post by TimJBart on 2007-04-28
> **Nick75 said:**
> i got it to install, dont know if its correct but didnt get any errors... but it doesnt run

new to linux, any help will be gladly appreciated

thx,
Nick

Well I think the concensus is that this particular app is broken and awaiting a fix.  It didn't work for me at all on Feisty, so may be someone else can help you?

---

### Post by kitsura on 2007-04-28
I followed the instructions and installed the applet but then my gnome panels crashes when I try to add the icon to the panel. I had to created a new profile in the recovery terminal to solve my problem. If I knew of this thread in the first place I would have solved the problem without so much trouble.

---

### Post by dansweat on 2007-04-28
Just confirming the 

The panel encountered a problem while loading "OAFIID:GNOME_FoldingAtGnome". Bug


***PROCESS***
Click add applet
Select applet from list
hit add
get error message
********************

Running Ubuntu Feisty Fawn
Man I wish it was summer again here in AUS. Autumn/Winter in Canberra is goddam cold.

Keep up teh good work chief!

---

### Post by ExxonValdeez on 2007-04-29
I have the same problem. I had to reset my GNOME settings because every time I logged in the panel would crash. The app looks really cool though!

---

### Post by dansweat on 2007-04-29
The most bizzare thing happened this morning.
I turned my pc back on and there were lik 8 copies of the applet in the taskbar!
I closed them all off, then decided to have another crack at the applet.
When I added it no error!
It looks to be all working perfectly.

It may have something to do with the running of FAH in the background as i did yesterday.
I did do a ctrl-c and kill it before i tried using the applet, however there MAY have been the cores lying about.

In any case my reccomendation to young players would be to do a reboot, dont start FAH and then initialte the applet. Worked for me

---

### Post by ruudiculus on 2007-04-30
dansweat,

It seems that using F@G to start the F@H process works for you, instead of first running F@H and thenF@G.

Could you send me the F@G log file please? I'm curious if I can find a reason in there...

---

### Post by ruudiculus on 2007-06-09
Hi there,

I'm busy rewriting F@G at the moment. It will support the monitoring of multiple F@H processes. However I don't have an SMP computer. So I need a little help here from users that run >1 F@H processes!!!

**What I can do here:**
I can try to run multiple instances of F@H by copying the executable, say 3 times:
/home/programs/fah1
/home/programs/fah2
/home/programs/fah3

Then run them and let F@G monitor each process unit workfile. This will work without problems I guess and I think this is the way most people configure it when they want to have >1 F@H processes running.

**What I don't know:**
I have no idea what the x86_64-SMP version of F@H does. Does it use all available cores to  fold a work unit? Or can that single SMP-executable run >1 subprocesses (each on a core available) and does it make multiple unit work files? Or does it combine them in one unit work file?

Those of you SMP'ers who run >1 F@H processes, please help! :D

Thanks in advance!

---

### Post by badmofo666 on 2007-12-18
> **tomplast said:**
> Nice app though when I tried to add the applet my gnome-panel crashes (and reappears after a few seconds) and when I close the bugreporting dialog that comes up gnome-panel crashes again :/. I have had the same problem before so perhaps your applet may have something todo with it *-).


You got any ideas how to fix it (I don't want to create a new profile as I did last time). Thank you for any assistance.


EDIT:

I solved it by simple deleting the folder where I installed it :).

I had the same problem as the guy above with version 1.2, FAH version 5.04, and Fedora 7.  Crashes, close the bug reporting dialog, then crashes again.

This app would be nice, but I can't get it to work.

---

### Post by c0mp13371331337 on 2008-06-27
*Anxiously awaiting v2.0* :-D

---

