---
title: "[SOLVED] Backlight control from the command line"
date: 2009-01-04
forum: General Help
---

### Post by wilson47 on 2009-01-04
Hello all,

I try to avoid Ubuntu's GUI as much as possible, and prefer sticking to the CLI. One thing which I haven't quite managed 
to get full control of is my backlight on my laptop. I can modify the brightness by editing a file in /proc/acpi/..., 
but what I would really like to configure is a way for my backlight to shut off when my laptops lid is closed. Are there 
CLI versions of gnome-power-manager out there? Any suggestions, solutions, or directions to other forums are indeed 
quite appreciated. 

-Glen

---

### Post by wilson47 on 2009-01-04
It isn't that I dislike Ubuntu's GUI, I just get so distracted there... Less distractions on the CLI. I hope I didn't 
offend anyone! =)

---

### Post by DefineByte on 2009-01-04
I think you'd be looking at using setterm for that. Something like *setterm -powersave powerdown* should turn the backlight off. *man setterm* may shed some light if that doesn't work.

If you find a command that works you'll probably need to edit */etc/acpi/lid.sh* to have it run when the lid is closed.

---

### Post by wilson47 on 2009-01-04
None of the possible 
```
setterm -powersave <something>
```
work with my computer... I found an old fix, but it requires recompiling the kernel which is currently beyond my skill level. I will keep pursuing this unless there are any other ideas. Thank you for a very helpful starting point! 

-Glen

---

### Post by wilson47 on 2009-01-06
I have found a way to manually shut off and turn on my monitor! It can be done with: 
```

sudo vbetool dpms off

sudo vbetool dpms on

```
The only part that stinks, is that I have to type in the "On" command without seeing anything... Is there 
a file which is automatically run upon my lid being opened? I tried to understand /etc/acpi/lid.sh, 
but I haven't gotten very far. In the meantime, I will just enter it in manually.

---

### Post by adult swim on 2009-01-06
i had to comment out the line ```
if [ `CheckPolicy` == 0 ]; then exit; fi
```
in /etc/acpi/lid.sh to get my backlight to turn off when the lid is closed.

---

### Post by wilson47 on 2009-01-07
Thank you for the suggestion! I tried it, but it sadly didn't help me on the CLI. I'm starting to understand the /etc/acpi/lid.sh file a bit, so if I can make something work, I'll post it. Unless of course somebody has a better solution!

---

### Post by DefineByte on 2009-01-07
I completely forgot about vbetool. I think I ended up using it myself. :oops:

You could try commenting out the whole of the first for...done statement and replacing it with 'vbetool off' and the second for...done with 'vbetool on'. It doesn't look like they'd run unless you were using X anyway. Possibly a bit of a stab in the dark.

---

### Post by wilson47 on 2009-01-07
Once again, thank you very much DefineByte! Your suggested change to the file /etc/acpi/lid.sh worked like a charm. To 
summarize, and be explicit for any others who may be searching for this, here is what to do:
1. Make a backup of /etc/acpi/lid.sh just in case this doesn't work.
2. Replace the contents of /etc/acpi/lid.sh with:
```

#!/bin/bash
# TODO:  Change the above to /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` = 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        vbetool dpms off
else
        vbetool dpms on
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```
and save. 
3. To get the configuration to take effect, run
```

sudo /etc/init.d/acpid restart

```
and that should do it!

---

### Post by wilson47 on 2009-01-07
I would just like to make one more observation on this. The default set up doesn't shut the backlight off even when it 
is at the login screen. With this new configuration, it works with X, on the console, at the login screen---everywhere 
that I can think of. What are the advantages to the current default? Would it make sense to make something along these 
lines the default? Of course it would have to be modified to allow the user to adjust the settings as they see fit; it 
is just something that I expect to happen when the lid is shut.

---

