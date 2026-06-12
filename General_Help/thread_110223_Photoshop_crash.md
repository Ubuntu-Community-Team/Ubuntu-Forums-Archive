---
title: "Photoshop crash"
date: 2005-12-30
forum: General Help
---

### Post by drfalkor on 2005-12-30
I installed photoshop 7.0 with wine 0.9.4 - While I think "oh well, let's give wine another try at photoshop."
The installation is finishes, and I try to run Photoshop !

```
falkor@ubuntu:~/.wine/drive_c/Program Files/Adobe/Photoshop 7.0$ wine Photoshop.exe
```

Photoshop loading up, loading the brushes etc.. but when the loading is finish, it crashes, and gives me this message

```
fixme:actctx:QueryActCtxW stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:actctx:QueryActCtxW stub!
fixme:actctx:QueryActCtxW stub!
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:actctx:QueryActCtxW stub!
fixme:actctx:QueryActCtxW stub!
err:dc:CreateDCW no driver found for L"\\\\.\\DISPLAY1"
fixme:palette:GetICMProfileA (0xb104, 0x7fc0e86c, 0x7fc0e870): partial stub
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
wine: Unhandled page fault on read access to 0x0000000c at address 0x7c98bc16 (thread 000c), starting debugger...

```

and I think "#"¤"#¤"#¤"#%!#% !%!" :mad: :mad: "

I think I need a little help on this one, tehe :D

---

### Post by _axiom_ on 2005-12-30
I got Photoshop 7 to work under wine (don't ask me how, it just started working!), but it doesn't work quite right.  It will launch, and you can start editing images, but after a short while the menus cease to function (you click, and they show, but they immediately disappear).  Some of the dialogs don't work properly, and when creating new text, it goes way off the page somewhere where you can't see it, and for some reason you can't drag it back.

I've had good luck with win4lin in the past, though I may use qemu with the kqemu kernel module to speed things up.

So morale is, don't believe what they say, photoshop does not work (properly at least) under wine.

---

### Post by drfalkor on 2005-12-30
hmm - Maybe Im gonna try it later ;)

---

