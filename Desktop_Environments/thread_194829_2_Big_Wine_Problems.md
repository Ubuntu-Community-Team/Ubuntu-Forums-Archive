---
title: "2 Big Wine Problems"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Alienist on 2006-06-12
So I'm trying to get Wine configured and I'm running into two show-stopping problems. 
     1) When I try to map my cdrom drive, either automatically or manually the    information is never saved. I'll go back into winecfg and the information is gone.

     2) When I select the Audio tab it immediately crashes and the error message  in the terminal is:  [COLOR="Red"]Assertion failed at address 0xffffe410 (thread 0009), starting debugger...err:seh:raise_exception Unhandled exception code c000013a flags 0 addr 0xffffe410[/COLOR].

Thanks for any help anyone can give.

---

### Post by mdurham on 2006-06-12
If it's any help, mine also crashes when selecting audio with:
> Creating link /home/mike/.kde/socket-station1.
can't create mcop directory
whatever that means!

---

### Post by digimars on 2006-06-12
I've got the same issue on my laptop, yet my regular PC with Ubuntu and Wine works fine.  But when I select the audio tab in Winecfg on my laptop it crashes with teh "can't create mcop directory" in the terminal window.

---

### Post by Alienist on 2006-06-12
[QUOTE=Alienist]So I'm trying to get Wine configured and I'm running into two show-stopping problems. 
     1) When I try to map my cdrom drive, either automatically or manually the    information is never saved. I'll go back into winecfg and the information is gone.

     2) When I select the Audio tab it immediately crashes and the error message  in the terminal is:  [COLOR="Red"]Assertion failed at address 0xffffe410 (thread 0009), starting debugger...err:seh:raise_exception Unhandled exception code c000013a flags 0 addr 0xffffe410[/COLOR].

Thanks for any help anyone can give.[/QUOTE]

Just in case anyone may be having the same problems as me, I did figure out how to map my cdrom drive. Apparently, Wine requires that the cdrom drive be mapped to D. Wine had autodetected one of my mounted drives as D already so I had to remove that drive from Wine and manually mount my cdrom drive after that. Hope that helps anyone with the same problem. I still can't get the Audio tab to work though...

---

### Post by keithjr on 2006-06-18
One possible solution has been posted here:
[http://www.ubuntuforums.org/showthread.php?p=1154801#post1154801](http://www.ubuntuforums.org/showthread.php?p=1154801#post1154801)

---

