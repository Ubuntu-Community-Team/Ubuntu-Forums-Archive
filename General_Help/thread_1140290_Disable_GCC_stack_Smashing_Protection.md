---
title: "Disable GCC stack Smashing Protection"
date: 2009-04-27
forum: General Help
---

### Post by Maky001 on 2009-04-27
Hi to all of you.

Have a bit of problem and maybe someone give me help.
I use Ubuntu 7.04 and have a prob with one program
that from time to time just stop and dissapear from
proceses and make crashlog where i can see that SSP
stopped him.
I am not author of that program and cant change anything in it
and just wanted to know is there a way maybe to disable
stack Smashing Protection or is problem in program itself how it is written.

I have found some infos about " just add -fno-stack-protector to the gcc options to disable "
but i didnt quite understand where excatly should that and how.

So please i am just begginer so if any of you can help me
i would be thankful for any help.

---

### Post by Maky001 on 2009-04-27
Anyone please???

---

### Post by TheLions on 2009-04-27
did you compile that program by yourself?

Also give us link to the source so we can try it.

---

### Post by Maky001 on 2009-04-27
As i said i didnt compile him
i am just user of program so dont have any access
to source or whatever.
And just wanted to know is there any way disabling
SSP without doing anything on program itself.

Thanks!!!

---

### Post by sdennie on 2009-04-27
It's a bug in the program or the program is trying to do something nefarious.  You probably could disable the stack smashing but, it would be a lengthy process and I'm not sure if it would work.  Essentially, you'd have to know all the symbols in libssp and then LD_PRELOAD a stub library to intercept all the library calls in libssp.  And example on how to do things like that can be found here: [http://ubuntuforums.org/showthread.php?t=1103926](http://ubuntuforums.org/showthread.php?t=1103926).  I have no idea if it would actually work and would probably be a lengthy process.

---

