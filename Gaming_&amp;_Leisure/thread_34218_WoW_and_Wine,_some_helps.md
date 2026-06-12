---
title: "WoW and Wine, some helps"
date: 2005-05-13
forum: Gaming &amp; Leisure
---

### Post by reBoB on 2005-05-13
Hello,

I try to run WoW on wine. I'm not an advanced user but .... I'm not succed to patch the game ....

With the package Wine on Synaptic (I know it's out of date but I should be enough to install ) 
After a winesetup, after the installation without matter, I want to patch the game but :
1. he (bnupdate) ask me for mfc42.dll : Have you been that ? for me two solutions
          a) Recompiling wine in order to generate mfc42.dll ...have you done it ?
          b) Take a windows dll and put it on : I have done that choice
2. He ask me to install an activeX on my mozilla (so firefox) !!!! Have you been that ? How I do and witch one ? the message error is on CreateProcessDialog !!
    And the log is :

You need to install the Mozilla ActiveX control to
use Wine's builtin CLSID_WebBrowser from SHDOCVW.DLL
fixme:shdocvw:WBPCI2_GetGUID stub: dwGuidKind = 1, pGUID = {00000000-0000-0000-0000-000000000000}
fixme:shdocvw:WBPCI2_GetGUID Wrongly returning IPropertyNotifySink interface {9bfbbc02-eff1-101a-84ed-00aa00341d07}
fixme:shdocvw:WBQA_QuickActivate stub: QACONTAINER = 0x7e13e318, QACONTROL = 0x7e13e358
fixme:shdocvw:WBPSI_Load stub: LPSTORAGE = 0x7e13e3ec
fixme:shdocvw:WBCP_Advise stub: IUnknown = 0x77c76360, connection cookie = 0
fixme:shdocvw:WBOOBJ_SetExtent stub: (0x7baf1560, 1, (15690 x 6535))
fixme:shdocvw:WBOOBJ_DoVerb : stub iVerb = -5
fixme:shdocvw:WBOOBJ_DoVerb stub for OLEIVERB_INPLACEACTIVATE
fixme:shdocvw:WBOOBJ_DoVerb : stub iVerb = -3
fixme:shdocvw:WBOOBJ_DoVerb stub for OLEIVERB_HIDE
fixme:shdocvw:WBOIPO_SetObjectRects stub PosRect = 0x77c762b8, ClipRect = 0x77c762b8
fixme:shdocvw:WBOC_GetControlInfo stub: LPCONTROLINFO = 0x77c76300
fixme:shdocvw:WBOIPO_GetWindow stub HWND* = 0x7e13e424
fixme:shdocvw:WBOC_FreezeEvents stub: bFreeze = 1
fixme:shdocvw:WBCP_Unadvise stub: cookie to disconnect = 77c762d8
fixme:shdocvw:WBCP_Unadvise stub: cookie to disconnect = 77c76288
fixme:shdocvw:WBCP_Unadvise stub: cookie to disconnect = 1
fixme:shdocvw:WBOIPO_InPlaceDeactivate stub
fixme:shdocvw:WBOOBJ_SetClientSite stub: (0x7baf1560, (nil))
fixme:shdocvw:WBOOBJ_Close stub: ()
fixme:thread:GetThreadTimes Cannot get kerneltime or usertime of other threads

maybe the error come from the GetThreadTimes.

After, I test with the source 0419 (the last one and the package wine removed) but after the  configure, make depends, make,make install .... 
On the patch I have the same error.
On the Installer.exe , it tell me i ve not enough space on my HD and I sure it is :/.

please ..if you have an idea ... 
For making from source, my problem is to find the good devel package to install,I think ..If someone can do that list, i think it should be interresting for newbie want compile.

and last question: do you use winesetup or winetools or your hand to configure wine ?
ps: i tried also first with cvscedega without succes...

---

### Post by SWAT on 2005-05-14
Okay, why would you try to run WoW through WINE? For "Windows" games you could better use Cedega (Transgaming.org). I know for a fact that WoW works with Cedega (I use WoW with the Point2Play GUI). I use the newest version of Cedega and WoW and I'm online very much  :smile: 
So I would recommend to get a subscription on Cedega (with Point2play), it's 5 bucks a month. I personally like the project and the effort, so I'm willing to pay (and I'm a student!)
P.S. WINE is meant for applications.

---

### Post by GoneWacko on 2005-05-14
[QUOTE=SWAT]Okay, why would you try to run WoW through WINE? For "Windows" games you could better use Cedega (Transgaming.org). I know for a fact that WoW works with Cedega (I use WoW with the Point2Play GUI). I use the newest version of Cedega and WoW and I'm online very much  :smile: 
So I would recommend to get a subscription on Cedega (with Point2play), it's 5 bucks a month. I personally like the project and the effort, so I'm willing to pay (and I'm a student!)
P.S. WINE is meant for applications.[/QUOTE]


For some people, paying a monthly fee to use a piece of software, sounds rediculous.
Buying software for Linux is so-so. Acceptable.
But a **montly fee** takes the cake, IMHO.

I am currently contemplating to subscribe to Cedega. But the support I get had better be good (I have friends that use Cedega, and with a *lot* of work they have managed to get stuff to work with it. A *LOT* of work..)

I too, would like to run WoW on linux. but I am already paying more than enough money to play the game in the first place.  :) 
It would be interesting to see if Cedega will run those games that somehow mysteriously fail to run on Windows (NFSU 2, for instance). Then it would suddenly be worth a few bucks. (then again, a good reinstall of Windows would probably fix that)

I'm sure there are a lot of discussions about Cedega out there already and it is not my intention to start one here, but you sounded like you were just advertising the project shamelessly. [-X

---

### Post by reBoB on 2005-05-15
Why !! because even if the project is good, I have not the profile  ;).
I am not a hard gamer and I played 1 Game (actually WoW) fews hours per week....I'am not testing every new game etc ....So a montly fee to add to the WoW montly fee :(. 
I would like  Blizzard make an Linux version of WoW   :? and it will be perfect... 
I used Linux few years ago (4 years) and I enjoy my come back on Linux(unbuntu)......execpt with WoW ...4 week without WoW ..aaarrg  ](*,) .

And anyone has an idea why I don't succeed with bnupdate.exe ?

---

### Post by valadil on 2005-05-15
You could always subscribe to cedega for a month or two, then cancel it.  You won't lose your copy of cedega, you just won't get access to a new one when it comes out.  If you don't care about trying all the new games to come out then you probably won't need an updated cedega that supports them all.  

$5 once for wow is worth it.

---

### Post by Muchacho_Gasolino on 2005-05-15
you should use the latest CVS wine from [www.winehq.org](www.winehq.org)
i remember a while ago the devs were specifically working on getting WoW working, and succeeded, and actually fixed a bug that the Cedega guys had been working on for months
the package might be old enough so that that work is not included
however, the patcher error you are getting might present a problem. Blizzard changed the way their patcher works which introduced a problem in Cedega I know, which was fixed, but the problem may not have been fixed in Wine

---

### Post by SKLP on 2005-05-16
I play WoW using wine quite nicely, there're just some minor isses.
Check out this thread at the gentoo forums and you should be able to get it running...

[http://forums.gentoo.org/viewtopic-t-246098.html](http://forums.gentoo.org/viewtopic-t-246098.html)

oh and btw i will never pay for cedega since i consider it really bad to support such a "bad for free software" piece of software. WINE will probably never get good gaming support if people keep buying the proprietary cedega.

---

### Post by brdweb on 2005-05-16
How exactly is Transgaming bad again? We all know that no matter how much people wine about gaming on linux, there just aren't enough desktop users to support the R&D for most companies. And for those that complain about the monthly fee for cedega, then pay for it with your time spent and use the CVS version which is freely available. I'm sure it won't cost you any more effort than getting wine to run games. 

Cedega isn't perfect and yes there's a fee involved, but in order to play several hundred dollars worth of my games without having to boot into windows it's very much worth the $5 a month to me. I just wish we would stop having flame wars about it.

---

### Post by reBoB on 2005-05-19
the topics on the gentoo forums seems good... I'm going to read and try  ;-) 
thanks for help. 

just a question : if I buy cedega just for one month and after I want to use again cedega program:
- I'm ok with their licence (without using new version) ?

---

### Post by Raku on 2005-05-20
the monthly fee is for support and updates.  you  will still be able to use cedega after  the subscription runs out.

---

### Post by dust on 2005-05-24
Getting wow running with wine is easy. That gentoo topic is pretty indept for what most users will need. Winex is bad because they don't give back after they take.

---

### Post by Kurse on 2005-05-25
[QUOTE=brdweb]How exactly is Transgaming bad again?[/QUOTE]

Well for one, they do not give anything back to the project it forked from, or any other project. They take, but dont give! 

WoW works great in Wine, no need to pay a montly fee

---

### Post by Masato on 2005-05-25
[QUOTE=valadil]You could always subscribe to cedega for a month or two, then cancel it.  You won't lose your copy of cedega, you just won't get access to a new one when it comes out.  If you don't care about trying all the new games to come out then you probably won't need an updated cedega that supports them all.  

$5 once for wow is worth it.[/QUOTE]
 Whoa $5 a month for WoW is...unprecedented. I haven't played it myself due to a lack of current income, but I've seen a few friends and I loved it from what I saw. Wasn't expecting to see it in Linux yet, but that's amazing. 

BTW this is my first post, so yeah. Not that I'm a total newbie at Ubuntu; I've been using it for months now. I must say it gets much less frustrating than Red Hat 9.  :P

---

