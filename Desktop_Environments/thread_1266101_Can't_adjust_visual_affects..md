---
title: "Can't adjust visual affects."
date: 2009-09-14
forum: Desktop Environments
---

### Post by GroogFish on 2009-09-14
I was trying to enable windows and I saw someone said you should do this in the terminal-

compiz --replace -c emerald &

Well I did that and my visual affects broek. I reinstalled my drivers, completely removed compiz and emerald, ran system restore, and reinstalled my compiz and emerald. Now when I try and turn on visual affects the computer blinks a few times and then I get a message-

"Desktop effects could not be enabled"

So what should I do?

---

### Post by earthpigg on 2009-09-14
tell us more about this 'system restore', please?

---

### Post by snakeman21 on 2009-09-14
Yeah, so far as I know, there is no "system restore" function or program on Linux...  Perhaps you are mixing the name up with something else?

---

### Post by GroogFish on 2009-09-14
The system restore was in my boot menu.
It shows-

Ubuntu
Ubuntu (System Restore)
Windows XP

---

### Post by snakeman21 on 2009-09-14
I think it says "Ubuntu (Recovery Mode)"

Unless I am mistaken?

---

### Post by andrea000 on 2009-09-14
Before you do anything run compiz in the terminal and post
the output
> command:compiz

also have you ran compiz check?I dont think recovery
mode will undo what broke compiz but it will not hurt
you can try it.

---

### Post by GroogFish on 2009-09-14
> **andrea000 said:**
> Before you do anything run compiz in the terminal and post
the output


also have you ran compiz check?I dont think recovery
mode will undo what broke compiz but it will not hurt
you can try it.

If I try to run compiz my computer locks up. I tried command:compiz and compiz check though.

command:compiz
> micah@micah-comp:~$ command:compiz
bash: command:compiz: command not found


compiz check
> micah@micah-comp:~$ compiz check
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


---

### Post by andrea000 on 2009-09-14
Running compiz in the terminal shouldn't
lock your system up just open a terminal 
and type compiz then hit the enter key.
I'm sorry compiz was the command.

---

### Post by GroogFish on 2009-09-14
When I run compiz I get the same information as compiz check but it in addition locks up. The top bars of my windows also disappear.

---

### Post by andrea000 on 2009-09-14
Check to see if your running full screen support in compiz
I'M not sure were it is but turn it off if it's on there is
a bug in full screen support and only some ever see it.

---

### Post by GroogFish on 2009-09-14
The doesn't make any sense. Compiz full screen mode?
Googled it, nothing relevant came up.

---

### Post by andrea000 on 2009-09-14
not full screen mode full screen support

---

### Post by andrea000 on 2009-09-14
here read [this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159664") about it and a quick google search
will turn up more about it

---

### Post by theZoid on 2009-09-14
> **andrea000 said:**
> here read [this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159664") about it and a quick google search
will turn up more about it

Nice link, friend :wink:

---

### Post by andrea000 on 2009-09-15
> **theZoid said:**
> Nice link, friend :wink:

I ran into this when i first installed ubuntu 9 but
didn't think that was the problem then it hit me when the
post said top bars of my windows also disappear when compiz
was run in the terminal what was going on.I still don't know
for sure if that is the problem but it's a good place to start.

---

### Post by snakeman21 on 2009-09-15
> **andrea000 said:**
> I ran into this when i first installed ubuntu 9 but
didn't think that was the problem then it hit me when the
post said top bars of my windows also disappear when compiz
was run in the terminal what was going on.I still don't know
for sure if that is the problem but it's a good place to start.

The only time I've seen that happen is when you run either compiz or emerald --replace from the terminal, then close the terminal window.  It happens because closing the terminal kills the process.

---

