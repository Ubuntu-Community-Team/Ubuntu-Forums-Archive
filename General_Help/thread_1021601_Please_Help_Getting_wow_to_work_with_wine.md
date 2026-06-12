---
title: "Please Help Getting wow to work with wine"
date: 2008-12-25
forum: General Help
---

### Post by Vash9190 on 2008-12-25
I just downloaded the game and installed it, updated it and all. I click the launcher and the intro movie comes up but after its over or if I push enter to skip it, it crashes and shows this

==============================================================================
World of WarCraft (build 9183)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Dec 25, 2008  4:34:19.456 PM
User:     vash
Computer: Hookerbot9000
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:005CEF48

The instruction at "0x005CEF48" referenced memory at "0xFFA28348".
The memory could not be "read".

---

### Post by roggaro on 2008-12-25
I just installed Ubuntu myself and had the same problem that you got myself, the only problem is that wow uses directX as default, so you need to change it to OpenGL.
go into your world of warcraft folder, then into your wtf folder and open Config.wtf and add this line:
```
SET gxApi "opengl"
```

it made my world of warcraft work :)

i found some help in [HTML]https://help.ubuntu.com/community/WorldofWarcraft[/HTML]

but as i said, the only code i needed to add was the one i pasted above :)

---

### Post by finku on 2008-12-25
Hi roggaro, was <SET gxApi "opengl"> the only mod you had to do? I've done all that, I'm able to play the game fine, but I have a problem with the chat text (bottom left) and all text within Menus. In menus, all text is invisible (while I can still see the buttons), and the chat text acts funny (gets scrambled in lots of lines) - its more like a laser show then plain text!

I'm using two ATI HD4850 crossfired cards with latest drivers (8.12). I've completely disabled desktop effects. Any help?

---

### Post by themusicalduck on 2008-12-25
Try disabling Compiz if you haven't, it might cause problems for it.

EDIT: Nevermind, missed the last sentence in your post. >.<

---

### Post by finku on 2008-12-26
thanks anyway, I found a fix for this. One needs to disable GL_ARB_vertex_buffer_object from registery ;)

Now it works flawlessly, except I need to kill pulseaudio each time I want to play, else the sounds would be messed up.

---

### Post by roggaro on 2008-12-26
good thing you had it svolved :D
i didn't had any problems with the text, using the addon fontain to set all the text to one specific font :)

---

