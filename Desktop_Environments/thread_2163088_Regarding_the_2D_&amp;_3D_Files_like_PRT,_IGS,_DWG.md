---
title: "Regarding the 2D &amp; 3D Files like PRT, IGS, DWG, etc"
date: 2013-07-17
forum: Desktop Environments
---

### Post by slkamath on 2013-07-17
Hi Everyone,

In my office we are using ubuntu 12.04, 12.10, 13.04. in all these system I have installed 3d & 2d package of FREECAD, DRAFTSIGHT respectively.

In the 3d (Freecad) i cant open prt files, So please suggest me how i can open prt files in ubuntu?
Also in 2d (Draftsight) if i open dwg files and if i do any changes and save means i cant open in autocad.

So please suggest me.

Regards

Lokesh Kamath

---

### Post by dino99 on 2013-07-17
[https://help.ubuntu.com/community/UbuntuEngineering](https://help.ubuntu.com/community/UbuntuEngineering)
[https://launchpad.net/ubuntu/+ppas?name_filter=freecad](https://launchpad.net/ubuntu/+ppas?name_filter=freecad)
[https://forum.solidworks.com/index.jspa](https://forum.solidworks.com/index.jspa)

---

### Post by Gemnoc on 2014-01-14
It's very late to reply, but in any case,

PRT is a proprietary file format used by Pro Engineer, now named Creo. DWG is a proprietary file format from Autodesk. Proprietary file formats are usually undisclosed. The commercial CAD applications can usually open file formats from competitors by reverse engineering the file format in-house, or licensing a third-party file import library. The open source projects do not have the resources to do the former and evidently by their nature cannot do the latter.

So it is best to request 3D CAD files in open formats such as STEP (ISO 10303, *.step, *.stp) or IGES which is an older file specification (*.igs, *.iges). FreeCAD can open both these formats. For 2D data, open source software such as LibreCAD and FreeCAD can open DXF R2000 and no later.

[QUOTE=slkamath]Also in 2d (Draftsight) if i open dwg files and if i do any changes and save means i cant open in autocad.[/QUOTE]
What version of AutoCAD are you using? You must make sure you save in the same DWG version as your AutoCAD version or older. For example if you have AutoCAD 2004, you must save in DWG 2004 or older. The DWG format changes every 3-4 years.

---

