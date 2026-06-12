---
title: "Ubuntu Dofus"
date: 2010-04-07
forum: Gaming &amp; Leisure
---

### Post by MikeVaughanG on 2010-04-07
I used to run Ubuntu 9.10 Karmic 32bit. 

Yesterday, I made the switch to 64bit. 

Everything works perfectly, except the only game I like to play. :) 
Dofus. 

I got it to install.. 
but whe i click the launcher i am getting this error:
```

Failed to execute child process "/home/mike/ankama/Dofus/share/UpLauncher" (Permission denied)

```

The reason i think this is 64bit specific, is because i didnt have this issue before i switched. 

Any help is much appreciated. 
Thanks in advance.

---

### Post by dearingj on 2010-04-07
Sounds like you need to give yourself execute permission for that file. Try this in a terminal:
```
chmod u+x /home/mike/ankama/Dofus/share/UpLauncher
```

---

### Post by MikeVaughanG on 2010-04-07
That worked. Thank you. 

:D 
:D

---

### Post by mkloch on 2010-04-19
This solution has worked for me too! Thanks. What is this command doing anyway?

---

### Post by myromance123 on 2010-04-19
Basically it's giving the owner the permission to execute that program.

---

### Post by Polydeuces on 2010-04-20
Sorry to resurrect this thread...

What if changing permissions is NOT allowed? That's been happening to me :(
```
chmod: changing permissions of `UpLauncher': Operation not permitted
```

any help is appreciated!

---

### Post by DrMelon on 2010-04-20
Do "sudo chmod u+x /path/to/game"

---

### Post by Polydeuces on 2010-04-20
Okay, that worked. Thanks DrMelon!

Though now, I'm experiencing a new issue altogether. 

Since it's a MMORPG-styled game, it has an updater client. When I run this, it comes up normally, though during the update it will pause and will tell me it "is impossible to connect to the internet" and when I close/reopen it resumes downloading. However, usually once it gets to 61%, I get another error message. 

"One of the downloaded files is corrupted. The update has been interrupted"

and another one that says "bad zipfile to offset entry"

I think this stems from the problem of the inconsistent/choppy download... Anyone have any ideas? This is really the only game (other than free ones in the software package) that I'm interested in playing. 

I'm running Ubuntu 9.10 Netbook Remix on an Acer Aspire One AOA150, the old 9" monitor one. Everything else seems to run fine with no problems.

---

