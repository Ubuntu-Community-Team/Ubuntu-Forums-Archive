---
title: "HowTo run a script after RESUME [LUCID]"
date: 2010-05-15
forum: Desktop Environments
---

### Post by produnis on 2010-05-15
Hi folks,

here is my workaround on how to run a script after the PC resumes from suspend.

This is at least working on Lucid Lynx.

1. Have a look at folder **/etc/pm/sleep.d/** - all scripts within this folder are automatically run as root-user after/before suspend or hibernate.
2. A script needs to look like this example:
```

#!/bin/bash
case "$1" in
    hibernate|suspend)
        ACTION BEFORE SUSPEND/HIBERNATE
        ;;
    thaw|resume)
        ACTION AFTER RESUME
        ;;
    *)
        ;;
esac
exit $?

```

**EXAMPLE:**
Let's say you want to run ```
/etc/init.d/icecast2 restart
``` after resume. 
Here is what you need to do:

Type in a terminal:
```
sudo touch /etc/pm/sleep.de/99-icecast-restart.sh
sudo chmod +x /etc/pm/sleep.de/99-icecast-restart.sh
sudo nano /etc/pm/sleep.de/99-icecast-restart.sh
```Then give it the following content:
```

#!/bin/bash
case "$1" in
    thaw|resume)
        /etc/init.d/icecast2 restart 2>/dev/null
        ;;
    *)
        ;;
esac
exit $?

```
That's all
:-)


Hope this is helpful to anybody, because I spent hours to google for it.

German version: [here]("http://www.produnis.de/blog/?p=1236")

---

### Post by danwood76 on 2010-05-15
Thanks,

I was looking for just this to get madwifi to reload after hibernation!

best regards,
Danny

---

### Post by pp7 on 2010-07-27
Thanks alot for this.  I just love when people in the community give out information like this so freely! :)

---

### Post by henriquemaia on 2010-10-16
Thanks a lot for this tutorial and example. I had tried before some other explanations I found while googling to no avail, but yours did the trick.

[IMG]https://addons.mozilla.org/en-US/firefox/images/addon_icon/162124/1283212251[/IMG]

---

### Post by SaintDanBert on 2010-11-04
Are there any rules or restrictions about what commands or programs can appear in these scripts?

Specifically, can I use **logger** to add my own details into the suspend and resume logs -- or even create my own logs?

Also, I need to make sure than any USB or SD media are unmounted prior to suspend processing. There are known troubles with external devices and suspend-resume success.

Lastly, if there are several connected but un-mounted USB or flash drives, is there some command that will "force" some sort of scan and re-mount of the whole crop?

Merci d'avance,
~~~ 0;-Dan

---

### Post by skullriot on 2010-11-20
Hopefully this isnt dead, But i cant seem to get my two finger scroll scrip to run after resume from suspend. 

I just put 10.10 on my eee 1001p, and finally got the brightness and two finger scrolling to work. 

A couple problems, and this is the thread that I keep getting sent to in my searches. I'm a very new user, and what I am doing doesn't seem to work. I got the script to run by putting it in the start up thing, but it seems to be a common problem that some scripts get shut off after you re open the laptop. 

uh... well i think you all know what im talking about. Here is what i made: 
```
#!/bin/bash
case "$1" in
    thaw|resume)
    /boot/twofinger
        ;;
    *)
        ;;
esac
exit $?
```
Contents of /boot/twofinger:

```
#
# Synaptics TouchPad 2 finger Scrolling
#
sleep 10
# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
```And i ran the sudo chmod +x on my script, so it does run at boot, just not resume.

I tried your commands, but i don't understand why the file name is different in that touch, nano and chmod commands... 

thanks for the help.

---

### Post by SaintDanBert on 2010-11-21
> **skullriot said:**
> 
...
I tried your commands, but i don't understand why the file name is different in that touch, nano and chmod commands
... 


software looks for scripts and script parts in specific locations depending on whether it is power-management or udev or udrive or acpi or "upstart" or ... that is trying to do something. I suspect that the relevant parts are not looking or finding your **/boot/twofinger** script in spite of your explicit absolute reference.

I'm not yet sure of the details myself, but I think that you need something like in **/etc/pm/*/NN_twofinger** where NN is two digits that manage the desired order of execution. I have no idea what "*" would need to be.

~~~ 0;-Dan

---

### Post by skullriot on 2010-11-22
Well the OP specifically states that sleep.d is what gets run before and after a suspend action. Maybe this kind of a script was changed in 10.10 and doesn't run the same way, not that I have had experience with this in 10.4. Karmic was my first Ubuntu. The boot order would make sense, though. I will try that out.

It would probably help me to look up documentation on what those specific commands do, considering I only know that chmod +x makes the file executable.

---

### Post by SaintDanBert on 2010-11-22
You don't say what name you used for the script-fragment with the case statement. I believe you want something like "/etc/pm/sleep.d/NN_somename.sh" (the file type is optional but a fetish of mine).
I believe that files execute in shell glob order and so the NN gets used to help sequence things.

Check out **man bash** or any of several available shell scripting books and articles.

The "$1" calls for the first command line parameter when the script is launched. "parameters" are parts of the command line separated by whitespace -- blanks, tabs, continuations, etc. In this case, you might see string values of "hibernate" or "suspend" or "resume" or "thaw".

"Hibernate" means suspend-to-disk.
"Suspend" means "suspend-to-ram.
"Resume" means "restart after either form of suspend-to".
"Thaw" (I think) means a synomyn for "resume."

Your script fragment then does some processing for either form of "resume".

Within the twofinger script, "sleep" inserts a run-time pause into whatever happens. I suspect this is a way to allow time for X-windows to start and run and be ready for what follows. Perhaps your delay is not long enough. There are ways to wait for something specific rather than wheel spinning.

Next "xinput" is the command that tells your X-server all sorts of details. Start with **man xinput** and keep reading (grin) for the rest of your geekish life. If these several device strings do not match exactly, things won't happen. Try **xinput --list** to see which devices you really have available and check your typing.

Are your **/var/log/Xorg.*.log** files saying anything about what is and is not happening?

~~~ 0;-Dan

---

### Post by needlez6 on 2011-03-16
Hey wondering if there's a way to run something like this. I want to run a script at startup, as well as everytime someone logs into gdm, or logs back in from switch user/ unlock in screensaver. Not sure how this would be achieved. Thank you for taking the time, to look this over.

---

### Post by rocuan on 2011-04-18
Good Thread.

I am running into problems too.
Mine are specifically with the GDK environment being undefined
I believe scripts run from /etc/pm/sleep.d are executed before gnome is fully "awake"
so, trying to start a program like Pidgin will fail.

Started a thread on it but haven't had any hits as of post time : [http://ubuntuforums.org/showthread.php?p=10663041](http://ubuntuforums.org/showthread.php?p=10663041)

---

### Post by heathman001 on 2011-08-22
Thanks, this worked great for me on Natty.

---

### Post by sonicb00m on 2011-10-16
Thanks for the tip!

---

### Post by wildmanne39 on 2012-11-21
Old thread closed.

---

