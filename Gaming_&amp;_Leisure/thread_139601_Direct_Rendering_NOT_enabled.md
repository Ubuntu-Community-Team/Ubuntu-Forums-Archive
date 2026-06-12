---
title: "Direct Rendering NOT enabled??"
date: 2006-03-04
forum: Gaming &amp; Leisure
---

### Post by linuxishard on 2006-03-04
hi.. when playing a a game called BOSON i was given a msg that sed

"Direct rendering is NOT enabled - boson will run very slow. You should ensure that direct rendering is enabled!"

i havent got a clue haw to do that:cry: ... im pretty sure someone does  ????

---

### Post by e2k on 2006-03-04
What graphics card have you gotten, nvidia or ati? Have you got the latest (or any) drivers installed? Seems that you don't have hardware acceleration enabled, you can try to verify this with
```
$ glxinfo | grep direct
```

---

### Post by linuxishard on 2006-03-05
sorry i ges i shud have sed that i have an ATI card im prettyt sure i have the rite drivers.. cos it was set up by an experianced linux user (unlike myself).

but i tried the command> glxinfo | grep direct

and i got this msg>   direct rendering: No
                                  OpenGL renderer string: Mesa GLX Indirect

i aint got any idea what to do to change it..... or update my drivers. ill take a look at the help pages..but i find them pretty hard to traul through and find what im after..

thanx though..

p.s.
oh yeh i ges i should mention that im using dapper.. cos my shoddy old pc realy doesnt like breezy,,,not sure why....
but  it seems to like dapper... and i aint had much problems since upgrading...
i have noticed that graphics have been pretty slow.... i ges thats cos i dont have direct rendering enabled

any more help on this would be  greatly apreciated..its the only thing stoppin this pc form working perfectly.. thanx

---

### Post by tregetour on 2006-05-19
glxinfo | grep direct
returns: direct rendering: Yes

However, Boson still claim that it's not enabled.

Any clue what's going on?

---

