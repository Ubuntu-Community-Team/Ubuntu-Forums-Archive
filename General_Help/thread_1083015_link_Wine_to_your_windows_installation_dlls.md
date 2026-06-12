---
title: "link Wine to your windows installation dlls?"
date: 2009-02-28
forum: General Help
---

### Post by WaliWorld on 2009-02-28
I have ubuntu and XP dual booted (on separate hardrives) is it possible to link wine to your windows installion dlls? or maybe im looking at the wrong way? basically, what im wondering is what can i do to make wine run apps in peak performance? how can i add dlls to wine? what can i do to make it the best it can be? 

oh and one more question, i have a Wine folder link in my applications tab thing, how can i put links to applciations in the "programs" menu?

thanks in advance :)

---

### Post by lha on 2009-02-28
You can copy Windows' dlls to ~/.wine/drive_c/windows/system32 (or wherever your fake c:\windows\system32 directory is). Use winecfg to force Wine to use native dlls.

The [Wine documentation]("http://www.winehq.org/docs/wineusr-guide/index") used to have a short list of the most common dlls that might work better if they were native, and also of those that won't work. However, the list seems to be gone - it might have become obsolete. I use native dlls only when my programs require them. In case you still want to try fiddling with dlls, see [Codeweavers site]("http://www.codeweavers.com/support/docs/wine-user/config-dll"), they have some comments on native dlls.

If you want to see which dlls are loaded by a given program, start wine with
```

WINEDEBUG=+loaddll wine myprogram.exe

```

---

### Post by theDaveTheRave on 2009-03-02
Hi

I'm having trouble with wine and running a setup.exe from the cdrom.

I want to install FileMakerPro via wine - a works requirement unfortunately. The wine site says that it [should work]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10680") (OK ish, it currently has "Bronze" compatibility).

But when I try to install I keep getting the same error message of <setup cannot find the necessary files>

I tried lha's trick and did

```

davem@Anticlimax:~/.wine/dosdevices/d:$ WINEDEBUG=+loaddell wine setup.exe

```
as you can see I'm in the "fake" cd drive (<d:>) that is created by wine, but I get no information at all?

it this going to be a problem that I can't resolve? as I would prefere to not have to dual boot my works pc. As I can then have the database that I'm developing in MySQL live on my Ubuntu terminal rather than on the windows terminal - then I can have it accessable all the time.

Thanks in advance for any help / advice you are able to offer.

David

---

### Post by lha on 2009-03-02
> **theDaveTheRave said:**
> 
I tried lha's trick and did

```

davem@Anticlimax:~/.wine/dosdevices/d:$ WINEDEBUG=+loadd[COLOR="Red"]e[/COLOR]ll wine setup.exe

```


You have an extra 'e' there, it should be +loaddll.

---

### Post by theDaveTheRave on 2009-03-03
> **lha said:**
> You have an extra 'e' there, it should be +loaddll.

OOps](*,)

David

Hello again...

so I tried it with this and there is no difference, it is happily finding all the required dll's!

At work there happens to be an iso of the file on the server, so I unpacked this to my HDD and I was able to start the install procedure.

But again however it gets stuck, this time with an error that seems to be somehow related to visual c++. A little investigating on this and I am unable to the current version of Visual C++ (th visc2008) to load correctly.

Again using the various winedebug options I get no sensible reasoning for the failure, and I've been unable to find a solution.

does anyone have any ideas of the specific switch I should pass to winedebug, I tried it wil < +all > but it really wasn't helpfull!

thanks in advance.

David.

---

