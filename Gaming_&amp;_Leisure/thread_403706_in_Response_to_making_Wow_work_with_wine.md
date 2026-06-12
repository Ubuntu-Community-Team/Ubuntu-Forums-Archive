---
title: "in Response to making Wow work with wine"
date: 2007-04-07
forum: Gaming &amp; Leisure
---

### Post by Aviatore on 2007-04-07
ya so i did the howto on these forums but im realtivly a noobie to linux so how do i

(quote)

Almost mandatory performance enhancing tweak

This is a simple registry edit for Wine that will dramatically increase the framerate in game for both ATi and nVidia users.

1. Open a regedit window with this command regedit
2. Find this key HKEY_CURRENT_USER\Software\Wine\
3. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
4. Click right on the wine folder and select [NEW] then [KEY]
5. Replace the text New Key #1 with OpenGL
6. Click right in the right hand pane and select [NEW] then [String Value]
7. Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
8. Then double click anywhere on the line, a dialog box will open.
9. In the value field type GL_ARB_vertex_buffer_object

Here's what regedit should look like once you have finished adding this new key and it's value: [http://appdb.winehq.org/appimage.php?iId=4640](http://appdb.winehq.org/appimage.php?iId=4640)

(unquote)
???:confused:

---

### Post by hikaricore on 2007-04-07
> 1. Open a regedit window with this command **regedit**

read step one

---

