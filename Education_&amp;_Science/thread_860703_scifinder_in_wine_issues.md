---
title: "scifinder in wine issues"
date: 2008-07-15
forum: Education &amp; Science
---

### Post by ZeldaFan on 2008-07-15
I installed scifinder in wine rather easily, and all seems to work well. The only problem is that the "viewer" never really opens probably because it can't open an Internet Explorer browser. How do I get it to open the "viewer" under wine. I tried installing firefox under wine and it installed fine. I attempted to set it as the default browser, but it never remained as the default browser and the notification always popped up when I started the program, so Scifinder wasn't able to open up the viewer in firefox under wine. Any ideas as to getting my viewer working?

---

### Post by gunksta on 2008-07-16
Disclaimer: I have never used scifinder and my suggestion may be way off base, but I do know how to install Internet Explorer into Wine:

Use ies4linux!


Before downloading anything from this site, make sure you have the program cabextract installed on your computer. Use Synaptic to make sure you have this installed. If oy uhave installed the MS Windows Core Fonts you already have it installed.

Once cabextract is installed, go to:

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

and download the script. It will automagically install internet explorer for you. Note: I don't think it can do IE 7. I think it tops out at 6.5, but that's probably enough for what you need.

---

### Post by ZeldaFan on 2008-07-16
Thanks for the reply. I installed internet explorer 6 with the script and it installed perfectly. The programs loads fine and works well, but scifinder may not be able to find the program because the problem still exists. The viewer still doesn't open the link in internet explorer.

---

### Post by gunksta on 2008-07-16
Dang. That's really weird. What version of scifinder are you using? I ask because I bounced over to the WineHQ and looked up (I think) your app.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2852](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2852)

And it looks like it is a well supported application. (these things can be incorrect of course)

IRC might be a way to get some help:

#WineHQ on            irc.freenode.net 

I wish I could be of more help, but I'm afraid that I have only dipped my little toes into the anarchy of Wine.

---

### Post by mj_ja55 on 2008-07-23
I started using SciFinder in wine earlier this year, and it worked great.  It used my normal Ubuntu Firefox browser as the viewer.  Recently, it stopped working and it will no longer use Firefox as the viewer.  I think this is related to the bug posted here: [http://www.winehq.org/pipermail/wine-bugs/2008-June/119497.html](http://www.winehq.org/pipermail/wine-bugs/2008-June/119497.html)

This would make sense on my maching as I get this same error message when I try to activate ChemDraw, which I installed in wine.  Apparently, this bug was introduced into wine recently, so I think that is why SciFinder suddenly stopped working properly.

I may be way off on all of this, but it is the only thing I have been able to find that seems to make sense.

---

### Post by ZeldaFan on 2008-07-24
I think I found a solution and it works relatively well. If you install Firefox 2 in WINE and set it to the default browser, the SciFinder viewer will work. Make sure you do not install firefox 3 however, that doesn't work. Also don't worry about setting it as your default browser, it will not change Ubuntu firefox from being your default. Generally opening the viewer will automatically open firefox 2 in WINE, but if not, you can open it yourself and then the viewer will open the link in a new tab.
Download Firefox 2 from here:
[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)
Make sure its the windows version, and install it using WINE. Version 1.0 or later works seamlessly.

---

### Post by frbe0101 on 2009-04-22
Anyway to get the scifinder viewer to open the existing firefox in ubuntu, I like to use it in conjunction with zotaro.

---

### Post by gunksta on 2009-04-22
Since this thread started, I have gotten [more interested]("http://ubuntuforums.org/showthread.php?t=1113065") in running certain Windows applications on Linux. Based on what I see here, I suspect that Wine may have a hard time running  scifinder (fully) for the same sort of reasons that MS Access is difficult to get up and running, DLL hell.

We need to identify exactly how scifinder works. Note, we don't need to see the source code. We really just need to understand what parts of the Windows API are used by the application. For example, does it require .Net? Does it require MDAC? Does it reqiured VBA or VBScript? All of these systems exist as part of a standard Windows install or are easily available installations, but have not been implemented (or only partly implemented) by Wine. Thus, applications that require these components may "fail" when running on Wine. In the case of Acces, which requires a native MDAC and the Jet database components, it installs but isn't fully functional because the Windows installers lacks a function common to most advanced linux package management tools, dependency resolution. There is no way for Wine to tell the installer that a necessary component is missing from the system, and thus you get applications that install cleanly but fail to run.

It sounds like scifinder needs Internet Explorer to be fully functional. Yeah, you can try to use FireFox, but it may be easier to use IE 6 or 7.  If all you need is Internet Explorer, you might want to try the [IEs for Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") project. If you need something more complex, [winetricks]("http://wiki.winehq.org/winetricks") is probably what you are looking for.

Someone with an interest in this software, and a paid license should [contact CAS]("http://www.cas.org/forms/inforeq.html") (the makers of scifinder) directly and try to find out what parts of the Windows API are used by this application. This knowledge will make applying tools like winetricks more efficient and effective. Or, you could pay for the [web version]("http://www.cas.org/support/academic/sf/moveweb.html").  :-)

---

### Post by huggies15 on 2010-04-27
Hi,
Sorry to reopen an old thread, but ive been struggling with this issue for ages now and only just decided to try and fix it. I used to copy and paste references into google and find them that way, but i have fixed it now.
I tried installing firefox and ie into wine, but that didnt work. Then i stumbled upon this post which shows how to get it to open wine links in your ubuntu browser. Works a charm!
[http://www.webupd8.org/2010/03/how-to-make-wine-open-links-in-your.html](http://www.webupd8.org/2010/03/how-to-make-wine-open-links-in-your.html)
Hope it helps someone somewhere.

Steve

---

### Post by JabberWalkie on 2010-04-27
I just tried this, and it works! Thanks!

---

