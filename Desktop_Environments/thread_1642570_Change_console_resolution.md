---
title: "Change console resolution???"
date: 2010-12-10
forum: Desktop Environments
---

### Post by Eremis on 2010-12-10
Hi guys,

I was wondering how would I change my console resolution (ctl+alt+f1 - f6) under ubuntu 10.4?

I found a lot of tutorials where they require you to change something in menu.lst file, but ubuntu 10.04 uses grub2 and insted of that file there's only "/etc/default/grub" where I can change 
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

```

--> #GRUB_GFXMODE=640x480

but is this even it?
I think this will change the grub resolution, not the console resolution...
Am I right?
How would i change it?

I use proprietary nvidia drive rnvidia 96
I have nvidia MX440, very old card

I like working in console so I was wondering if anyone can help me make it better. 

PS.

Also want to know how to change syntax colors in console, so it will look gentoo'ish, plz dont tell me to switch to gentoo...

---

### Post by sisco311 on 2010-12-10
You can use the GRUB_GFXPAYLOAD_LINUX variable to change the vc resolution, e.g.:
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

```
or
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=1024x768

```
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by Krytarik on 2010-12-10
For me only the second option worked (naming the resolution twice).

---

### Post by gaelicbright on 2010-12-10
The standard size of the console is 80 columns and 25 rows, which is too large, if you want to work easily and the console does not even use the desktop environment. It will also look better when you turn on the system. You can change the resolution and color depth of the console have to edit / boot / grub / menu.lst and add a line parameter contains the kernel to boot.

---

### Post by Krytarik on 2010-12-11
> **gaelicbright said:**
> The standard size of the console is 80 columns and 25 rows, which is too large, if you want to work easily and the console does not even use the desktop environment. It will also look better when you turn on the system. You can change the resolution and color depth of the console have to edit / boot / grub / menu.lst and add a line parameter contains the kernel to boot.
gaelicbright is obviously talking about GRUB (version 1), not GRUB2, which is the default bootloader since Ubuntu 9.10.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

@Eremis: please update the Ubuntu-version in your profile, if it's adequate, to avoid those misunderstandings.;-)

---

### Post by Eremis on 2010-12-11
Thanks for the help, I will try it and come back to the post tommorow.
However I am wondering, why does this have to do with grub? I am trying to change the console res of ubuntu, not a boot manager.

Can you explain what does boot manager have to do with ubuntu console?

Thx

---

### Post by Eremis on 2010-12-11
Just tried it,

Now I got a bigger problem. My nvidia graphics drivers stoped working properly.
Before I loged in the system asked me if I wanted to reconfigure xorg, so I said yes and restarted. After reconfiguring the nvidia drivers are not used, and desktop composition is not enabled...

How would I fix this?

When I go to System --> Admin --> Hardware Drivers it says that driver is currently activated and in use however, then I try to enable effects it says that it can not do so...

How would I get nvidia drivers to work again?

---

### Post by Krytarik on 2010-12-11
> **Eremis said:**
> Just tried it,

Now I got a bigger problem. My nvidia graphics drivers stoped working properly.
Before I loged in the system asked me if I wanted to reconfigure xorg, so I said yes and restarted. After reconfiguring the nvidia drivers are not used, and desktop composition is not enabled...

How would I fix this?

When I go to System --> Admin --> Hardware Drivers it says that driver is currently activated and in use however, then I try to enable effects it says that it can not do so...

How would I get nvidia drivers to work again?
Set the X-Server-options via the tool "NVIDIA X Server Settings" in "System -> Administration" and save the settings to the "X Configuration File", replace, not merge.
It's usually not such a good idea to choose the reconfig-option when failing to load the desktop, it makes things worse.;)

Actually I've tried a number of options, just today, the above mentioned works for me, at least now.:-s
I've set up the (higher) resolution another way, before I read this post, was not happy with the old config either.

You may also try this solution: [http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html:](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html:) insert "set gfxpayload=keep" into "/etc/grub.d/00_header" instead of the option in "/etc/default/grub".

---

### Post by Eremis on 2010-12-11
After going to NVIDIA X Server settings, I got a message box telling me to run: "nvidia-xconfig" After doing so I got the following output:
<code>
XXXXXX@linux-machine:~$ sudo nvidia-xconfig
[sudo] password for andriy: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

XXXXXX@linux-machine:~$ 
</code>

Then I restarted and again I got the screen where it told me that ubuntu is running in low graphics mode and it aksed me what I wanted to do...
Here some of the options;
* Use default generic confic (The one choose)
* Create new config file for the hardware
* Use ur backed up config

Now again the graphics dont work...

Any other solution?

---

### Post by Krytarik on 2010-12-11
Have you changed the /etc/default/grub and the /etc/grub.d/00_header following my advice before reboot?;)

When you are given the options after the desktop failed to load always choose "low-graphics-mode", the xorg.conf will not be changed then.

---

### Post by Eremis on 2010-12-11
here is my header file, no line with /etc/default/grub in it...

```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`
locale_dir=`echo /boot/grub/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d _ -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  set saved_entry=\${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z \${boot_once} ]; then
    saved_entry=\${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n \${have_grubenv} ]; then if [ -z \${boot_once} ]; then save_env recordfail; fi; fi
}
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
EOF
if [ x$GRUB_THEME != x ] && [ -f $GRUB_THEME ] \
	&& is_path_readable_by_grub $GRUB_THEME; then
    echo "Found theme: $GRUB_THEME" >&2
    prepare_grub_to_access_device `${grub_probe} --target=device $GRUB_THEME` | sed -e "s/^/  /"
    cat << EOF
  insmod gfxmenu
  set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
  set menuviewer=gfxmenu
EOF
fi
    cat << EOF
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

# Gettext variables and module
if [ "x${LANG}" != "xC" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir})
  cat << EOF
set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
set lang=${grub_lang}
insmod gettext
EOF
fi

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  cat << EOF
insmod play
play ${GRUB_INIT_TUNE}
EOF
fi

```

---

### Post by Krytarik on 2010-12-11
Ok, once again, my file /etc/default/grub looks like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600
GRUB_GFXPAYLOAD_LINUX=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
This works for me. 

I also tried the way to insert
```
set gfxpayload=keep
```
into the file /etc/grub.d/00_header, like this:
```
<---- snip ---->
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
set gfxmode=${GRUB_GFXMODE}
set gfxpayload=keep
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
EOF
<---- snip ---->
```
This way you have to remove the "GRUB_GFXPAYLOAD_LINUX"-entry from the file /etc/default/grub!

This way worked for me also.

---

### Post by Eremis on 2010-12-11
I just changed it back and reverded all the changes and graphics work again....

---

### Post by Eremis on 2010-12-11
I will try the way you told me above next week (after college exams...)
a little busy now,

thx for the help so far!

---

### Post by tekkidd on 2010-12-11
Install a program called startup manager ```
sudo apt-get install startupmanager
```it can be accessed in System>Administration. From their you can change the resolution of the console.

---

### Post by subjucha on 2010-12-29
So, how to change resolution of console? Changing parameters of GRUB doesn't help. Passing vga=xxx to kernel doesn't work. And I have only terminal without any desktop (it is a server), so I can't install Startupmanager. I have read completely this forum about changing of resolution of console and there isn't a solution. Let's find it!

May be you have to use fbset command?

---

### Post by Krytarik on 2010-12-29
> **subjucha said:**
> So, how to change resolution of console? Changing parameters of GRUB doesn't help. Passing vga=xxx to kernel doesn't work. And I have only terminal without any desktop (it is a server), so I can't install Startupmanager. I have read completely this forum about changing of resolution of console and there isn't a solution. Let's find it!

May be you have to use fbset command?
Have you tried my instructions posted above?! It should work for non-desktop systems as well.

---

### Post by subjucha on 2010-12-29
Yes, I've tried both your methods: setting GRUB_GFXPAYLOAD_LINUX and inserting **set gfxpayload=keep**.

They don't work on my system (Ubuntu 10.04).

---

### Post by Krytarik on 2010-12-29
Then try this solution:

[http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/](http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/)

---

### Post by subjucha on 2010-12-30
Yes, this helped me! The resolution sets as what I want.
I was searching the solution during 4 days. And this work is for a product of our company in Russia. Krytarik, thank you a lot!!!

---

### Post by Krytarik on 2010-12-31
You're welcome, glad that I could help you.:-) Thanks for the feedback.

---

### Post by r_widell on 2011-01-11
> **Eremis said:**
> Thanks for the help, I will try it and come back to the post tommorow.
However I am wondering, why does this have to do with grub? I am trying to change the console res of ubuntu, not a boot manager.

Can you explain what does boot manager have to do with ubuntu console?

Thx
I have been having the same problem with an install of Kubuntu 10.04LTS on one of my newer machines. The default resolution on the hardware is 1600x1280, which is way too small for these tired old eyes on a 17" monitor. Reading the initial answers, I had the same question about Grub vs. Linux resolution. Doing a little more searching, I came upon this post which provides the magic key:
[http://forums.debian.net/viewtopic.php?f=5&t=56932#p330266](http://forums.debian.net/viewtopic.php?f=5&t=56932#p330266)

So the new KMS kernels, when used with appropriate graphics cards no longer support the old VGA=xxx argument. The new argument passed to the kernel is in the form of video=HHHHxVVV[-DD]. I tried it by interrupting Grub at bootup and editing the kernel= line (Grub legacy) to add video=800x600 and then escaped back to boot with that argument passed to the kernel. It worked! I had 1600x1280 resolution in graphics mode and 800x600 on the text mode virtual consoles.
It appears to me from reading the Grub2 docs that setting those previously referenced variables are just a way of eventually getting that arg passed to the kernel by Grub.

---

