---
title: "Setting function key macros for xterms?"
date: 2012-12-22
forum: Desktop Environments
---

### Post by dkoleary on 2012-12-22
Hi;

On all previous versions of linux, I've always used a ~/.Xdefaults file to set macros for function keys:

$ cat ~/.Xdefaults
*ttyModes: erase 
*VT100.Translations: #override \
<Key>F4:string("ssh -l root localhost\n")\n\
<Key>F7:string("/bin/ksh -o vi\n")\n\
<Key>F8:string(". ./mcd\n")\n\
<Key>F9:string("exit\n")\n\

The last time, when I switched to ubuntu, I read a bunch of posts about how deprecated the .Xdefaults file is; but, after some poking around, I managed to make it work.

Now that I've upgraded to Ubuntu 12.10, I can't get it to read the file at all anymore.  Yet, I'm unwilling to do without my keyboard short cuts.  They come in really handy for me.

I tried setting them up via the system settings tab w/no joy.  I also found and installed xbindkeys thinking that would solve my problem.  While it does solve the problem of me having to hunt down the xterm app every time I want to run it, xbindkeys wants to run new x-based commands, not issue commands in an already existent xterm.

Does anyone know how I can go about setting function key shortcuts - or any other way of being able to issue commands like the ones listed above in an xterm?

Thanks for any help you can provide.

Doug O'Leary

---

### Post by dkoleary on 2012-12-22
Hey;

Interesting data point:  I can get *a* function key working via:

xterm -class XTerm -xrm \
"XTerm*vt100.translations:      #override \n\
<Key>F4:string(\"exit\n\")\n"

That kicks off an xterm and executes the 'exit' command if I press F4.  If I change it to F9, the function doesn't work anymore.  I suspect this is all tied in together; but, for the life of me, I can't figure out how...

Thanks.

Doug O'Leary

---

### Post by dkoleary on 2012-12-22
Hey;

I got it solved.  I forgot that I had to run "xrdb -merge ~/.Xdefaults".  The issue with the F9 key was me playing around with xbindkeys.  One issue remains; but, that'll be the subject of another post.

Thanks.

Doug O'Leary

---

### Post by itcotbtoemik on 2012-12-22
I avoid using xrdb (it's too blunt an instrument to be useful). Instead, I set XAPPLRESDIR to my own app-defaults directory, and customize things there. :)

---

