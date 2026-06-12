---
title: "Firefox acroread plugin shows a white page"
date: 2006-06-08
forum: Desktop Environments
---

### Post by pesachzon on 2006-06-08
Hi,
I have recently installed Dapper and for some reason the firefox acroread plugin isn't working. When I try to open a pdf it opens a new tab with a blank page.

I tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=191438&highlight=acroread+plugin+work")
and it didn't work.

Has anyone had this problem?

Thanks

---

### Post by Rondonjin on 2006-06-08
[QUOTE=pesachzon]Hi,
I have recently installed Dapper and for some reason the firefox acroread plugin isn't working. When I try to open a pdf it opens a new tab with a blank page.

I tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=191438&highlight=acroread+plugin+work")
and it didn't work.

Has anyone had this problem?

Thanks[/QUOTE]

is Acrobat reader working at all for you? (it isn't for me) Open a terminal and type:

acroread

Wayne

---

### Post by pesachzon on 2006-06-09
yes it is. acroread starts fine but the plugin doesn't work

---

### Post by dpm on 2006-06-09
Funnily enough, I've got the same problem in Epiphany, but not in Firefox.

I posted a bug about it some time ago, but it didn't seem to get much attention:

[https://launchpad.net/distros/ubuntu/+source/epiphany-browser/+bug/43655]("https://launchpad.net/distros/ubuntu/+source/epiphany-browser/+bug/43655")

It only seems to affect upgraded machines (i.e. Breezy->Dapper), but not fresh installations of Dapper.

Since I couldn't solve this, I ended up uninstalling acroread and installing mozplugger instead. Mozplugger is quite flaky, but at least I can view most pdfs now. What it basically does is to start up Evince when you click on a pdf link and then Firefox "swallows" the Evince instance and makes it appear inside a tab.

Cheers.

---

