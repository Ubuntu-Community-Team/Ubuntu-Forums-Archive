---
title: "breezy and xmspy problem"
date: 2005-12-29
forum: Desktop Environments
---

### Post by lizardking on 2005-12-29
I'm trying to emulate [XmlSpy Altova]("http://www.altova.com/") windows software in ubuntu beause i'm doing  a xml work that need that.
I try the altova [howto]("http://www.altova.com/support_platform_linux.html") to run on line but it quite old (red hat 8 ) :( 
i have also a tread [here]("http://www.ubuntuforums.org/showthread.php?t=47377&highlight=xmlspy") but for hoary.

I have installed wine and put the *.dll in ~/.wine/driver_c/windows/system as altova howto say to do.
then when i tried to start with:
```
wine -dll riched32=n XMLSpy.exe
``` as the say.

i get
```
lizardking@lizard:~$ wine -dll riched32=n XMLSpy.exe
wine: cannot find '-dll'

```
. Without passing this argumets fail with a GUI dialog that report:
```
Program exit abnormal Runtime error 
fixme:variant:VarBstrFromDec semi-stub

```

Altova say to use Wine 20030115. But I have a most recent version I think (remember red hat 8 )...that take no more -dll parameters. So...some hacks or help it will be appreciated?

Thanks and sorry to use this prorietary application

ps there is a equivalent free and open soure powerful application: I have tried mlview, kxmleditor but not likde xmlspy...

---

### Post by lizardking on 2005-12-30
some help?

---

### Post by kaamos on 2005-12-30
Try running winecfg and setting the dll setting for XMLSpy.exe and then just start the program with wine without any arguments.

This is just a guess, but it looks to me like the howto is so old that wine has updated so much since that the -dll switch no longer exists.

---

### Post by lizardking on 2005-12-30
I tried but doesn't work. It says the same error. I think is not possibile to run... :(

---

### Post by joehill on 2006-01-26
I have the same problem.  XMLSpy is one of the few programs keeping me from wiping out my Windows partition (that and the Sony HiMD-Wav conversion utility--if you have any ideas on how to get working too, I'm all ears).  Someone in the Breezy 5.04 forum (see [http://ubuntuforums.org/showthread.php?t=47377](http://ubuntuforums.org/showthread.php?t=47377)) got it to work with Wine 20041019, but I installed the same version and it gives me a "Microsoft Visual C++ Runtime Error" saying "abnormal program termination." With the latest version (0.9.6) the spash screen comes up but then I get a dialogue box asking if I want to install ActiveX and then it just quits.  I don't know where to find Wine 20030115 (the one Altova has tested and says works), but it's over three years old and would probably break the other programs that work with the newer version even if I could find it.

Has anyone gotten SMLSpy to work using more recent versions of Wine?  If I could find an open-source alternative I wouldn't even bother with it, but I'm not aware of any good open-source XML editors.

---

