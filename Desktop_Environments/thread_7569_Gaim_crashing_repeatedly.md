---
title: "Gaim crashing repeatedly"
date: 2004-12-08
forum: Desktop Environments
---

### Post by paul.hendrick on 2004-12-08
Hi All,
I'm getting weird crashes from gaim, occasionally when i click a conversation window. I ran it from a terminal until it crashed, and the output was:

```

The program 'gaim' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1056196 error_code 3 request_code 10 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

any references refering to similar output all relate to problems when running it remotely, but i'm not doing that.

any reason why this is happening?

---

### Post by GNU/Hippie on 2004-12-14
Does it happen when accessing msn? The same thing is happening to me. The only solution (and a poor one at that) was to stop using msn. There's a open bug on it over at gaim: [http://sourceforge.net/tracker/index.php?func=detail&aid=1082187&group_id=235&atid=100235](http://sourceforge.net/tracker/index.php?func=detail&aid=1082187&group_id=235&atid=100235)

Once I logged off my msn account everything was fine. I'm curious if this helps.

dgh

---

### Post by jdong on 2004-12-15
What GAIM version is this? The default Warty one? Hoary? Backported?

---

### Post by GNU/Hippie on 2004-12-16
[QUOTE=jdong]What GAIM version is this? The default Warty one? Hoary? Backported?[/QUOTE]

Why, does it matter? =)

Good point. I should've mentioned it in my posting. I'm using "1.0.0-1ubuntu1.1". I assume that's Warty. BTW, I can consistantly repeat the gaim crash by placing the mouse cursor over a MSN "buddie".

If I stay off of MSN (which I don't mind) Gaim is fine.

---

### Post by mukherjee.siddhartha on 2006-10-31
Its happenning on gaim->ICQ too.
I am using Edgy :(
I have to use [http://www20.meebo.com/](http://www20.meebo.com/) now.

---

### Post by mukherjee.siddhartha on 2006-11-01
OK,
Now i did this (Dont know what was the problem, but what ever the  problem was, ... NOW fixed!)

1) uninstall gaim-data
    sudo apt-get remove gaim-data
2) installed the gaim beta
    sudo dpkg -i gaim_2.0.0beta4_i386.deb 

And now it is not crashing, altleast untill now.:-k

---

