---
title: "Cannot stop recording macro with xmacro in Kubuntu 9.04"
date: 2009-05-03
forum: General Help
---

### Post by Victor Warner on 2009-05-03
I am using the release version of Kubuntu 9.04 and have installed xmacro.

I have tried to record macros with xmacro but after starting it, choosing the key to stop recording, going through the key presses/mouse moves I find that the stop recording key does not work (I have tried the suggested escape key as well as several others). I have also uninstalled and reinstalled xmacro. But this has not made any difference.

For example to start recording the macro I would do the following:

```
victor@kubuntu904:~$ xmacrorec2 >/home/victor/various/xmacro/victor.macro 
Server VendorRelease: 10600000                                           
XRecord for server ":0.0" is version 1.13.                               


Press the key you want to use to end the application. This key can be any key, 
as long as you don't need it while working with the remote display.            
A good choice is Escape.                                                       

The chosen quit-key has the keycode: 9
XQueryPointer returned: 1
Got Start Of Data
Skipping...
```


The file "victor.macro" is created, but has a zero characters (and nothing in it).

I noticed that under kubuntu 8.10 when then recording is started the following is added to what is set above:

```
- Skipping stale KeyRelease event. 1
```

I am not sure if this makes any difference or what its significance (not having much Linux knowledge).

Help with this would be greatly appreciated.

Victor Warner.

---

