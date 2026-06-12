---
title: "Running PDF Annotator 2 in Wine"
date: 2009-05-27
forum: Education &amp; Science
---

### Post by ishtob on 2009-05-27
I'm a college student using a tablet to take notes in class. I saw my classmate use a program called "PDF Annotator 2" to take notes, and saw that it is a pretty awesome note-taking software. I tried to install it in Linux but it just freezes up.

this is the meessege i get from terminal:
```
$ env WINEPREFIX="/home/andy/.wine" wine "C:\Program Files\PDF Annotator\PDFAnnotator.exe"
fixme:reg:GetNativeSystemInfo (0x32fb94) using GetSystemInfo()
fixme:atl:AtlModuleInit SEMI-STUB (0x49b97000 0x49b97ae8 0x49a90000)
err:ole:CoWaitForMultipleHandles Unexpected wait termination: 192, 0
fixme:msvideo:DrawDibRealize (0x1, 0x64f0, 0), stub
fixme:gdiplus:GdipCreateHBITMAPFromBitmap stub
fixme:gdiplus:GdipCreateHBITMAPFromBitmap stub
err:seh:setup_exception_record stack overflow 1556 bytes in thread 0019 eip 7bc3c3de esp 03240d1c stack 0x3240000-0x3241000-0x3340000
```

I'm not sure what I am missing since im still new to linux and learning, can anyone help?

I am currently running:
Kubuntu 9.04
Wine version 1.1.22
on a HP TC1100

--------

crosspost: [Here]("http://ubuntuforums.org/showthread.php?t=1181496")

---

### Post by PGScooter on 2009-05-28
Hi ishtob,

I think you might get more help on this topic in the Wine subforum: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

If you do decide to crosspost, please say so on both of your posts.

good luck!

---

### Post by autumnraine on 2009-06-28
I also use use this program and love it but have been unable to get it to install through Wine. Ubuntu would be PERFECT for me if I could get this working.

---

### Post by ishtob on 2009-06-28
i have gotten it to start without crashing, but cannot see any opened files and unable to write/edit a new file,i installed gdiplus_dnld.exe (i dont remember exactly where I got it)

---

### Post by autumnraine on 2009-07-01
How'd you get that far? When I try it breaks at the point where it says it has to install Windows components, then says something like "Error. Cannot open AVI."

---

### Post by autumnraine on 2009-07-01
I've cross-posted this problem in the Wine forum as the person suggested above. Here's the link ([http://ubuntuforums.org/showthread.php?p=7547539#post7547539](http://ubuntuforums.org/showthread.php?p=7547539#post7547539)) and here's what I posted there: 

                                                  Hi, there's a couple of us who have been trying to get PDF Annotator 2 to work, in this thread: [http://ubuntuforums.org/showthread.p...79#post7547479]("http://ubuntuforums.org/showthread.php?p=7547479#post7547479"). So far it isn't working. The program's own installer seems to run alright, but then it says that you need to install missing windows components, and something called InstallAWARE begins to run. It runs for 20 seconds or so and then says "Runtime error in install: Cannot open AVI", and then the install just stops. That's when Wine is emulating XP. I tried running it Vista mode and then the program won't run and brings up this message. "Missing Required Windows Service. Please ensure that the required 'TabletInputService' is running." Can somebody help us with this. This program is really important to a lot of students because there's no adequate native pdf annotator in linux, and the lack of this program is the only thing preventing me from being able to run Ubuntu full-time on my IBM X41 tablet.

---

### Post by ishtob on 2009-07-05
hmmm... interesting find autumnraine, i should look into what thie "tabletinputservice" is, and see if i can port it or copy it from my desktop. I was able to get my pdf annotator to start without crash by installing gdiplus from some random file I found googling ( sry didnt save the link)... but editing and openning pdf's are still crashy and unusable

and I agree, there is a great need for a native pdf annotator that doesn't suck... xournal is what I am using in the meantime, but it is not editable after saving the file back to pdf.

---

