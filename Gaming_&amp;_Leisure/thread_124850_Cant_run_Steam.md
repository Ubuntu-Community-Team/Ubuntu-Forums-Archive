---
title: "Cant run Steam"
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by Kimm on 2006-02-02
I just bought CounterStrike 1 Anthology. The installation works fine, but I cant create a Steam account, I have tried with both wine and cedega,  but they give me different problems.

Wine loads Steam... but there is no text on any buttons, and when I get to the licence agreement, wine hangs... and I have to kill it.

Cedega loads Steam nicely... at first, then, when I get to the licence agreement, I cant read it since Mozilla ActiveX is not installed (doesnt work to install it), if I cant read it, I can accept it (since I have to scroll to the bottom to do that..........)

this is my wine output:

[/quote]
[email]kim@ubuntu:~/.wine[/email]/drive_c/Program Files/Valve/Steam$ wine steam.exe
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
fixme:imm:ImmGetContext (0x10044): stub
fixme:hook:IsWinEventHookInstalled (32773)-stub!
[/quote]

Can someone help me fix wine, or get Mozilla ActiveX in Cedega? :cry:

[i]Edit:
I'm using wine 0.9.5, latest from the wine repositry...[/i]

---

### Post by Kimm on 2006-02-02
This is steam in wine:

[img]http://img141.imageshack.us/img141/3057/steamwine3pu.jpg[/img]
(the program freezes at this point, and uses 100% CPU)

And this is cedega:

[img]http://img141.imageshack.us/img141/9106/steamcedega9li.jpg[/img]

---

### Post by soulglo83 on 2006-02-03
had same problem, only i never bothered with cedega.  wine runs steam flawlessly, maybe even as responsively as windows, just not with the < 2.6.10 kernels, in fact, i jumped straight from .10 to 2.6.15 and have noticed no problems @ all w/ my ubuntu install. well, no bootsplash, but im sure that could even be easily remedied. to upgrade ur kernel u can simply follow the two guides i link to here in this post:

[http://www.ubuntuforums.org/showthread.php?t=124692](http://www.ubuntuforums.org/showthread.php?t=124692)

it does require compiling a kernel, but the instructions are very straightforward and can even be copied and pasted (albeit u will want to swap 2.6.15 in place of 2.6.14 in their commands).  hope this helps if u need help feel free to message me.

---

### Post by pedwards on 2006-02-03
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)


these guys might be able to help you out
ive tried this and it install steam and cs
getting it to run correctly is a different animal
~good luck

---

### Post by Kimm on 2006-02-04
I tried recompiling my kernel by following that tutorial... not that I dont like my new kernel, but it didnt help :(

---

### Post by Kimm on 2006-02-04
nevermind, a friend provided me with the cedegamozzctl. now it works

---

### Post by claydoh on 2006-02-04
If you have cedega, you can ***easily*** install the MS fonts and the Mozilla control from the "Check for Updates" under the "Transgaming" menu. You can also use the mozilla control in regular wine
[ Here is the most current and accurate how-to for Steam and recent wine versions]("http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=1234")

---

