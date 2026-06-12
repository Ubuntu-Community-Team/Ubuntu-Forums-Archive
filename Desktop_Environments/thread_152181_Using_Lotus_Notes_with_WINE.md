---
title: "Using Lotus Notes with WINE"
date: 2006-03-29
forum: Desktop Environments
---

### Post by lnunes on 2006-03-29
Hi all!

I'm new on Ubuntu, but with great feelings!:D 

I'm facing just one problem.... Here I use Lotus Notes mail. But I cannot start Notes with wine... On another dists it works fine, just here this happens.

Theese are the errors:](*,) 

fixme:uniscribe:ScriptRecordDigitSubstitution 1024,0x61beeb38
wine: Call from 0x7fc92410 to unimplemented function usp10.dll.ScriptCacheGetHeight, aborting

err:wineconsole:WCUSER_SetFont wrong font
fixme:netapi32:NetUserEnum ((null),20, 0x2,0x7faff1a0,2,0x7faff3a8,0x7faff3ac,0x7faff198 ) stub!

fixme:advapi:LookupAccountSidA ((null),sid=0x7fafeed8,0x7fafe890,0x7fafec94(512),0x7fafea90,0x7fafee9c(512),0x7fafeea0): semi-stub

err:virtual:NtQueryVirtualMemory Unsupported on other process

fixme:ntdll:NtQueryObject Unsupported information class 1

I also tryed to ignore usp10.dll (WINEDLLOVERRIDES), but without success.

Anyone has faced this????:-k

---

