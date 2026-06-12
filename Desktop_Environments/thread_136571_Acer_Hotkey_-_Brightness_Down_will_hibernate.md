---
title: "Acer Hotkey - Brightness Down will hibernate"
date: 2006-02-26
forum: Desktop Environments
---

### Post by momox on 2006-02-26
Hi all,

question from a (quasi) newbie

I have an Acer Aspire 1652 wlmi, kernel 2.6.12 custom.

I have hotkey-setup and acerhk modules loaded.

Most hotkey combinations work properly.
The most annoying thing is that whenever I do the Brightness Down command (Fn + LeftArrow) my laptop hibernates.

both bum, sysv-rc-conf, and lsmod say modules are mounted.
In bum, hotkey-setup is not tikced in the script sesction (but it tells me I cannot modify that from the program).


/usr/share/hotkey-setup has an "acer.hk" file.

Here is what it says:

# Help key
setkeycodes e025 168

# Misc 1
setkeycodes e074 239 

# Misc 2
setkeycodes e073 236 

# Unset brightness down - by default, it generates the hibernate keycode
setkeycodes 70 256



I tried everything with the last two lines, both uncommentig the first and commenting the second. Nothing changes.

The same folder has a generic.hk, saying

# Disable keys that may generate a hibernate event
setkeycodes 5d 256
setkeycodes e02a 256
setkeycodes e06f 256


I tried to add the keycode of the last line of the file acer.hk.
Nothing changes again.

Can anybody help me with this?

Do I have to do any mapping with the keys? Is there any way to avoid that? If not, how can I do it?

Changing brighteness is essential to me for saving battery and preventing fan noise when working on batteries.
(by the way, is there any othe way I can change the sreen's brightness even if this thin can't get fixed soon?)

Thanks for any help,

momox

---

### Post by momox on 2006-02-27
Nobody has the same problem?
Nobody knows any solutions to it...??

Please...

momox

---

### Post by momox on 2006-03-02
Hi, just to let anyone reading know...

I disabled and removed both the **hibernate** package and the **hotkey-setup** module, and also the **acerhk** module.

Nothing changes. Funny thing is that neither seems to be required for all other hotkeys to work, nor for any keyboard combinations.

**Acerhk**, module, though, seems automatically reloaded at startup. Might be the problem? Is there a way I can completely remove it? I did "sudo rmmod acerhk", then I check with lsmod and the module is gone. At reboot it is there again. How could I remove it once for all?

However, 

The most important combinations with Fn works fine. Volume up and down (Fn + ArrowUP/ArrowDown) works great.

I've seen that other Fn combinations don't work. Of all, Fn combinations that should emulate the numeric pad, only that for -, *, and + work, those for numbers don't, nor that for "." (dot), which instead emulates the Canc key

EVEN **Brightness Up** (Fn + RightArrow) works great.
Moreover, the acpi brightness conrol works fine (when I unplug the AC screen's brightness goes down, as supposed in order to save battery).


STILL. **brightness down** (Fn + LeftArrow) will **hibernate** my laptop...

Anybody knows where I could look for an answer? I spent days googling, nothing found.

Still don't know how to reduce brightness without hibernating my laptpop....

](*,)

---

### Post by djtm on 2008-03-10
Hey, I can change my brightness by issuing
echo x > /sys/class/backlight/acer_acpi/brightness
as superuser.
whereas x is a number between 0 and /sys/class/backlight/acer_acpi/brightness.

---

