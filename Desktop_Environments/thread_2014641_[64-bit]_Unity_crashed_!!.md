---
title: "[64-bit] Unity crashed !!"
date: 2012-07-02
forum: Desktop Environments
---

### Post by nipunshakya on 2012-07-02
Hello friends. I was playing lord of ultima in chrome when i ran out of battery and had to shut down my laptop in last 2 minutes left... don't even know if it shut down properly because the shutdown screen was kind of freezed to my current wallpaper and it shut down strangely.

Now when i restart my laptop, all i see is the screenshot of my screen... 

I got to the browser currently by a chrome extension of facebook!!!

Ubuntu2D works fine...just the unity has crashed... i can't even access the terminal to type ```
unity --reset
```

Any suggestions?

---

### Post by blackbird34 on 2012-07-02
Can you not do Ctrl+Alt+F1 (or F2, F3, F4, F5) to get a console (non-graphical) session and do it from there?

---

### Post by nipunshakya on 2012-07-02
Negative results.... 
when running
 ```
unity --reset
``` after hitting ctrl+alt+F1, i get errors saying somethings like 
```
....<other texts here>.........compiz(core) 'unityshell' couldn't load......
....<other texts here>......... /usr/lib/compiz/libunityshell.so : libGL.so.1: can't open shared file : No such files or directories....<other texts here>
```

guess ill have to reinstall unity..

---

### Post by nipunshakya on 2012-07-02
ok so i followed the following link.... but nothing has changed literally..
[http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)

---

### Post by nipunshakya on 2012-07-02
ok so i followed the following link.... but nothing has changed literally..
[http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)

---

### Post by nipunshakya on 2012-07-03
ok... so i ran following in the terminal.. i got errors as such:

```

winuxuser@MagicBox:~$ unity --reset & disown
[1] 3370
winuxuser@MagicBox:~$ unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0xc00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing addhelper options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing decor options...done
Initializing expo options...done
Initializing extrawm options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing grid options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600401

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x16004ce

```

and no further things happen... is it supposed to be like that??

i also ran the following:

```

winuxuser@MagicBox:~$ compiz --replace & disown
[1] 3341
winuxuser@MagicBox:~$ Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x26000d6

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing addhelper options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing decor options...done
Initializing expo options...done
Initializing extrawm options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
GConf Error: Configuration server couldn't be contacted: D-BUS error: Can't overwrite existing read-only value: Value for `/apps/metacity/global_keybindings/panel_main_menu' set in a read-only source at the front of your configuration path
GConf Error: Configuration server couldn't be contacted: D-BUS error: Can't overwrite existing read-only value: Value for `/apps/metacity/global_keybindings/panel_run_dialog' set in a read-only source at the front of your configuration path
Initializing grid options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x26000d6
```

and it stuck at there too... no further actions... i didn't get anything.... no blinking cursor , nothing... is it supposed to be like that?? or is the process still running?? too much confused here.. :(
Any suggestions guys?

---

### Post by stinkeye on 2012-07-03
Check to see what gfx driver your using.
```
sudo lshw -c video
```
eg my output
```
[COLOR="Olive"]glen@Precise:~$[/COLOR] sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Red"]driver=nvidia[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```

---

### Post by nipunshakya on 2012-07-03
i have a ati video card but haven't installed its drivers from additional drivers 
```
winuxuser@MagicBox:~$ sudo lshw -c video
[sudo] password for winuxuser: 
  *-display               
       description: VGA compatible controller
       product: RV710 [Mobility Radeon HD 4300 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:e0000000-efffffff ioport:de00(size=256) memory:f6df0000-f6dfffff memory:f6d00000-f6d1ffff

```

---

### Post by nipunshakya on 2012-07-03
i logged to GNOME this time... and ran ```
unity --reset-icons
```... then logged back to Ubuntu... the minimize and maximize icons bar were recovered... im just wondering why this unity refuses to be reset... :(

---

### Post by stinkeye on 2012-07-03
It was just a thought in case you were loading a 3d unsupprted driver after the incorrect shutdown.

Try the unity support test.
```
/usr/lib/nux/unity_support_test -p
```
eg my output.
```
[COLOR="Olive"]glen@Precise:~$[/COLOR] /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 302.17

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by nipunshakya on 2012-07-03
before your suggestion i ran the following logging from GNOME session```
winuxuser@MagicBox:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Failure during recursive unset of "/apps/compizconfig-1/profiles/unity": Configuration server couldn't be contacted: D-BUS error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/winuxuser/.compiz/session to /home/winuxuser/.compiz-1/session
[LOG]: Copied file /home/winuxuser/.compiz/session/10ffc6fa7ce1c43019134129029251712200000022030045 to /home/winuxuser/.compiz-1/session/10ffc6fa7ce1c43019134129029251712200000022030045
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000014

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3400004

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3a00099!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing addhelper options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing decor options...done
Initializing expo options...done
Initializing extrawm options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing grid options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"


```

after the last line, it keeps blinking and blinking.... and it goes on and on... should i break the process or let terminal process it till it finishes and prompts me to enter other commands...??

Well now i don't have the minimize buttons even in GNOME .... :(

---

### Post by nipunshakya on 2012-07-03
```
winuxuser@MagicBox:~$ /usr/lib/nux/unity_support_test -p
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
winuxuser@MagicBox:~$ 

```

isn't there any possible way to reninstall libGL.so.1?? or something like that? i see the error in compiz(core) when running previous codes of resetting unity.... can't the compiz be safely removed completely and reinstalled back to the machine??

---

### Post by isaacj87 on 2012-07-03
> **WinuxUser said:**
> ```
winuxuser@MagicBox:~$ /usr/lib/nux/unity_support_test -p
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
winuxuser@MagicBox:~$ 

```

isn't there any possible way to reninstall libGL.so.1?? or something like that? i see the error in compiz(core) when running previous codes of resetting unity.... can't the compiz be safely removed completely and reinstalled back to the machine??

Yes, you could try reinstalling libGl.so:

```
sudo apt-get install --reinstall libgl1-mesa-glx
```

---

### Post by nipunshakya on 2012-07-03
> **isaacj87 said:**
> 
```
sudo apt-get install --reinstall libgl1-mesa-glx
```
yes... i got my unity back now... wow...im loving it... yes..yes..yes.. clearly there were indications that the library was being corrupt.. but don't know how...

anyway, now i can successfully get
```

winuxuser@MagicBox:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
winuxuser@MagicBox:~$ 

```

Thanks guys for your help....):P

---

### Post by nipunshakya on 2012-07-07
> **isaacj87 said:**
> Yes, you could try reinstalling libGl.so:

```
sudo apt-get install --reinstall libgl1-mesa-glx
```

well this is embarrassing. This is the third time i have reinstalled the library since my error about the library has appeared. It seems now that my unity keeps on crashing every once in 15 boot ups and i have to reinstall the library again and again. Isn't there any piece of code that can really find out what is happening to this library?? and why it is crashing again and again?? The crash error shows details about my compiz, and i report it everytime it appears... but it seems like there is error with the library....

Any suggestions you guys and gurus??

Thanks.):P

---

### Post by radioz on 2012-07-07
Have you checked to see if you are having hardware problems?

Look at your log files (dmesg would be good) to see if there are any problems booting up.

I would also check for disk problems. If you don't have it, install GSmartControl and run it. Select your drive and look for any errors in the error log. Also look at the Attributes list for signs of failure (you'll have to Google for 'smart' information on your drive to interpret some of these values).

You might also try running a memory test to make sure your ram is ok.

Something sounds flakey with your system. Good luck!

---

