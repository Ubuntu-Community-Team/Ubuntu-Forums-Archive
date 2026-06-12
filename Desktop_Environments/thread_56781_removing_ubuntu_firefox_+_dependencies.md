---
title: "removing ubuntu firefox + dependencies"
date: 2005-08-14
forum: Desktop Environments
---

### Post by desheikh on 2005-08-14
I want to remove the firefox I installed via the ubuntu repository and install it from the mozilla website (heard its faster)...but I also want to remove all the dependencies that were installed with firefox.. could somebody please tell me how to do that or provide the list of dependencies so i can remove them manually.

Thanks,
Ali

---

### Post by heimo on 2005-08-14
These may help:

[http://www.ubuntuforums.org/showthread.php?t=53176](http://www.ubuntuforums.org/showthread.php?t=53176)
[http://www.ubuntuforums.org/showthread.php?t=53150](http://www.ubuntuforums.org/showthread.php?t=53150)

---

### Post by desheikh on 2005-08-14
Thanks! ill try deborphan out and see what happens..

---

### Post by desheikh on 2005-08-14
Thanks Deborphan is perfect.. installed firefox from the mozilla website and its working a lot faster now.. 
im trying to add firefox to the kde menu but cant figure out what to add in the command: and workpath: area :S
any help there? :)

---

### Post by desheikh on 2005-08-14
Another problem is that flash does not seem to be working with the firefox from the mozilla website :S how do i get that done? already installed java and flash via apt

---

### Post by heimo on 2005-08-14
[QUOTE=desheikh]Thanks Deborphan is perfect.. installed firefox from the mozilla website and its working a lot faster now.. 
im trying to add firefox to the kde menu but cant figure out what to add in the command: and workpath: area :S
any help there? :)[/QUOTE]

Probably command is *firefox* or [i]mozilla-firefox

[/i]I don't know if this will work, but maybe:
[http://www.ubuntuguide.org/#flash-mozilla]("http://www.ubuntuguide.org/#flash-mozilla")

EDIT: For workpath, probably not needed, but if it's required field, try /tmp
EDIT2: See below.

---

### Post by desheikh on 2005-08-14
No thats the problem niether firefox nor mozilla-firefox work...
for the menu i need to ./firefox from /opt/firefox but i dunno how to put that in the kmenu settings
and iv already installed the mozilla-flashplayer through ubuntuguide.org and thats not working :(

---

### Post by roland on 2005-08-14
The path entry is the path where the firefox binary is located. It is most probably not needed, but /tmp will not work. You could type [font=courier]which firefox[/font] in a terminal window (Applications - Terminal) to find out where it is located. Don't forget to click the Apply button after changing settings.

---

### Post by desheikh on 2005-08-14
Ok figured out the command i need to put in.. its '/opt/firefox/firefox' with the colons dunno why but it works :P
anyways has anyone installed firefox from the mozilla website?... still cant get java and flash to work with it :S

---

### Post by z-vet on 2005-08-14
Yes, i have Firefox installed manually. To install java and flash player follow the instructions given on  [this page.](http://plugindoc.mozdev.org/linux.html)

---

### Post by yhotg on 2005-08-15
hi.

I had installed manually the firefox from the mozilla site.
For reasons that i can't really remember now (i think that has something to do with not been able to make kde to use firefox by default and tired of having to close konqueror and open firefox...) i installed the kubuntu/ubuntu firefox.

for a while oi had both firefox side by side and one day deleted the manually installed.
My question is: is it really faster, the firefox from the mozilla site? how come?
and if it is so, it worth to make the change back? and having to re configure all the plug ins and so on?


[COLOR=Teal]desheikh[/COLOR]:
to put the firefox on the menu you need to go to the "K menu" on the panel
there if u click with the right button u can chose edit menu
in the KDE menu editor u can add items.
where it says "command" u need to fill: 
[COLOR=SandyBrown]/opt/firefox/firefox[/COLOR]

now for the java and flash
[http://www.mozilla.org/products/firefox/central#central-engines](http://www.mozilla.org/products/firefox/central#central-engines)
there u have the "Get Common Plugins"
 follow the instructions there.  :grin: 


yhotg

---

### Post by Gezzer on 2005-08-15
this may help if you require realPlayer working in your stand alone install of firefox
i got RP working in a stand alone install of FF 1.0.6 this way ...

i downloaded & installed FF to a folder on my home partition
i then installed RP via synaptic (it wouldn't work at this stage)

i then downloaded RP from there site untar to a folder then remove the "mozilla" folder from the RP folder
which contains the two plugins that are needed (i then deleted the RP folder)

in the FF folder i placed a copy of the plugins from the "mozilla" folder
nphelix.xpt to the components folder within the FF folder
nphelix.so to plugins folder within the FF folder

RP now works with everything using FF 1.0.6 as a standalone install on my home partition using RP which was installed via synaptic ...

---

### Post by desheikh on 2005-08-16
Hmm thanks.. ill give that link a shot and see if it works... In my experiance the firefox from the mozilla website is considerably faster than the one on the ubuntu repo... 
Thanks for the realplayer tip ;).. ill give that a shot too

---

