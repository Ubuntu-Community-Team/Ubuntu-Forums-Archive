---
title: "Problems with Sony Ericsson k750i"
date: 2006-03-09
forum: Desktop Environments
---

### Post by PSIman on 2006-03-09
Hi!
I have a SE k7750i and want to backup my sms from the mobile to my harddisk.
Has anyone of you an idea how i can do this?
I allready searched the web for a linux tool, but most that i found dont support this mobile.
There is a nice windows tool called MyPhoneExplorer ( [http://members.aon.at/fwechsel/](http://members.aon.at/fwechsel/) ) which i allready tried to usw with wine, but it doesnt work. You need Visual Basic 6 Runtimes. I downloaded the msvbvm60.dll, how a guy told me, and copied it to /.wine/drive_c/windows/system32 , but when i run wine i get the followin error message :

```
Run-time error "339"
Component "vbalSGrid6.ocx" or one of its dependencies not correctly registered: a file is missing or invalid
```

In the shell i get :
```
jan@localhorst:~/.wine/drive_c/Programme/MyPhoneExplorer$ wine MyPhoneExplorer.exe
fixme:ole:CoRegisterMessageFilter stub
fixme:ole:OleLoadPictureEx (0x7dbb7744,300062,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x7facf90c), partially implemented.
fixme:ole:OLEFontImpl_Invoke varg of first disparg is not VT_I2, but 8
fixme:ole:OleLoadPictureEx (0x7dbb8ad4,3646,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x7facf66c), partially implemented.
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x7fdd7924), stub!
err:toolbar:ToolbarWindowProc unknown msg 2210 wp=00000001 lp=0001003a
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject no class object {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} could be created for for context 0x3
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject no class object {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} could be created for for context 0x3
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x7fdd8224), stub!
err:toolbar:ToolbarWindowProc unknown msg 2210 wp=00000001 lp=0002003a
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject no class object {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} could be created for for context 0x3
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject no class object {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} could be created for for context 0x3
err:toolbar:ToolbarWindowProc unknown msg 2210 wp=00000001 lp=0003003a
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject no class object {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} could be created for for context 0x3
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject class {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} not registered
err:ole:CoGetClassObject no class object {c5da1f2b-b2bf-4dfc-bc9a-439133543a67} could be created for for context 0x3
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:CoRegisterMessageFilter stub
jan@localhorst:~/.wine/drive_c/Programme/MyPhoneExplorer$ 
```

Can anyone help me ?
Thank you! If you know a nativ linux tool for this, it also would be wonderfull :)
edit: i hope this is the right forum :)

---

### Post by PSIman on 2006-03-10
Has no one an idea :/

---

### Post by toon on 2006-06-08
I have a w800i, and I would very much like to know this as well. I'd also LOVE to be able to send and recieve messages through, say, kmobiletools.

---

