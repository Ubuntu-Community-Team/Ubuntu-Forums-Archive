---
title: "Keyboard Shortcut for 'shutdown'"
date: 2006-07-21
forum: Desktop Environments
---

### Post by jackn on 2006-07-21
(Added later: to just see the shortcut, see second post)

Can't set up keyboard shortcut for 'shutdown'.

Have set up several others, using either System>Preferences or aysiu's advice in [www.ubuntuforums.org/showthread.php?t=164157](www.ubuntuforums.org/showthread.php?t=164157) (*gconf-editor* and *Metacity*). No problem, works great, a treat.

The *Metacity* procedure requires use of a terminal command in order to create a keyboard shortcut. To shutdown, as can be found in the forums: ```
sudo shutdown -h now
```

Have tested the command, worked fine from the terminal. Added the command to *Metacity*, in 'keybinding commands'. Added the shortcut in 'global keybindings': <CTRL><ALT>n. Have also tried: <CTRL><ALT>0.

This doesn't work. Yet, it's the same procedure as with the other shortcuts. 
The reason doesn't seem to be the need for a password with 'sudo' - a shortcut I have for *Synaptic* (which calls for 'gksudo') does prompt me for the password, and works just fine,..

Why is there a difference? How can you work around it?

---

### Post by jackn on 2006-07-25
```
gksudo /sbin/halt
``` will do the job.

To be keyed in the  *keybinding_commands* part of *metacity*, as for any custom keyboard shortcut (pointer in previous post).
User required to put in password then.

/sbin/halt is a binary file, so can't view. But *man halt* says that in run levels 1-5, basically all usual circumstances, 'halt' will call upon 'shutdown', So this is safe, orderly shutdown.

Unrelated to this, will sometimes get a blank screen upon start. CTRL+ALT+F7 will then shift to the GUI.

Still, no idea why 'sudo shutdown -h now' won't work although it does from terminal.
Any insights?

---

### Post by cucisan on 2006-07-25
```
sudo shutdown -h now
```
will not work because it is a CLI tool and will prompt you for the password in the console from which X/gdm was started - which is not visible

gksudo is the X version of sudo which should do fine for you.
possible workaround is to SUID root the shutdown binary.. but may be a security risk

there may be nicer ways of doing this though

---

### Post by metalheart on 2006-07-25
create file /etc/shutdown.allow and add your login name in it. Then run
```
sudo shutdown -h -a now
```
You should now be able to halt the computer by pressing CTRL+ALT+DEL.

See 
```
man shutdown
``` for more information

---

### Post by jackn on 2006-07-25
Thanks a bunch, Cucisan and Metalheart.

This helps a lot.

Below, some more studies.

One.
*gksudo* or *sudo*?

OK, Cucisan, got it, indeed it's got to be *gksudo*, as shown by some experimentation. For example,

```
sudo /sbin/halt
```

doesn't work, whereas

```
gksudo /sbin/halt
```

does. And I now understand why.

But...

```
sudo shutdown -h now
``` works fine from terminal, but won't work from *metacity* shortcuts, even with *gksudo*...

Two.
*shutdown.*

*Shutdown* is an independent problem. It behaves oddly regardless of *metacity* shortcuts.

a. CTRL-ALT-DEL works *only* from the *console*, *not *from a *terminal emulator*.

CTRL-ALT-DEL has no effect, although it is commented out in /etc/inittab:
```

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now
```

Metalheart points to *man shutdown*. 
The manual says that CTRL-ALT-DEL is *only* recognized by the *console*. It is a unique key combination. 
Indeed, upon creation of the /etc/shutdown.allow file with my username, as Metalheart suggested, could make it work from the *console*, but *not* from the *terminal emulator*.
Even after removing the -a switch from the above *shutdown* command in /etc/inittab, CTRL-ALT-DEL is still recognized *exclusively* from the console.

In short, CTRL-ALT-DEL can simply not be used from any X-Windows environment, as indeed the manual says.

b. The -a switch refers only to the use of CRTL-ALT-DEL. It, too, has no effect in a terminal emulator.

The following 'shutdown' command

```
sudo shutdown -r -a now
```
 
has no effect:

```
jackn@Phoenix:~$ sudo shutdown -a -r now
Password:
jackn@Phoenix:~$
```


This, even though the /etc/shutdown.allow file is there:
```
#list of users allowed to use CTRL-ALT-DEL, a key combination that *only* works from the console.
jackn
```

The above results obtained after logging out and back in, for changes to take effect (prior to that, with the same files, the shell didn't even prompt for the password with the above command, but went right away to the next prompt).

So, while the original issue of a shortcut is resolved, one question is left, it seems...

What is it that doesn't allow the command ```
shutdown -h now
```, effective on the terminal, to work with *metacity* shortcuts, even though *gksudo* is used?

---

### Post by metalheart on 2006-07-25
Found something like this.
[http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/07/linux-desktop-how-to-shutdown-restart.html](http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/07/linux-desktop-how-to-shutdown-restart.html)

---

### Post by jackn on 2006-07-25
Neat ref, furled.
Great to learn about 'create launcher'. 
Loved to find out about /etc/sudoers...

---

