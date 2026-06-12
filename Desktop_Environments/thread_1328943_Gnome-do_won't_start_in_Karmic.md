---
title: "Gnome-do won't start in Karmic"
date: 2009-11-16
forum: Desktop Environments
---

### Post by carleton on 2009-11-16
Please help with Gnome-Do! Since upgrading to Karmic I can't get it to start at all. Every time I run it I get the following error.

```
[Error 22:43:33.717] Missing login credentials. Please set login information in plugin configuration.

(Do:9227): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Could not locate Tomboy on D-Bus. Perhaps it's not running?
Microblogging.FriendSource "Microblog friends" encountered an error in Items: Object reference not set to an instance of an object.
Microblogging.FriendSource "Microblog friends" encountered an error in Items: Object reference not set to an instance of an object.
[Debug 22:43:35.600] Acquiring org.freedesktop.DBus session instance
[Debug 22:43:35.603] Starting org.bansheeproject.CollectionIndexer

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at org.freedesktop.DBus.IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 

```

I've tried uninstalling and reinstalling it several times to no avail. Any help would be much appreciated.

Cheers!

---

### Post by coldReactive on 2009-11-16
Did you remove wnck, tomboy and banshee recently? If not, did you upgrade recently?

---

### Post by Captain_Glen on 2009-11-19
I get a similar error.

I have a fresh install of Ubuntu 9.10.

I don't think I removed any of the packages you mentioned.
```

(Do:3498): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: Object reference not set to an instance of an object.
```

---

### Post by Kuro-Chinko on 2009-11-19
I can't remeber the error message I got, but I did get something similar when I attempted to install Gnome-Do.

A friend told me to purge Mono and all it's related apps, and then reinstall Gnome-Do and related stuff again.... it worked.

That is all I know. I'm new to Ubuntu, unfortunately.

---

### Post by stinkeye on 2009-11-19
> **carleton said:**
> Please help with Gnome-Do! Since upgrading to Karmic I can't get it to start at all. Every time I run it I get the following error.

```


(Do:9227): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.



```


I wouldn't worry about this error.I get this on a fresh karmic install and gnome-do runs fine.
With all the problems people are having with upgrading, I would do a backup and fresh install.
I've had no major problems with karmic.

---

### Post by Captain_Glen on 2009-11-19
stinkeye can you get Gnome Do to auto run?

The reason I need to be able to run it from the terminal is so I can set it to run automatically when ubuntu starts.

Mine works if I click the icon in the Gui.  But I want it to load automatically.

Kuro-Chinko are you using ubuntu 9.10?  Have you got Gnome Do working on so that it auto starts?

Also I don't have mono installed so purging it won't work.

I have filed a bug on launchpad.

---

### Post by stinkeye on 2009-11-19
> **Captain_Glen said:**
> stinkeye can you get Gnome Do to auto run?

The reason I need to be able to run it from the terminal is so I can set it to run automatically when ubuntu starts.

Mine works if I click the icon in the Gui.  But I want it to load automatically.

Kuro-Chinko are you using ubuntu 9.10?  Have you got Gnome Do working on so that it auto starts?

Also I don't have mono installed so purging it won't work.

I have filed a bug on launchpad.
Yes. Just select *start gnome-do at login* in preferences.
I think you might find that gnome-do is built on mono.
What window manager are you using?

---

### Post by Captain_Glen on 2009-11-23
I am using Compiz.

But I found gnome-do works if I use metacity.

Is there a solution to get it working with compiz?

---

### Post by stinkeye on 2009-11-24
> **Captain_Glen said:**
> I am using Compiz.

But I found gnome-do works if I use metacity.

Is there a solution to get it working with compiz?
Firstly I would make sure you are running compiz at startup by installing wmctrl
```
sudo apt-get install wmctrl
```
Then after you restart run in terminal
```
wmctrl -m
```
and it will tell you what window manager is running
eg. I get
```
glen@karmic:~$ wmctrl -m
Name: compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```
Although I don't have to on my machine you might want to try delaying the 
starting of gnome do until after compiz has loaded.
This is a script I use for delaying the start of conky that I tested and will do the same for gnome-do.
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 gnome-do >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "GNOME-DO IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```
Save this in your home folder as *start_do*
Right click on start_do properties > permissions and tick the execute box.
Go to your gnome do preferences and untick start gnome-do at login.
Open startup applications and add *start_do* to the startup programs
by adding ```
/home/[COLOR="Blue"]your-username[/COLOR]/start_do
```
in the command box.
[ATTACH]137412[/ATTACH]
[COLOR="DarkOrange"][SIZE="5"]For this script to work you must have the Dbus plugin enabled.[/SIZE][/COLOR]
It is under utilities in CCSM.
Restart and see if gnome-do loads.

---

### Post by Captain_Glen on 2009-11-24
Thanks stinkeye that fixed it!

---

### Post by stinkeye on 2009-11-24
No problem.
One other thing you might want to look at is fusion-icon if your using it.
In startup applications I start it with the command...```
fusion-icon -n
```
which will start fusion-icon but stop it from trying to load a window manager.
Your computer should boot into compiz anyway and as I said before I don't need a delay script on my computer.
Good luck.

---

### Post by El Jamo on 2009-12-07
Similar problem here: gnome-do, karmic (9.10), and compiz.

I can get gnome-do to start from the menu, but I can't get it to come up when I press the hotkeys.  I had changed my settings to make gnome-do start when I press alt+space (habit I picked up from using launchy).

Here's how I solved it:
I found that compiz was already using that key combination to open the window menu.  I just disabled that key combination in the compizconfig-settings-manager (General Options -> Key bindings) and everything worked fine.

Note that you might have to install the compizconfig manager (I don't think it's installed by default): sudo apt-get install compizconfig-settings-manager

Once it's installed, you can find it in System -> Preferences.

EDIT: Most people won't be using the alt-space key combination, so you may need to search through the compizconfig manager a little bit to find out which plugin is sharing that key combination, and then change it.

---

### Post by gusarp on 2009-12-07
Recently i updated to kernel .16 and Gnome-do stop working at all, I un- and re-install it, but problem continues.
Even i cant open it from icon.

Any help will be so much appreciated.

---

### Post by phazixc on 2009-12-11
.

---

### Post by phazixc on 2009-12-11
Stinkeye...

Excellent thanks I have been looking every were, trying to find out how to fix this, Your script fix it, Thanks very much, Im new to ubuntu. best thing I have done moving from windows to Ubuntu.

---

### Post by martini1179 on 2009-12-18
> **gusarp said:**
> Recently i updated to kernel .16 and Gnome-do stop working at all, I un- and re-install it, but problem continues.
Even i cant open it from icon.

Any help will be so much appreciated.

I hope this helps. I've just upgraded to Karmic and everything worked (so far!) except Gnome-Do wouldn't start. 

If creating start_do script didn't help, then delete it/disable it in Startup Applications (System >> Preferences >> Startup Applications)

Then open your terminal. Applications >> Accessories >> Terminal 

Type Gnome-Do 

Take a look at the entire error message. What applications does it reference? Methinks it'll be different for everybody. Mine mentioned Banshee. For some reason, Banshee was uninstalled during the Karmic upgrade on my system. Reinstalling Banshee allowed Gnome-Do to run again! 

I'm thinking that there's a bug in Gnome-Do that'll prevent it from running if one of the apps to which it has shortcuts is removed in the Karmic upgrade, but I can't confirm this.

---

### Post by gusarp on 2009-12-22
> **martini1179 said:**
> I hope this helps. I've just upgraded to Karmic and everything worked (so far!) except Gnome-Do wouldn't start. 

If creating start_do script didn't help, then delete it/disable it in Startup Applications (System >> Preferences >> Startup Applications)

Then open your terminal. Applications >> Accessories >> Terminal 

Type Gnome-Do 

Take a look at the entire error message. What applications does it reference? Methinks it'll be different for everybody. Mine mentioned Banshee. For some reason, Banshee was uninstalled during the Karmic upgrade on my system. Reinstalling Banshee allowed Gnome-Do to run again! 

I'm thinking that there's a bug in Gnome-Do that'll prevent it from running if one of the apps to which it has shortcuts is removed in the Karmic upgrade, but I can't confirm this.
**Thank you. did as u said... to be honest now I'm even more lost. Couple days ago y try making a new user. Gnome-Do actually starts on new user but doesn't work at all. Whatever i click or type it just closes.**

**Now, following your instructions this is the error i get:**
[I]"** (/usr/lib/gnome-do/Do.exe:2851): CRITICAL **: _wapi_shm_file_open: shared file [/home/gustavoramirez/.wapi/shared_data-gustavoramirez-laptop-Linux-i686-312-12-0] open error: Input/output error

** (/usr/lib/gnome-do/Do.exe:2851): CRITICAL **: _wapi_shm_attach: shared file [/home/gustavoramirez/.wapi/shared_data-gustavoramirez-laptop-Linux-i686-312-12-0] open error
**
ERROR:shared.c:349:shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/gnome-do/Do.exe:2851): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/gnome-do/Do.exe:2851): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/gnome-do/Do.exe:2851): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

    /usr/bin/cli [0x80c8824]
    [0x728410]
    [0x728422]
    /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x5094d1]
    /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x50c932]
    /lib/libglib-2.0.so.0(g_assertion_message+0x13c) [0x16fddc]
    /lib/libglib-2.0.so.0 [0x17043d]
    /usr/bin/cli [0x81bb9db]
    /usr/bin/cli [0x81a7c86]
    /usr/bin/cli(mono_once+0x67) [0x81b5eb7]
    /usr/bin/cli [0x81a7bd4]
    /usr/bin/cli [0x81ba6af]
    /usr/bin/cli [0x8153d80]
    /usr/bin/cli(mono_runtime_init+0x26) [0x815bec6]
    /usr/bin/cli [0x805d041]
    /usr/bin/cli(mono_main+0x285) [0x80b0195]
    /usr/bin/cli [0x805aba5]
    /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x4f5b56]
    /usr/bin/cli [0x805aae1]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
0x00728422 in __kernel_vsyscall ()
* 1 Thread 0xee66f0 (LWP 2851)  0x00728422 in __kernel_vsyscall ()

Thread 1 (Thread 0xee66f0 (LWP 2851)):
#0  0x00728422 in __kernel_vsyscall ()
#1  0x00987c63 in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  <signal handler called>
#4  0x00728422 in __kernel_vsyscall ()
#5  0x005094d1 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0x0050c932 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0x0016fddc in g_assertion_message () from /lib/libglib-2.0.so.0
#8  0x0017043d in g_assertion_message_expr () from /lib/libglib-2.0.so.0
#9  0x081bb9db in ?? ()
#10 0x081a7c86 in ?? ()
#11 0x081b5eb7 in mono_once ()
#12 0x081a7bd4 in ?? ()
#13 0x081ba6af in ?? ()
#14 0x08153d80 in ?? ()
#15 0x0815bec6 in mono_runtime_init ()
#16 0x0805d041 in ?? ()
#17 0x080b0195 in mono_main ()
#18 0x0805aba5 in ?? ()
#19 0x004f5b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#20 0x0805aae1 in ?? ()

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted"[/I]            

[B]I hope some you or somebody else can figure it out.

Again thanks a lot.

Best regards and happiest seasons.[/B]

---

### Post by ssayler on 2010-01-22
Just got the same error as Gusarp today. It started after I hooked up an external monitor and tried to enable extended desktop, so I think it's GDM related. I reduced the size of my Virtual Desktop back to 1680 by 1050 from 3360 by 1050, but that didn't resolve it.

** (/usr/lib/gnome-do/Do.exe:4378): CRITICAL **: _wapi_shm_file_open: shared file [/home/itshss/.wapi/shared_data-MRMLLITSHSS-Linux-x86_64-328-12-0] open error: Input/output error

** (/usr/lib/gnome-do/Do.exe:4378): CRITICAL **: _wapi_shm_attach: shared file [/home/itshss/.wapi/shared_data-MRMLLITSHSS-Linux-x86_64-328-12-0] open error
**
ERROR:shared.c:349:shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/gnome-do/Do.exe:4378): WARNING **: Thread (nil) may have been prematurely finalized


edit - directhex's solution from this post fixed the issue for me. [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8407968](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8407968)

kill all Mono apps, and run "rm -r /home/benjamin/.wapi"

---

### Post by gusarp on 2010-01-25
Now all is working just fine. Solution? I create a new admin user. copy/paste all my stuff there, delete and forget bout last user.
I know this is not a real solution, but all is working now so i stand to it.

---

### Post by helbent forleder on 2011-01-12
After having what I thought was a completely separate problem with nautius, I reinstalled the nautilus package and now gnome-do starts correctly every time. Try it! :)

---

