---
title: "suspend previously working , now has stopped working on intrepid"
date: 2008-12-28
forum: General Help
---

### Post by macvr on 2008-12-28
hi all,

i'm using intrepid. on acer aspire 5672Wlmi laptop...

i was able to use the suspend / hibernate functions in my laptop until a few days ago...

once while resuming from suspend i accidentally pressed the power button...
instead of resuming the system just shutdown!

ever since this happened suspend and hibernate doesnt work!

i thought that the swap was probably not loading properly and did this after a bit of googling
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda6
sudo swapon -a
```

but now my uuid has changed! [i'm not sure if doing the above commands has changed the uuid or changed after the abrupt shutdown?:confused:]

i have set the correct uuid in the fstab and the swap is working,
i'v checked using 'free' command

but still the suspend/ hibernate are not working :confused:


how do i get the suspend /hibernate to work again?

---

### Post by Elfy on 2008-12-28
Check and change if necessary the swap UUID in 

```
sudo nano /etc/initramfs-tools/conf.d/resume
```

Once amended run

```
sudo update-initramfs -u
```

---

### Post by macvr on 2008-12-28
> **forestpixie said:**
> Check and change if necessary the swap UUID in 

```
sudo nano /etc/initramfs-tools/conf.d/resume
```

Once amended run

```
sudo update-initramfs -u
```

did the above , also restarted
 but suspend/hibernate dont work still!

they both only lock the screen!

any ideas?

---

### Post by Elfy on 2008-12-28
Sorry no - all I could suggest would be check back and see if you got any updates that might have caused it or have reported bugs.

---

### Post by macvr on 2008-12-28
> **forestpixie said:**
> Sorry no - all I could suggest would be check back and see if you got any updates that might have caused it or have reported bugs.

ok... thanx...
i dont think that the updates caused it... because after the **abrupt shutdown [which happened DURING RESUME FROM SUSPEND]** i noticed the problem , before i got any updates...

 any ideas how the uuid got changed? was the swapoff and swapon the reason for the change or would the abrupt shutdown have changed the uuid...

---

### Post by Elfy on 2008-12-28
swapoff or swapon shouldn't have changed the uuid - I do it fairly frequently

I would hazard a guess that the abrupt shutdown could have - I've had a quick search,as I'm sure you have, but can't see much 

I'll have another look later as well and ask on some of the irc channels I use

---

### Post by macvr on 2008-12-28
> **forestpixie said:**
> swapoff or swapon shouldn't have changed the uuid - I do it fairly frequently

I would hazard a guess that the abrupt shutdown could have - I've had a quick search,as I'm sure you have, but can't see much 

I'll have another look later as well and ask on some of the irc channels I use

ya, i'v been googling , but the results seem to be only for suspend problems due to hardware incompatibility and other issues....

this seems to be a freak case , i'v tried #ubuntu also but noone seems to know the solution :confused:

[COLOR="Blue"]please get back to me if u find a solution... [/COLOR]i'm just a noob ,  so there is noway i can figure this out by myself!

---

### Post by macvr on 2008-12-28
/var/log/pm-suspend.log 
```
Initial commandline parameters: 
Sat Dec 27 16:26:15 IST 2008: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Sat Dec 27 16:26:17 IST 2008: performing suspend
```

this seems to be the last time suspend worked... could it be a power manager problem?

but when i change the settings in the power manager to ask me, i get the prompt for the shutdown/suspend but suspend doesnt work!

---

### Post by Elfy on 2008-12-28
> **macvr said:**
> ya, i'v been googling , but the results seem to be only for suspend problems due to hardware incompatibility and other issues....

this seems to be a freak case , i'v tried #ubuntu also but noone seems to know the solution :confused:

[COLOR="Blue"]please get back to me if u find a solution... [/COLOR]i'm just a noob ,  so there is noway i can figure this out by myself!

Yea - I will - I'm subscribed to the thread so if you ifnd anything post back.

I've not been here much longer than you so just as noob 

#ubuntu is a bit of a hrad place to find anything out I've found ;)

Personally I've only tried suspend/hibernate once and it didn't work too well for me - so stopped worrying, probably would have carried on with a laptop

---

### Post by macvr on 2008-12-28
> **forestpixie said:**
> Yea - I will - I'm subscribed to the thread so if you ifnd anything post back.

I've not been here much longer than you so just as noob 

#ubuntu is a bit of a hrad place to find anything out I've found ;)

Personally I've only tried suspend/hibernate once and it didn't work too well for me - so stopped worrying, probably would have carried on with a laptop

will report back too...

any other irc i could check out for help?

---

### Post by Elfy on 2008-12-28
I intend to ask in the beginners team - but the person I want to ask is not there atm - it's not really a help channel as such, beginners-help is but it's opnly got me there at the moment anyway.

There might be a loco team for where you live - [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)


I'll be flagging it on the unanswered team later as well.

---

### Post by macvr on 2008-12-28
ok... i'v done further digging...

i'v run>
```

cd /usr/lib/hal/scripts
sudo ./hal-system-power-hibernate
sudo ./hal-system-power-suspend
```

for both the commands i get this error!
```
 .: 3: hal-functions: not found
```

my hal-functions file>
```
# -*-Shell-script-*-
#
# hal-functions         This file contains functions to be used by most or all
#                       hal shell scripts

hal_check_priv() {
    if [ "$HAVE_POLKIT" = "1" -a -n $HAL_METHOD_INVOKED_BY_SYSTEMBUS_CONNECTION_NAME ]; then
        local ACTION
        local PK_RESULT
        local RET
        ACTION=$1
        PK_RESULT=`hal-is-caller-privileged --udi $UDI --action $ACTION \
            --caller $HAL_METHOD_INVOKED_BY_SYSTEMBUS_CONNECTION_NAME`
        RET=$?
        if [ "$RET" != "0" ]; then
            echo "org.freedesktop.Hal.Device.Error" >&2
            echo "Cannot determine if caller is privileged" >&2
            exit 1
        fi
        if [ "$PK_RESULT" != "yes" ] ;then
            echo "org.freedesktop.Hal.Device.PermissionDeniedByPolicy" >&2
            echo "$ACTION $PK_RESULT <-- (action, result)" >&2
            exit 1
        fi
    fi
}

hal_call_backend() {
    local PROGRAM
    PROGRAM=$(basename $0)
    if [ -n "$HALD_UNAME_S" -a -x ./$HALD_UNAME_S/$PROGRAM-$HALD_UNAME_S ]; then
        ./$HALD_UNAME_S/$PROGRAM-$HALD_UNAME_S $@
    else
        echo "org.freedesktop.Hal.Device.UnknownError" >&2
        echo "No back-end for your operating system" >&2
        exit 1
    fi
}

hal_exec_backend() {
    local PROGRAM
    PROGRAM=$(basename $0)
    if [ -n "$HALD_UNAME_S" -a -x ./$HALD_UNAME_S/$PROGRAM-$HALD_UNAME_S ]; then
        exec ./$HALD_UNAME_S/$PROGRAM-$HALD_UNAME_S $@
    else
        echo "org.freedesktop.Hal.Device.UnknownError" >&2
        echo "No back-end for your operating system" >&2
        exit 1
    fi
}
```

so i tired reinstalling hal>
```
sudo apt-get install --reinstall hal
```

no use... still same error!

---

### Post by macvr on 2008-12-30
anyone has any ideas how to resolve this problem?

---

### Post by macvr on 2009-01-02
bump?

---

### Post by macvr on 2009-01-05
bumping!!! need urgent help

i'v tried this

```
~$ echo /usr/lib/hal/scripts/hal-system-power-suspend
/usr/lib/hal/scripts/hal-system-power-suspend


~$ echo /usr/lib/hal/scripts/hal-functions
/usr/lib/hal/scripts/hal-functions
```

so i guess the file is being found, but when i run it i says
```
~$ sudo /usr/lib/hal/scripts/hal-system-power-suspend
.: 3: hal-functions: not found
```

i tried renaming hal-functions file to '.hal-functions' '. hal-functions' but i got the same error only!

---

### Post by ColombianGold on 2009-03-12
bump 

Hi macvr!
Did you resolve the problem?
I have the same thing....when I suspend/hibernate all that happens is that my sceens locks up.

Will suscribe to post.

---

### Post by macvr on 2009-03-12
> **ColombianGold said:**
> bump 

Hi macvr!
Did you resolve the problem?
I have the same thing....when I suspend/hibernate all that happens is that my sceens locks up.

Will suscribe to post.

hi...
i tried everywhere, this problem was never solved...

**_but since my suspend/hibernate worked previously_**, i just reinstalled 8.10

[COLOR="DarkRed"]**I WOULD SUGGEST A REINSTALL , SINCE I FOUND NO SOLUTION FOR THIS SPECIFIC PROBLEM**[/COLOR], and i dont think there might be a fix for this since this seems to be a freak problem!


[COLOR="Green"]**reinstalling ubuntu is soooo easy **[/COLOR], since all the installed programs are in the repos and u dont have to go around looking/remembering what programs u had installed

if u plan on reinstalling and have a separate /home partition... check these methods... its very simple, no need any other reconfiguration..., maybe a few :
[http://ubuntuforums.org/showpost.php?p=6660813&postcount=1]("http://ubuntuforums.org/showpost.php?p=6660813&postcount=1")

[http://ubuntuforums.org/showpost.php?p=6870536&postcount=13]("http://ubuntuforums.org/showpost.php?p=6870536&postcount=13")


but if u have any other solutions, let me know, might be of use if i have a repeat of the same problem ;)

---

