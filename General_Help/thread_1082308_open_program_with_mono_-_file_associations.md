---
title: "open program with mono - file associations"
date: 2009-02-27
forum: General Help
---

### Post by dreaminhere on 2009-02-27
I've upgraded to intrepid and now an exe file that I want to open with mono tries to open in the archive manager instead when I double click on it.  I can type in the terminal "mono program.exe" and it opens fine.  How do I get it to open in mono using the mouse instead of the terminal?  If I right click and choose, open with other program, mono isn't in there.

---

### Post by kestrel1 on 2009-02-27
Right click on the icon & choose Properties, go to the Open With tab & if mono is not there click on Add. If mono doesn't come up in the list, then click on Custom command near the bottom & type the command for mono.

---

### Post by directhex on 2009-02-27
Generally speaking.....

Just make a little launcher (e.g. a .desktop icon, or a .sh)

---

### Post by dreaminhere on 2009-02-27
Thanks.

I tried that but nothing happened.  Then I found out the program was throwing an unhandled exception... :(

Now if I can figure out how to mark things as solved.

---

