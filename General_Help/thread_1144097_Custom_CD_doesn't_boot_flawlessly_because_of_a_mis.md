---
title: "Custom CD doesn't boot flawlessly because of a missing package"
date: 2009-04-30
forum: General Help
---

### Post by uflieven on 2009-04-30
Hi,

I created a custom CD with remastersys. I've done it before with hardy and intrepid and all went without problems. Now I'm trying this with jaunty.

This are my findings:
Starting off the full 700 MB Ubuntu-CD, no problems.
Starting off the command-line-install-option on the alternate-cd or on the ubuntu minimal cd-image, I got stuck while booting my newly created live-cd. It gets stuck at configuring network interfaces (about halfway through the usplash-progress-bar). However there's no problem with my network, because if i press Ctrl-Alt-Del when it's stuck, booting continues I and can use firefox on the live-cd as normal. The only problem is, why do I have to press Ctrl-Alt-Del?

When I look to the output of the dmesg command, it says something like:
link is not ready, link becomes ready and then again link is not ready.
I can post the full output if necessary.

So there must be a package missing, thus any help in determining which package would be greatly appreciated.

---

### Post by uflieven on 2009-04-30
I've attached the output of dpkg -l, so you can see which packages are currently installed.

---

