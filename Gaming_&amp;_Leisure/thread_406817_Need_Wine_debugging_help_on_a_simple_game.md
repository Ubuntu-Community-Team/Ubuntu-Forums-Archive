---
title: "Need Wine debugging help on a simple game"
date: 2007-04-11
forum: Gaming &amp; Leisure
---

### Post by kingmob on 2007-04-11
I apologize for posting a purely wine based question here, but i can't find it on the internet and there seem to be no wine-forums and the manuals are either too advanced or too simple :(. 

I'm trying to load a simple game with wine. It is of a somewhat dubious nature, in case anyone notices the name of the .exe, so that is out of the way ;).
Debugging what dll's needed to be added went well and all errors related to ole32.dll etc. are gone, but the program still won't start. All i get is a window with: "System Error &Hbunchofnumbers(more numbers)".

In the console all i get is the following and i have no idea how to proceed. I think i'm basically asking what kind of debugging options to activate so i can find the problem.
```

kingmob@HAL9000:~/LE$ wine Lovers.exe 
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ntdll:NtAllocateLocallyUniqueId 0x33f844
fixme:ntdll:NtAllocateLocallyUniqueId 0x33eff0
fixme:ntdll:NtAllocateLocallyUniqueId 0x33efb0
fixme:reg:RegOpenUserClassesRoot (0x94, 0x0, 0x2000000, 0x33f7d4) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {f9043c85-f6f2-101a-a3c9-08002b2f49fb} 0x33f7a8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {f9043c85-f6f2-101a-a3c9-08002b2f49fb} 0x33f754
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {f9043c85-f6f2-101a-a3c9-08002b2f49fb} 0x33f0c8

```

All help is welcome.

---

### Post by hikaricore on 2007-04-11
Did you check: [http://appdb.winehq.org](http://appdb.winehq.org) for the name of your software?

I don't have time myself right now, just trying to point you in the right direction.

---

### Post by bugzor on 2007-04-11
have you tried no-cd / backup cd patch for it? (if it haves copyprotection)
since wine haves problems with most copyprotections.

---

### Post by kingmob on 2007-04-13
I've checked the appdb, but it's not a well known program so it is not in there. It does use copy protection, but as far as i know, it is very easy and the program is not cd-based, so there are no cd-checks, just a registration number. I can't imagine that to be a problem and would expect if it was that i would get different errors or that the program wouldn't let me play (in that case it switches to shareware).

I must say i find it odd that there is a gap in the wine manuals here, it makes a jump from complete newbie to professional, ignoring the probably large part of the people like me who are somewhere in between.

Debugging with option: +all just gives too much info, even with the relay disabled.

---

### Post by kingmob on 2007-04-19
noone?

---

