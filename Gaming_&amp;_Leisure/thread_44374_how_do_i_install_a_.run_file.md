---
title: "how do i install a .run file"
date: 2005-06-25
forum: Gaming &amp; Leisure
---

### Post by Dark Damo on 2005-06-25
any ideas?

---

### Post by desdinova on 2005-06-25
I take it you're probably talking about the NVidia drivers? For any .run file

sh nameoffile.run

---

### Post by Dark Damo on 2005-06-25
[QUOTE=desdinova]I take it you're probably talking about the NVidia drivers? For any .run file

sh nameoffile.run[/QUOTE]
 nah the command and conquer generals installer is a .run dw i found it out now

---

### Post by broekskw on 2006-12-02
hey dark damo i am having problems installing the first c&c on ubunto keep getting setup error see attached screen shot, any suggestions as how to correct this,i am installing from disk:cool:

---

### Post by po0f on 2006-12-02
broekskw,

You did notice the dates on the previous posts in this thread, right?  They're from over a year ago.  ;)

Where is your CD mounted?  /media/cdrom?  Try this from a terminal:
```
[FONT="Courier New"]$ wine /media/cdrom/Setup.exe[/FONT]
```

---

### Post by mabhatter on 2006-12-03
make sure it's executable under permissions.  That's the BIG one, otherwise it will try to do goofy things like open in a text editor, etc.. it won't tell you it's not executable or what to do.  Typically any .run file you download will not be executable by default.. it's extra security so something or somebody else has to manually release any file before the system will run it!!  it's a good thing, but often pros omit those "small" details.

---

### Post by broekskw on 2006-12-03
thanks for both your replys,sorry did not see the date. here is what i get when i input your command in terminal mode, i also get the same screen error as before.
ok how do i check to see if it is executable under permissions.

thanks8) ](*,) :mrgreen:

---

