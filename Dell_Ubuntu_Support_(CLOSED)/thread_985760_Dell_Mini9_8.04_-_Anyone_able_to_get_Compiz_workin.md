---
title: "Dell Mini9 8.04 - Anyone able to get Compiz working (on the 'standard Ubuntu' desktop"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RichTJ99 on 2008-11-17
Hi,

I have a Dell mini 9, sometimes running 8.04 (dell version) & sometimes running 8.1 while I am testing.  I really do like Compiz & would liek to install it using Dells 8.04. 

So with that being said, if I am not using Dells Netmix "launcher" screen, can I run Compiz? 

If so, how would I do that?

Thanks,
Rich

---

### Post by starcannon on 2008-11-17
> **RichTJ99 said:**
> Hi,

I have a Dell mini 9, sometimes running 8.04 (dell version) & sometimes running 8.1 while I am testing.  I really do like Compiz & would liek to install it using Dells 8.04. 

So with that being said, if I am not using Dells Netmix "launcher" screen, can I run Compiz? 

If so, how would I do that?

Thanks,
Rich

The easy way is to install fusion-icon
```
sudo apt-get install fusion-icon
```
run it from Applications>System Tools
if you want it to run on boot, add it to System>Preferences>Sessions

GL and have fun

---

### Post by armandh on 2008-11-17
this does work with dell ubuntu. needs to be enabled each session, and the "window" manager restarted probably not the best way

QUOTE
 Re: Inspiron Mini 9 just works except.....
To enable desktop effects on the factory install on the mini9 i simply installed fusion-icon from synaptic, now I have compiz goodness, no reloading the OS needed.
Code:

sudo apt-get install fusion-icon

You'll find fusion-icon in Applications>System Tools. If you want it to load at boot be sure to add it to System>Preferences>Sessions.
The only thing I don't like about my mini is the keyboard layout, who ever came up with it needs to go back to ergonomics 101.

The machine works perfectly out of the box though.

GL and have fun
END QUOTE

regular Ubuntu [not dellbuntu] just works when the compiz manager is installed but it needs sound

this thread
[http://ubuntuforums.org/showthread.php?t=981602](http://ubuntuforums.org/showthread.php?t=981602)

---

### Post by DragginMaster on 2008-11-27
I am pretty new to ubuntu, I want to add compiz to my sessions on my mini but am not sure what info i need to put into the session manager.

i know in windows how to figure out the command line and where to look for the executable files. I am clueless where to look to garner the infomation.

i have the compiz fusion icon installed and working, just lacking the knowledge for the next step. any help is appreciated

---

### Post by earthpigg on 2008-11-27
normally, its 

```
sudo apt-get install ccsm
```

but that doesnt seem to be in the dell repos for whatever reason...

so open synaptic (system->admin->synaptic package manager) and install 'compizconfig-settings-manager'

(i just did this literally 2 min ago :) )

then go to 'system->pref->compizconfig settings manager' to start the program that lets you set options, etc.

---

