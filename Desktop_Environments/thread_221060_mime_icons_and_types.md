---
title: "mime icons and types"
date: 2006-07-22
forum: Desktop Environments
---

### Post by brucehohl on 2006-07-22
I'm using Ubuntu (Gnome) and added the KDE application Rekall.  There was no mime icon or type association so I did the following based on information in this forum.  (see below)

This provided the mime icon and type association I wanted except in the following case:  If I open Nautilus the rkl file will show the associated icon and type.  If I single click that rkl file so that it receives the focus the new mime icon and type are lost.  If I single click another file then refresh Nautilus the desired mime icon and type for the rkl file are restored.

So can anyone help me refine my set-up so that the desired mime icon and type remain even if a subject file has the focus in Nautilus?


--------------------------------------------------------------------------
1- Added the mime entry below in following file:
   ~/.local/share/mime/packages/Override.xml

    <mime-type type="application/x-rekall-rkl">
      <comment>Rekall database</comment>
      <glob pattern="*.rkl"/>
    </mime-type>

--------------------------------------------------------------------------
2- Copied needed icon to theme directory:   
   # cp /usr/share/pixmaps/other/rekall.xpm       ~/.local/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-rekall-rkl.xpm

--------------------------------------------------------------------------
3- updated mime db:
   # update-mime-database ~/.local/share/mime

   This action wrote following file to:
   ~/.local/share/mime/application/x-rekall-rkl.xml

--------------------------------------------------------------------------
4- update icon cache:
   # gtk-update-icon-cache ~/.local/share/icons --ignore-theme-index
   Returned message: "Cache file created successfully."

--------------------------------------------------------------------------

---

