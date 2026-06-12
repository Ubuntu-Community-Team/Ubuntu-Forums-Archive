---
title: "Firefox 3 broke, can't reinstall/upgrade"
date: 2009-01-29
forum: General Help
---

### Post by Mzwo on 2009-01-29
hi,

this is a "fork" of this problem: [http://ubuntuforums.org/showt...]("http://ubuntuforums.org/showthread.php?t=1048122")

after doing as suggested, namely to run firefox in safe mode, the following happened:

[LIST]
[*]back/forward stopped working (icons grey, "unclickable")
[*]reload won't work (see above)
[*]bookmarks are gone. restore didn't work, bookmarks.html not to be found, new bookmarks could not be created. 
[*]after complete reinstall, removal, complete removal and install the problems could not be solved. all of the above will just not work.
[/LIST]

i had to resort to firefox 2, but would quite like to get back to firefox. what to do?

Thanks,
Mzwo

---

### Post by khedron on 2009-01-29
I'll post what I just posted there:

Ok, first try deleting your profile directory (well, actually just moving it somewhere else so firefox can't find it):
```
temp="$(mktemp ~/profileXXX)"
mv ~/.mozilla/firefox/*default "$temp"

```This should force Firefox to create a new profile for you. If this fixes the problem, you should be able to copy back the bookmarks.html file from your old profile to ~/.mozilla/firefox/????????.default to keep your bookmarks.

If this doesn't, try fully reinstalling Firefox:
```
sudo aptitude purge firefox
sudo aptitude install firefox

```

---

### Post by Mzwo on 2009-01-30
hi, 

thanks. will try this as soon as i get back to my computer (as opposed to the office pc) and report. 

Mzwo

---

### Post by blazemore on 2009-01-30
A cool way of deleting everything to do with Firefox:
```
sudo su
rm -rfv $("locate -i" firefox)
```
That searched for any files containing the word "firefox" (case insensitive) and deletes it.

---

### Post by khedron on 2009-01-30
> **blazemore said:**
> A cool way of deleting everything to do with Firefox:
```
sudo su
rm -rfv $("locate -i" firefox)
```That searched for any files containing the word "firefox" (case insensitive) and deletes it.

Seems a bit too general to me, could end up deleting a bit too much...

---

### Post by Mzwo on 2009-01-31
@khedron: did purge and install - problem persists. firefox 3 refuses to work properly. no back/forward/reload/bookmark option.

What to do?

cheers,

Mzwo

---

### Post by khedron on 2009-01-31
Maybe some of your packages aren't properly installed. Try
```
sudo dpkg --configure -a
sudo aptitude install -f
```
The first command will fully install any packages that may have not been properly installed.

The second command should fix any dependency problems with your packages, but make sure that if it suggests something, you read what it is removing carefully.

If that doesn't do anything, we'll see what else can be done.

---

### Post by khedron on 2009-01-31
If that doesn't work, the other thread talked about flash problems. To find out what flash stuff you have installed, run ```
aptitude search flash
``` and paste the output here, please.

---

### Post by Mzwo on 2009-02-02
thanks.

will do and get back to you.

Mzwo

---

### Post by Mzwo on 2009-02-02
hi khedron,

thanks for your help so for. alas, no luck. firefox 3 remains a no go.

"aptitude search flash" got me:

```
mzwo@Mzwo:~$ aptitude search flash
p   flashblock                                                                                      - mozilla extension that replaces flash plugin by a button                                                 
i   flashplugin-nonfree                                                                             - Adobe Flash Player plugin installer                                                                      
p   flashrom                                                                                        - Universal BIOS/ROM/flash programming utility                                                             
p   flashybrid                                                                                      - automates use of a flash disk as the root filesystem                                                     
p   libflash-dev                                                                                    - GPL Flash (SWF) Library - development files                                                              
p   libflash-mozplugin                                                                              - GPL Flash (SWF) Library - Mozilla-compatible plugin                                                      
p   libflash-swfplayer                                                                              - GPL Flash (SWF) Library - stand-alone player                                                             
p   libflash0c2                                                                                     - GPL Flash (SWF) Library - shared library                                                                 
p   libflashsupport                                                                                 - Support library for sound output of Flash 9 with pulseaudio                                              
p   libroxen-flash2                                                                                 - Flash2 module for the Roxen Challenger web server                                                        
p   m16c-flash                                                                                      - Flash programmer for Renesas M16C and R8C microcontrollers                                               
p   mobile-basic-flash                                                                              - Home applet for Hildon                                                                                   
p   vrflash                                                                                         - tool to flash kernels and romdisks to Agenda VR                                                          
mzwo@Mzwo:~$ 
```

any thoughts?

cheers,
Mzwo

---

### Post by khedron on 2009-02-02
Since the comment on the other thread mentioned flash, I thought it might be worth uninstalling your Flash and seeing if Firefox started working.
```
sudo aptitude remove flashplugin-nonfree
```

Try that.

---

### Post by Mzwo on 2009-02-02
ok ...

BUT: firefox 2 is working just fine, merely 3 is giving me grief. could that be flash-related? i'm the first to admit that i don't know my kernel from my terminal when it comes to all things linux, but that does sound a shade unlikely. why would flash make firefox 3 forget how to use back/forward/reload *and* the existance of bookmarks?

cheers,
Mzwo

---

### Post by Mzwo on 2009-02-02
know what's funny?
firefox 3 for windows is running fine under wine, flash an' all ...

too weird, this.

Mzwo

---

### Post by Mzwo on 2009-02-04
uninstalled flash - no change. firefox 3 still not working.




what now?

Mzwo

---

### Post by Mzwo on 2009-02-04
problem solved!!

solution was found here:[URL="http://kb.mozillazine.org/Locked_or_damaged_places.sqlite"] http://kb.mozillazine.org/Lock...
[/URL]

all it took was to delete files named "places.sqlite"

many thanks to all those who helped.

Mzwo

---

