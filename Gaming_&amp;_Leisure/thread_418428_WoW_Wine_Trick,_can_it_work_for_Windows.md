---
title: "WoW Wine Trick, can it work for Windows?"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by Drezliok on 2007-04-22
> 
Tweak #1

This is a simple registry edit for Wine that reportedly may dramatically increase the framerate in game for both ATi and nVidia users.

   1.

      Open a regedit window with this command regedit
   2.

      Find this key HKEY_CURRENT_USER\Software\Wine\
   3.

      Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   4.

      Click right on the wine folder and select [NEW] then [KEY]
   5.

      Replace the text New Key #1 with OpenGL
   6.

      Click right in the right hand pane and select [NEW] then [String Value]
   7.

      Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   8.

      Then double click anywhere on the line, a dialog box will open.
   9.

      In the value field type GL_ARB_vertex_buffer_object

Note: If you are unable to rename the newly created key "New Key #1" to "OpenGL" then expand the left hand pane of the regedit window using the vertical divider bar. You should now be able to change it. A known bug in Wine is causing this unwanted behavior.



I have a old laptop and I was wondering if this wine tweak could be used to help the FPS in Windows aswell?

Thankyou for your time
Drezliok

---

### Post by eyelessfade on 2007-04-22
It might. Just one way to find out :) Just remember the old values if it doesn't

edit:
When I think about it. I think it works better in linux since opengl is a open implementation and directx isn't. So wine can pass thing more easily through to the graphic card when using opengl.

---

### Post by Drezliok on 2007-04-22
never mind, I remembered that it won't on my own, lol

Thankyou anyways.

---

### Post by lakersforce on 2007-04-22
The question would be: where to put the string?

---

### Post by hikaricore on 2007-04-22
You wouldn't be using opengl in windows more than likely.

---

### Post by AndrewRiedi on 2007-04-22
Wine used to have a ~/.wine/config file ages ago.  (Since Transgaming took the Wine code ages ago, they still have this file.)  Anyhow, Wine now uses the registry internally for configuration options.  That is simply one Wine configuration option, and thus it will not work in Windows.

---

