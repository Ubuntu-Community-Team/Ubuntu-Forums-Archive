---
title: "Mount usb in xfce minimal ubuntu installation"
date: 2010-04-19
forum: Desktop Environments
---

### Post by Athanasius on 2010-04-19
What program does Xubuntu use to have a usb drive show up in the Thunar menu and allow you to unmount/eject a usb drive?

---

### Post by kerry_s on 2010-04-19
the systems, it should just work if you have thunar.

---

### Post by snowpine on 2010-04-19
Try thunar-volman.

---

### Post by Athanasius on 2010-04-19
It is installed but the drive still does not appear in thunar.  I have to go to /media and then it is there.  Not really what I wanted though.

---

### Post by kerry_s on 2010-04-19
> **Athanasius said:**
> It is installed but the drive still does not appear in thunar.  I have to go to /media and then it is there.  Not really what I wanted though.

oh crap, i just checked & mines not working now to & mine don't show in media. i say some update screwed it, maybe just wait for an update that fixes it. it was working like 2 days ago when i backed my files. :confused:

---

### Post by kerry_s on 2010-04-19
alright mines working again. what i did was uninstalled it & deleted ~/.config/Thunar, then reinstalled now it shows up in thunar & xfdesktop.

ps: i also killed the "thunar --daemon" i had running from startup.

---

### Post by Athanasius on 2010-04-19
It didn't work for me but thanks anyways  :)

---

### Post by sean_worker on 2010-04-19
everything is working for me ... this is what I see when I query thunar (though it might not be thunar that is the cause/solution to this problem):
```
seanpk@ralfe:~$ aptitude search thunar
i A libthunar-vfs-1-2               - VFS abstraction used in thunar            
p   libthunar-vfs-1-dev             - Development files for libthunar-vfs       
i   thunar                          - File Manager for Xfce                     
i   thunar-archive-plugin           - Archive plugin for Thunar file manager    
i A thunar-data                     - Provides thunar documentation, icons and t
p   thunar-dbg                      - debugging informations for thunar         
i   thunar-media-tags-plugin        - Media tags plugin for Thunar file manager 
i   thunar-thumbnailers             - thumbnailers for Thunar file manager      
i A thunar-volman                   - Thunar extension for volumes management   
v   thunar-volman-plugin            -                                           
seanpk@ralfe:~$
```

---

### Post by kerry_s on 2010-04-19
> **sean_worker said:**
> everything is working for me ... this is what I see when I query thunar (though it might not be thunar that is the cause/solution to this problem):
```
seanpk@ralfe:~$ aptitude search thunar
i A libthunar-vfs-1-2               - VFS abstraction used in thunar            
p   libthunar-vfs-1-dev             - Development files for libthunar-vfs       
i   thunar                          - File Manager for Xfce                     
i   thunar-archive-plugin           - Archive plugin for Thunar file manager    
i A thunar-data                     - Provides thunar documentation, icons and t
p   thunar-dbg                      - debugging informations for thunar         
i   thunar-media-tags-plugin        - Media tags plugin for Thunar file manager 
i   thunar-thumbnailers             - thumbnailers for Thunar file manager      
i A thunar-volman                   - Thunar extension for volumes management   
v   thunar-volman-plugin            -                                           
seanpk@ralfe:~$
```

i don't install recommends on mine.
```

owner@foxconn-1:~$ dpkg -l *thunar*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  libthunar-vfs-1-2         1.0.1-3ubuntu1            VFS abstraction used in thunar
un  libthunarx-2-0            <none>                    (no description available)
ii  thunar                    1.0.1-3ubuntu1            File Manager for Xfce
ii  thunar-archive-plugin     0.2.4-5                   Archive plugin for Thunar file manager
ii  thunar-data               1.0.1-3ubuntu1            Provides thunar documentation, icons and translations
un  thunar-media-tags-plugin  <none>                    (no description available)
un  thunar-volman             <none>                    (no description available)
owner@foxconn-1:~$ 

```

& in synaptic:

---

### Post by sean_worker on 2010-04-20
looks like you should try installing thunar-volman, as suggested, it doesn't look installed right now:
> un  thunar-volman             <none>                    (no description available)


---

### Post by kerry_s on 2010-04-20
> **sean_worker said:**
> looks like you should try installing thunar-volman, as suggested, it doesn't look installed right now:

mine works without it is what i'm saying.

---

### Post by sean_worker on 2010-04-20
sorry Kerry, brainfart ... I thought you were the OP ... Athanasius, what do you have installed?

---

