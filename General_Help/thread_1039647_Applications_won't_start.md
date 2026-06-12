---
title: "Applications won't start"
date: 2009-01-14
forum: General Help
---

### Post by doug-M on 2009-01-14
I'm using Ubuntu 8.04 2.6.24-22-generic and every once in a while the system gets into a state where most GUI programs won't start, or rather they won't display anything.

For example firefox, ps shows it running but no window appears.
If I start it on command line I get no errors (no output at all).

Terminal brings up a window just fine.

Administration -> System Log
  brings up a blank window with the title Log Viewer
  attempting to close it says "Log Viewer" is not responding wait or force quit.

Nautilus can start new windows just fine.

Nothing shows up in /var/log/messages

Others:
  Work:
    Accessories -> Calculator
    Graphics -> Gimp
  Fail:
    Games -> AisleRiot Solitaire (blank window)
    Graphics -> F-Spot Photo Manager (blank window)

top shows vmware using a healthy amount of the CPU (20% or so) but nothing higher.

Seems like some resource associated with graphical displays is locked but I don't know what that would be.

One of the latest programs I had been using before the problem was GIMP.

Anyone have any idea of what is happening?

---

### Post by doug-M on 2009-01-15
Looks like pulseaudio is to blame.

I used strace to see what firefox was doing and it would hang on this:
strace firefox
...
connect(16, {sa_family=AF_FILE, path="/tmp/.esd-1000/socket"}, 23

That lead me to pulseaudio.
ps -ef | grep pulseaudio

find the number xxxx for /usr/bin/pulseaudio
kill -9 xxxx

So not sure exactly why pulseaudio is hanging but that seems to be the culprit.

---

