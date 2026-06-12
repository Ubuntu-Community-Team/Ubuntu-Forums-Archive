---
title: "custom DE session not working"
date: 2011-10-09
forum: Desktop Environments
---

### Post by runny6play on 2011-10-09
Im having troubling getting my custom GDM session to work.. can you help me figure out what im doing wrong?

my script file
```
#! bin/bash
openbox-session &
gnome-panel &
```
my .desktop file
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name[en_US]=Alecs desktop environment
Exec="/home/alec/scripts/A.D.E.sh"
Comment[en_US]= my DE
Name=Alecs desktop environment
Comment=my DE
Icon=
```
additional notes: 
*when i select it from GDM it loads gnome 3

---

### Post by Krytarik on 2011-10-09
GDM has no access to the content of your home directory at the time of login (however, it synchronizes your ".dmrc" and ".face" with its cache *after* login).

So, you need to place the script somewhere else; and also make sure that it's readable and executable for all.

Also, you can spare the "Terminal=false" part.

Regards.

---

### Post by runny6play on 2011-10-09
thanks for the reply.
I moved it to the same directory as the .desktop file and has permissions 755 the only difference is now it boots into gnome 3 faster.

the script does work from the recovery console

---

### Post by Krytarik on 2011-10-09
> **runny6play said:**
> the script does work from the recovery console
Yeah, might be, but unfortunately that doesn't mean that it works from GDM, too. So, you need to figure out what variables you might need to pass to make it work. I had to do so, too, when I was setting up a [Compiz Standalone]("https://help.ubuntu.com/community/CompizStandalone") session, for example.

---

### Post by runny6play on 2011-10-09
ugh. Linux.. a lot of work and troubleshooting. Can be quite fun though. it was first out of user error as i forgot to change the location of the file in the .desktop file but now that i have it initiates and then goes back to GDM. I think im going to try 
Terminal=true and see what happens.
thanks again for the help. I really appreciate it. nothings more frustrating than trying to solve a problem without the proper knowledge, poor documentation, (all I could find was information on how to make the .desktop file  and where to put it.) and you cannot find a more advanced user to help you troubleshoot.

---

### Post by Krytarik on 2011-10-09
> **runny6play said:**
> but now that i have it initiates and then goes back to GDM.
I had the exact same thing when setting up Compiz Standalone. :D
It's about those variables stuff; you can safely drop the Terminal option idea.

This is how my Compiz Standalone script looks like, maybe it helps:
```
#!/bin/bash
ck-launch-session dbus-launch --exit-with-session compiz ccp & wmpid=$! 
sleep 1
if [ -f ~/.compiz-session ]; then
    source ~/.compiz-session &
else
    gnome-terminal &
fi
# Wait for WM
wait $wmpid &
avant-window-navigator
```Also, now that I compared them, your crunchbang (first line of the script) is not correct!

---

### Post by runny6play on 2011-10-09
can you walk me through what your script is doing...  i get the basic idea of what its doing.. but i dont know the spefics and what some of those programs are that are being luanched

---

### Post by Krytarik on 2011-10-10
> **runny6play said:**
> can you walk me through what your script is doing...  i get the basic idea of what its doing.. but i dont know the spefics and what some of those programs are that are being luanched
Well, in complementation to the session script, I have the file "~/.compiz-session" in my home directory (only permissions of 644 needed, as it isn't run, but "sourced"):
```
gnome-settings-daemon &
pidgin &
smplayer &
parcellite &
alarmclock
```The apps specified there are, in addition to "avant-window-navigator" already run through the session script, the equivalent to Gnome's "Startup Applications", with the decisive difference that "avant-window-navigator" keeps the session running; if I quit it, the session quits, too. Also, in my setup, if this file isn't there, "gnome-terminal" is run instead.

Of course, I don't know any specifics of Openbox, but if just adapting my setup to your case, the session script would look like this:
```
#!/bin/bash
ck-launch-session dbus-launch --exit-with-session openbox-session & wmpid=$! 
sleep 1
if [ -f ~/.openbox-session ]; then
    source ~/.openbox-session &
else
    gnome-terminal &
fi
# Wait for WM
wait $wmpid &
gnome-panel
```As long as you don't at least create the file "~/.openbox-session", "gnome-terminal" would be run at login, in addition to "gnome-panel". To quit the session, you'd have to kill the latter. For that, I'd add a launcher to one of the panels for the command:
```
killall gnome-panel
```But as I said, I don't know if there are any specifics reg. Openbox, so this all might not work in your case. Just give it a try, however. ;-)

---

### Post by runny6play on 2011-10-10
> **Krytarik said:**
> Well, in complementation to the session script, I have the file "~/.compiz-session" in my home directory (only permissions of 644 needed, as it isn't run, but "sourced"):
```
gnome-settings-daemon &
pidgin &
smplayer &
parcellite &
alarmclock
```The apps specified there are, in addition to "avant-window-navigator" already run through the session script, the equivalent to Gnome's "Startup Applications", with the decisive difference that "avant-window-navigator" keeps the session running; if I quit it, the session quits, too. Also, in my setup, if this file isn't there, "gnome-terminal" is run instead.

Of course, I don't know any specifics of Openbox, but if just adapting my setup to your case, the session script would look like this:
```
#!/bin/bash
ck-launch-session dbus-launch --exit-with-session openbox-session & wmpid=$! 
sleep 1
if [ -f ~/.openbox-session ]; then
    source ~/.openbox-session &
else
    gnome-terminal &
fi
# Wait for WM
wait $wmpid &
gnome-panel
```As long as you don't at least create the file "~/.openbox-session", "gnome-terminal" would be run at login, in addition to "gnome-panel". To quit the session, you'd have to kill the latter. For that, I'd add a launcher to one of the panels for the command:
```
killall gnome-panel
```But as I said, I don't know if there are any specifics reg. Openbox, so this all might not work in your case. Just give it a try, however. ;-)
apparently openbox-session runs an autorun.sh  somewhere so ill look at that. Thanks for the help :o

---

### Post by runny6play on 2011-10-10
I fixed it by looking up the autostart.sh (location is noted in the man page) script and copying it and adding gnome-panel outside one of the if fi statements and them add that to the .desktop file replacing my script

---

### Post by Krytarik on 2011-10-11
> **runny6play said:**
> I fixed it by looking up the autostart.sh (location is noted in the man page) script and copying it and adding gnome-panel outside one of the if fi statements and them add that to the .desktop file replacing my script
I'm glad that you figured it out, and thanks for the feedback! :D

Please mark your thread as "solved" then, via "Thread Tools" above.

---

