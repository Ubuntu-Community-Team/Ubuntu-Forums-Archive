---
title: "compiz no more desktop effect's"
date: 2009-04-24
forum: Desktop Environments
---

### Post by andrea000 on 2009-04-24
When i ran 8.04 compiz ran fine and when i upgraded to 8.10 it stopped for some reason i tried 
to run compiz it said more then one chip sets running can not continue.I found one integrated 
card but it was disabled i also had 2 nvidia drivers installed 173 and 177 so i disabled 173 on 
that but it still says desktop effects could not be enabled.I looked and my card is not blacklisted.
Could someone lease help me.

---

### Post by jamessnell on 2009-04-25
> **andrea000 said:**
> When i ran 8.04 compiz ran fine and when i upgraded to 8.10 it stopped for some reason i tried 
to run compiz it said more then one chip sets running can not continue.I found one integrated 
card but it was disabled i also had 2 nvidia drivers installed 173 and 177 so i disabled 173 on 
that but it still says desktop effects could not be enabled.I looked and my card is not blacklisted.
Could someone lease help me.

Sounds like you're using the restricted drivers manager?

You could try getting the nvidia driver directly from the nvidia website.. Download that and run the installer from the command line.

Note that before you can run it in a terminal, you need to set the file as executable:
```
chmod +x <filename>
```

Then execute the file by running:
```
sudo ./<filename>
```

There may be other decent solutions, but there's one.. If you're comfortable giving that a try. :)

Another option is to perform a fresh install.. It's all a gamble of what'll cost ya less effort/time (unless you're excited to learn some plumbing stuff).

---

### Post by andrea000 on 2009-04-25
No luck with compiz after i installing from there website
i did a compiz-replace and here is the log i get from that

me@me-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "ubuntulooks",

so i guess my card or driver is blacklisted after all?
Why would it be and is there a work around.

---

### Post by jamessnell on 2009-04-25
> **andrea000 said:**
> No luck with compiz after i installing from there website
i did a compiz-replace and here is the log i get from that

me@me-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "ubuntulooks",

so i guess my card or driver is blacklisted after all?
Why would it be and is there a work around.

No, it sounds like the new ATI Catalyst driver doesn't support your particular card. I've seen this issue on at least two other threads. Could you please post the results of an "lspci"?

Also, the work around is probably using open source drivers.. In your /etc/X11/xorg.conf, there's a video card driver line that sets what driver your video card is using, if you can execute the following without obvious errors:
```
sudo modprobe radeon
```

Then in that case, I'd suggest you replace the driver line in xorg.conf to being "radeon" - that's the open source driver, it isn't as good as using a proprietary driver, however, sounds like that may be your only option. Well, I guess you could also use the "vesa" driver, which can save ya in a real bind.

---

### Post by andrea000 on 2009-04-25
I found the problem from a blog i have a Intel integrated card it's
turned off but compiz still see's it and thanks it's in use thats
the card that is blacklisted now just fixing it is the problem.
how would i go about telling compiz that that card is not in use?

---

### Post by andrea000 on 2009-04-25
Ok i have desktop effect's now after some editing but i need some
help slowing them down here is what i did i took this

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T=" 1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" "[COLOR="Red"]]intel[/COLOR] 965[/COLOR]
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
BLACKLIST_PCIIDS="$T"
unset T

and turned it into this

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T=" 1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
BLACKLIST_PCIIDS="$T"
unset T


[COLOR="Yellow"][COLOR="Black"]theni right clicked the desktop and set the visual effects
then went to compiz setting manager and set my effects but
i had to type in [COLOR="Red"]class=[/COLOR]in the windows match box

anyone have any idea how to slow these effect's down some

---

### Post by jamessnell on 2009-04-25
That seems kind of like a different topic - I'd start a new thread if I were you.

---

