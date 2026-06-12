---
title: "there is no ~/.xsession file - what selects the DE to run?"
date: 2021-06-09
forum: Desktop Environments
---

### Post by Skaperen on 2021-06-09
there is no **~/.xsession** file - _what selects the DE to run_?  i have a script that back traces process parentage/ancestry but it goes from terminal to init (PID 1).  so everything was backgrounded and i can't see what started what without stracing everything **opendm** does.

---

### Post by &amp;KyT$0P# on 2021-06-09
The display manager.  You choose it in the display manager greeter before you log in.  For Xubuntu at least some of the options are stored in [FONT=Courier New]/usr/share/xsessions/[/FONT] I don't know if that's the only place though.

---

### Post by Skaperen on 2021-06-10
what chooses to start Xfce in Xubuntu ... or ... what designates that the user is an Xubuntu/Xfxe (or whatever DM) user?   is it something in lightdm?

what i want to do is run some additional code (in a Python script or an ELF binary ... that i could build statically linked if necessary, so PATH is not needed, yet) for every user at login time.  running this AS that user with no privilege to become root is OK.  but needs to, at least, know which user (it will switch real and effective user to be that user, if it is root).  this code is intended to do some cleanup before anything (else) starts.

---

### Post by GhX6GZMB on 2021-06-10
I run Lubuntu myself with SDDM as display manager, but I imagine the setups are pretty much alike.

The items for the environment choices during login are in /usr/share/xsessions

As far as I can tell, the default or last chosen environment is defined in etc/sddm.conf, in your case probably /etc/lightdm.conf or /etc/lightdm/lightdm.conf

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by &amp;KyT$0P# on 2021-06-10
> **Skaperen said:**
> what chooses to start Xfce in Xubuntu ... or ... what designates that the user is an Xubuntu/Xfxe (or whatever DM) user?   is it something in lightdm?

Yes.  I wonder if that is stored in [FONT=Courier New]/var/cache/lightdm[/FONT] ?

> what i want to do is run some additional code (in a Python script or an ELF binary ... that i could build statically linked if necessary, so PATH is not needed, yet) for every user at login time.

Can you try editing the file in [FONT=Courier New]/usr/share/xsessions[/FONT] (or copying one and creating a new one) to somehow run your Python script before running the existing user session command?

---

### Post by deadflowr on 2021-06-10
User info like Xsession the user has set is stored in /var/lib/AccountsService/users/Username.

---

### Post by GhX6GZMB on 2021-06-10
That one's empty on my machine.

---

### Post by Skaperen on 2021-06-12
if something(s) hold what DE the user has chosen then i need the map of DE to /what/to/run.  either i fudge the map or stub the files to run.  i need my script to run ASAP after user credentials are authenticated for a login.  i will need to know or find out which DE the user is expecting (iff they chose a different one at login then i need to know or find out what that is).

---

### Post by &amp;KyT$0P# on 2021-06-12
If I were doing this I would edit (or better, if possible, copy somewhere it would override the original and edit the copy) the [FONT=Courier New]/usr/share/xsessions/*.desktop[/FONT] files to point to a wrapper script that calls your script with the DE name as an argument, and after your script is done [FONT=Courier New]exec[/FONT] the command that was originally in said .desktop file.  I'd have your script keep its own track of what DEs the user logs into.

Unless you also need this for non-GUI/tty sessions?

---

### Post by dddman on 2021-06-12
> An xprofile file, ~/.xprofile and /etc/xprofile, allows you to execute commands at the beginning of the X user session - before the window manager is started.
[https://wiki.archlinux.org/title/Xprofile](https://wiki.archlinux.org/title/Xprofile)

sounds like what your looking for

---

### Post by Skaperen on 2021-06-13
> **halogen2 said:**
> If I were doing this I would edit (or better, if possible, copy somewhere it would override the original and edit the copy) the [FONT=Courier New]/usr/share/xsessions/*.desktop[/FONT] files to point to a wrapper script that calls your script with the DE name as an argument, and after your script is done [FONT=Courier New]exec[/FONT] the command that was originally in said .desktop file.  I'd have your script keep its own track of what DEs the user logs into.

how does one execute a *.desktop* file from a script?  is executing what the [FONT=courier new]Exec=[/FONT] line has good enough?

> **halogen2 said:**
> Unless you also need this for non-GUI/tty sessions?

no.

---

### Post by Skaperen on 2021-06-13
> **dddman said:**
> [https://wiki.archlinux.org/title/Xprofile](https://wiki.archlinux.org/title/Xprofile)

sounds like what your looking for

i cannot determine from that page if my script would be run in place of some other script.  if so, that would probably make it necessary to add stuff to my script, such as actually running the DE.  if so, how to run it?  in the background?  use [FONT=courier new]exec[/FONT] (or its *python* equivalent) to replace my process?  retain certain environment variables?

---

### Post by &amp;KyT$0P# on 2021-06-14
> **Skaperen said:**
> how does one execute a *.desktop* file from a script?  is executing what the [FONT=courier new]Exec=[/FONT] line has good enough?

What I had in mind was the reverse: have the .desktop file execute a wrapper script that calls your script.  Then yes, have the wrapper script execute what the [FONT=Courier New]Exec=[/FONT] line has.

> **Skaperen said:**
>  probably make it necessary to add stuff to my script, such as actually running the DE.  if so, how to run it?  ...  use [FONT=courier new]exec[/FONT] (or its *python* equivalent) to replace my process?

This, I think.

If you try my implementation idea, it wouldn't necessarily be your main script though, you could write the wrapper script in bash and just use [FONT=Courier New]exec[/FONT] from there after your main script exits.

---

