---
title: "Diablo II LoD and wine."
date: 2006-01-28
forum: Gaming &amp; Leisure
---

### Post by lungdart on 2006-01-28
I'm trying to install Diablo II LoD. The install goes fine. After Diablo is installed I was getting disk not in drive errors, but read thats because of some protection diablo II uses. So I Push on through with LoD and the 1.11 patch for it. I then get a no cd crack for Diablo II 1.11, since that would fix the protection and not get the no cd error.

Unfortunatly when i run it, I get a wine error message with the error title "?????" and the error "??????????????????????????"

running it in a terminal gives this error for game.exe, diablo II.exe, and d2loader.exe (no cd crack)

```

fixme:ntdll:TIME_GetTZAsStr Can't match system time zone name "AST", bias=240 and dst=0 to an entry in TZ_INFO. Please add appropriate entry to TZ_INFO and submit as patch to wine-patches
fixme:ntdll:TIME_GetTZAsStr Can't match system time zone name "AST", bias=240 and dst=0 to an entry in TZ_INFO. Please add appropriate entry to TZ_INFO and submit as patch to wine-patches

```

I also read on these forums that copying over an install directory from windows would work fine, but that also gives the same errors. I have starcraft running fine on wine so it doesnt seem to be a wine global setting.

Any help?

Edit:
-----

Tried installing just Diablo II, and it worked flawlessy with the crack. Version 1.11e i do beleive. Had to emulate the sound, which made the sound skippy, but using nice -n 20 wine DLoad.exe worked great.

After resintalling LoD, and before i upgrade to LoD 1.11E, I get this error:

[code]
err:seh:setup_exception nested exception on signal stack in thread 0017 eip 7bed9267 esp b7f84cd0 stack0x7fa20000-0x7fb20000
[code]

when running diablo ii.exe

After patching i get the same error before with and withought the crack. Has anyone got LoD working with wine?

---

### Post by lungdart on 2006-01-29
bump

---

