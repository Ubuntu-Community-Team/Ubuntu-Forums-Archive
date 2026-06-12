---
title: "Switching X hanging with Firefox"
date: 2023-09-05
forum: Desktop Environments
---

### Post by Skaperen on 2023-09-05
one can switch from X to a virtual console.  X restores the original video mode then _"disconnects"_ (maybe just ceases accessing) the video device controls and buffers.  this might also include telling/responding to the kernel so it (re)establishes whatever it intended to have there (often a text mode virtual console or a different instance of X).  when X switches away to let something else access the display, what terminology is used to refer to the mode that X is in?  is it _"disconnected"_?  if you have 3 instances of X running, then you must have at least 2 (maybe all 3 when switched to a text console) instances in this mode, right?

ages ago, when computers were too slow for my needs in X, i would run many text mode virtual consoles (60 of them by doing some keyboard remapping) and few instances of X (3 of them in different hardware display modes).  very often applications running on an instance of X would update the display.  when i switched back, i would see the change.  if there were many changes, i would see only the last change as if the buffers were updated in-place many times.

now days computers are fast enough i no longer use virtual console text mode and use virtual terminal software *xfce4-terminal* on X.  and i run quite many instances of X.

```

lt1a/forums/3 /home/forums 6> w|cut -c10-
 up 1 day,  3:03, 10 users,  load average: 0.19, 0.42, 0.44
TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
tty7     :0               Mon18   27:03m  1:34   0.18s xfce4-session
tty8     :1               Mon18   27:03m  4:03   0.20s xfce4-session
tty9     :2               Mon18   27:03m  2:36   0.20s xfce4-session
tty10    :3               Mon18   27:03m  1:32   0.17s xfce4-session
tty11    :4               Mon18   27:03m 15:40   0.22s xfce4-session
tty12    :5               Mon18   27:03m  1:46   0.18s xfce4-session
tty13    :6               Mon18   27:03m  1:39   0.17s xfce4-session
tty14    :7               Mon18   27:03m  1:39   0.17s xfce4-session
tty15    :8               Mon18   27:03m  1:27   0.18s xfce4-session
tty16    :9               Mon18   27:03m  5:37   9.48s xfce4-session
lt1a/forums/3 /home/forums 7> 
```
in the above command line, i used *cut* to slice off user names for privacy reasons.  i have no idea what _"Mon18"_ means.  Monday at hour 18?

i can be switched away by two different means.  one way is by workspaces.  this is manged by the window manger within one instance of X.  when i have N instances of X running, to do this on each, there will be N instances of the window manger running.  i like near full-screen terminals and run one terminal per workspace with up to 9 running terminals (out of 10 or 20 workspaces) 

the other way to switch is to _"disconnect"_ from the active instance of X and _"connect"_ to another.  the display manager *lightdm* helps me do this.  i have various keys bound to execute (directly, not by typing to a shell) the command to tell *lightdm* which instance of X i want to switch to. sometimes i have as many as 18 to 24 instances of X (each in a userid) running.

if lots of text output updates a terminal that i am not _"connected"_ to, these changes update the buffers so that when i do _"connect"_ to it, i see the last text that was updated in each place in the terminal window.  if lots output happens on *firefox* (the browser i usually run) all these updates do _not_ happen.  firefox _"hangs"_ at the first update it tries to do while its X instance is in _"disconnected"_ mode.

anyone know what is happening?  is Firefox doing something different with X.

i would like to have the buffers update continuously.  one problem i am having is that when i play a video from YouTube to hear the music (a live radio station) it _"hangs"_ as soon as as i switch to the instance of X that has what i am working on.  usually i am working on several things and switch around often (like 5 or 6 times an hour) so having the music in one dedicated instance (user "*music*" at Ctrl+Shift+M).

this happened in Xubuntu 18.04.X and is happening with 20.04.X.  i am on 20.04.6 having upgraded everything 2023-09-02.

---

### Post by TheFu on 2023-09-05
PulseAudio uses XAuth as a weenie security system for audio out.  Don't know how that relates to everything else you are doing.  I just set the DISPLAY to :0 to have my console music play correctly, even when I'm not logged into the system directly. This works fine over ssh.

In theory, pulseaudio can be run in system-mode, not user-mode, but the pulse documentation says that is a really bad idea.

When you say "X", do you mean "X11"?

---

### Post by Skaperen on 2023-09-06
i mean Xorg, the X that comes with Xubuntu and upgrades via the Ubuntu repository (so, presumably, the same Xorg that comes with plain-ole Ubuntu.).

a means to have one user work directly with the audio device (whether its X is "connected" or not) might do the trick.  switching to/from should then have no effect.  apparently much effort is being made to have each "user" or userland get its audio out when it gets switched to.  my guess is that PulseAudio is making this same effort and system-mode conflicts with it.  system-mode works as expected in 18.04 but fails in 20.04.  i have not diagnosed it because i expect no support from others due to using system-mode.  having some kind of networked audio that can be configured to connect to *localhost* (127.0.0.1) as the player host might do the trick.  such a thing would need to make the expected audio API where the programs run and carry out the networking with that audio.  then a server would use a normal audio API and service an incoming connect and play its audio.  secure authentication should be shimmed in there.

---

### Post by Skaperen on 2023-09-23
i found another GUI program (dclock) that hangs when the X it is running in is not connected to the physical console.  now i presume it is an X issue.  it may be an X API thing as some other GUI programs i tried (various xterm programs) just keep going when X is disconnect from the physical console.

---

### Post by Skaperen on 2023-09-23
IMHO, X (the graphical support software, not the crumbling social media service) should add audio to its interfaces so that with apps using it, remote consoles can hear remote audio that is being played on the remote login.  multiple channels need to be supported with a "as many as uniquely IDed" basis.  the reverse direction needs to be supported for microphone usage.

---

