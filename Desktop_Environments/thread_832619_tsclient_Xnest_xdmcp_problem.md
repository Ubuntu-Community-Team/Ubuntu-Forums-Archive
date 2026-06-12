---
title: "tsclient Xnest xdmcp problem"
date: 2008-06-17
forum: Desktop Environments
---

### Post by research labs on 2008-06-17
Hi there,

i have Ubuntu 8.04 on a x86 platform and a server with Ubuntu amd64. both of them are updated.

i try to connect my x86 ubuntu to the amd64 server with a remote desktop, i've using XDMCP protocol, with XNest (also tsclient for gui)

i made the connection, but it is very slower and it change frequently of themes... :confused:

for example, i took two snapshots, on the same session (you can view the hour of both, only a minute of difference)

[IMG]http://img150.imageshack.us/img150/185/xnest1lf8.png[/IMG]

[IMG]http://img155.imageshack.us/img155/5491/xnest2br5.png[/IMG]

this is what i mean to changing themes... the connection works, bu very uncomfortable

also, when i try to run Xnest on a shell, i obtain these messages:

```
~$ Xnest -query 192.168.1.100 :2 -geometry 800x600
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
AUDIT: Tue Jun 17 21:53:08 2008: 8515 Xnest: client 1 rejected from IP 192.168.1.100
XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 163254 requests (163254 known processed) with 0 events remaining.
```

so... any ideas for solving that issue? i've try to browse the post of this fuorum but i don't get the solution.

Thanks in advance.

---

### Post by Kingmilo on 2008-09-18
Hi - 


I seem to be having a similiar problem to yours where i can make a connecti via XDMCP to my server and get full desktop etc, but the connection is a bit delayed and if i try and do to much like open a document i get kicked off. I cant say that i have had the theme problem other than seeing the smoothing of the window border and icons change which is really just something that happens quickly on the local desktop so you dont see it but because there is a delay now remotely you can see it 'morphing', not sure if im making sense.

However your screenshots seem to have different icons, they are a bit small so i cannot see very well so this might be a guess.

Did you have any luck in resolving your speed issue?
I have read that disabling the ESD sound daemon might help but so far im also in the dark.

Good luck!

---

### Post by gexcko on 2008-11-09
I also have the same issue. I'm running xnest on ubuntu 8.10 2.6.27-7-generic using xdmcp to log into an ubuntu 8.04 2.6.24-19-server machine. I've got gnome running on the server and it's working fine logging in via xdmcp straight from gdm however if I log in via xnest->xdmcp the theme flicks back and forth between the 'human' and 'crux' (I think) themes. Any ideas?

---

