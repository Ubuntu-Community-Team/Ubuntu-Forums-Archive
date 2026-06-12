---
title: "[Xubuntu 14.04] I decided to remove &quot;light-locker&quot; also"
date: 2014-05-02
forum: Desktop Environments
---

### Post by macachuto on 2014-05-02
So, as long as I liked Xfce 4.10 and want to use it as main OS it now needs to be polished.

But after analyzing the /var/log/lightdm/lightdm.log I found out that to lock my screen light-locker is doing:
```

[+3028.96s] DEBUG: Seat: Locking
[+3028.96s] DEBUG: Seat: Creating greeter session
[+3028.97s] DEBUG: Seat: Creating display server of type x
[+3028.97s] DEBUG: Using VT 7
[+3028.97s] DEBUG: Seat: Starting local X display on VT 7
[+3028.97s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+3028.97s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+3028.97s] DEBUG: DisplayServer x-0: Launching X Server
[+3028.97s] DEBUG: Launching process 3990: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+3028.97s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+3029.32s] DEBUG: Got signal 10 from process 3990
[+3029.32s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+3029.32s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+3029.33s] DEBUG: Seat: Display server ready, starting session authentication
[+3029.33s] DEBUG: Session pid=3993: Started with service 'lightdm-greeter', username 'lightdm'
[+3029.34s] DEBUG: Session pid=3993: Authentication complete with return value 0: Success
[+3029.34s] DEBUG: Seat: Session authenticated, running command
[+3029.34s] DEBUG: Session pid=3993: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+3029.34s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+3029.34s] DEBUG: Session pid=3993: Logging to /var/log/lightdm/x-0-greeter.log
[+3029.35s] DEBUG: Activating VT 7
[+3029.35s] DEBUG: Locking login1 session /org/freedesktop/login1/session/c9
[+3029.35s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c10
[+3029.44s] DEBUG: Session pid=3993: Greeter connected version=1.10.0
[+3029.69s] DEBUG: Session pid=3993: Greeter start authentication for vas
[+3029.69s] DEBUG: Session pid=4032: Started with service 'lightdm', username 'vas'
[+3029.69s] DEBUG: Session pid=4032: Got 1 message(s) from PAM
[+3029.69s] DEBUG: Session pid=3993: Prompt greeter with 1 message(s)
[+3036.49s] DEBUG: Session pid=3993: Continue authentication
[+3036.51s] DEBUG: Session pid=4032: Authentication complete with return value 0: Success
[+3036.51s] DEBUG: Session pid=3993: Authenticate result for user vas: Success
[+3036.51s] DEBUG: Session pid=3993: User vas authorized
[+3036.55s] DEBUG: Session pid=3993: Greeter requests session xubuntu
[+3036.55s] DEBUG: Seat: Returning to existing user session vas
[+3036.55s] DEBUG: Session pid=4032: Sending SIGTERM
[+3036.55s] DEBUG: Unlocking login1 session /org/freedesktop/login1/session/c9
[+3036.55s] DEBUG: Activating VT 8
[+3036.61s] DEBUG: Seat: Stopping greeter
[+3036.61s] DEBUG: Session pid=3993: Sending SIGTERM
[+3036.61s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c9
[+3036.61s] DEBUG: Session pid=4032: Terminated with signal 15
[+3036.61s] DEBUG: Seat: Session stopped
[+3036.67s] DEBUG: Session pid=3993: Greeter closed communication channel
[+3036.67s] DEBUG: Session pid=3993: Exited with return value 0
[+3036.67s] DEBUG: Seat: Session stopped
[+3036.67s] DEBUG: Seat: Stopping display server, no sessions require it
[+3036.67s] DEBUG: Sending signal 15 to process 3990
[+3036.67s] DEBUG: Process 3990 exited with return value 0
[+3036.67s] DEBUG: DisplayServer x-0: X server stopped
[+3036.67s] DEBUG: Releasing VT 7
[+3036.67s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+3036.67s] DEBUG: Seat: Display server stopped

```

I desided to remove that beast. This is not LIGHT locker !!!!

Now I changed it with i3lock.
Command "i3lock -d -n -c 000000" gives me everything I wanted.

Also I was disappointed of lack of the "xlockmore" - it is also very good and light locker.

---

