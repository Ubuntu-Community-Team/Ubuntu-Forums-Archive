---
title: "PC very slow unexpectedly - Shall I format?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by gfd on 2006-09-17
hello,

I don't know what happened but my pc is running extremely slow after a reboot.

It was fine yesterday, but now the login page takes ages to load along with everything else after that. 

I just get that round animated thing that tells me that something is happening...
After a certain time the operation does in fact complete (ie open a folder in Nautilus) but I might have to wait up to like 4-6 minutes... 

The last thing I did was to install Eclipse + PHPeclipse but the system was fine after that. I rebooted and worked for a while without a problem.

I did manage to run fsck from the command line but it didn't make a difference.

Has this happened to anyone else?
What might have caused this?
Do I have to format and re-install?
Can I re-install on top of the existing system so that I don't have to re-install and re-configure all my programs again?

thanks

---

### Post by MacMan on 2006-09-17
> **gfd said:**
> 
Do I have to format and re-install?

I can't help you with your problem but I'd say no, you don't have to format and reinstall. This is not Windows... :-) I mean, in Linux you can always have a look "under the hood" to see what's wrong, fix it and have your system back without restarting from scratch. There aren't things that happen behind your back or settings that are hidden from your view.

The first thing I'd do in this situation is start a shell and run "top" to see if there's some process taking up all your CPU time. Once you identify it you need to find out if it is a process you can do without, in that case you can just "kill" it, or if it's something you need, and in that case you'll have to investigate further to see what's wrong with it.

Anyway in my experience Linux very rarely changes its behaviour on its own. You probably **did** something that broke something else. Maybe an update or something: Ubuntu has been quite unlucky with updates lately. Try to think what you've done: even the most insignificant change could be causing your problem.

Google and this forum will certainly help you in your quest. Good luck.

> 
Can I re-install on top of the existing system so that I don't have to re-install and re-configure all my programs again?

If you have your /home directory in a separate partition, leave it alone, format the other ones, and you'll be fine: your personal settings will be there once you finish reinstalling. If not, you should consider backing it up, including the hidden directories, the ones starting with a "." that you usually don't see in the file browser.

This way you'll lose the system-wide settings though. But I don't think you have changed that much, so it shouldn't take too long and be too hard to redo those.

I hope this helps you at least a little bit.

Ciao.
-- 
Mac

---

### Post by gfd on 2006-09-17
Thanks MacMan,

> The first thing I'd do in this situation is start a shell and run "top" to see if there's some process taking up all your CPU time.

I just did that and in the CPU line at the top I get:
0% us, 0.3% sy, 0% ni, 99.7% id, and 0% for the others.

What does the "99.7% id" refer too?
I can't see any process that takes up that much in the list (how do I scroll down the list btw?).

thanks

---

### Post by gfd on 2006-09-17
Ok, now it's the gnome-terminal that's taking up 99.7% of the CPU.
I killed it but it didn't really make any difference.

---

### Post by MacMan on 2006-09-17
> **gfd said:**
> Ok, now it's the gnome-terminal that's taking up 99.7% of the CPU.
I killed it but it didn't really make any difference.

Poor gnome-terminal, I don't think it was doing anything wrong... :-)

Try resetting your gnome settings: open a console and type:
```
mv ~/.gnome ~/.gnome.backup
```

Then logout, login again and see if it makes any difference. If it doesn't, you can go back to your original configuration.
```
rm -rf ~/.gnome
mv ~/.gnome.backup ~/.gnome
```

Then logout and login again and you should be back to your original settings.
**BE VERY CAREFUL** with that rm -rf command: if you use it the wrong way it will delete everything in your home directory. Be sure to spell it exactly. If you want to be extra-sure don't use the "f" option, i.e. type:
```
rm -r ~/.gnome
```
For every file in the dir it will ask you if you want to delete it. Boring but safer.

Have you thought about what you may have changed before the system started misbehaving? Have you updated any package? Changed any settings? Added any hardware?

Good luck.
-- 
Mac

---

### Post by 3rdalbum on 2006-09-17
Gnome-terminal has probably only appeared at the top of the list briefly because it is the frontmost program. Try running top from Control-Alt-F1, and let it update a few times.

Have you installed Preload or Prelink?

---

### Post by gfd on 2006-09-17
> Poor gnome-terminal, I don't think it was doing anything wrong...
:-\" 

> Try resetting your gnome settings...
Excellent! I believe it's fixed now.
You can't imagine how grateful I am Mac.
I really thought I'd have to format and start again...

> Have you installed Preload or Prelink?
Nop.

> Have you thought about what you may have changed before the system started misbehaving?
A lot!! But I really can't tell because I installed quite a few things yesterday... I'm only a 3 day Ubuntu/Linux user you see...

Anyway, thank you very very much for your help guys, it's much appreciated.

---

