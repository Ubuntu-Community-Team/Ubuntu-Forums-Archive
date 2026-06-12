---
title: "Setting up a second X screen."
date: 2005-12-10
forum: General Help
---

### Post by bb002 on 2005-12-10
I just borked by system about 3 hours ago and just finally got all back up and running. Except I can't find this post that showed you how to create another X desktop at alt+ctrl+f8 for running games so you could easily switch between your desktop and the game. It was on this website somewhere but I can't find it now. Now I am wondering if anyone knows where that post is or would post me a howto.



For those that are curious I ruined my system through a typo....
I was wiping all the files out from a folder in my home directory that for some reason was owned by root. so i intended to delete them with "sudo -r ./*".  Can you guess what went wrong? That's right in the command I actually typed i missed the period. The command wiped out the "/boot" folder and enough of "/bin", needless to say, that I was screwed.

---

### Post by ninotob on 2005-12-10
:smile: 

I'm not laughing at you, I'm remembering when I did a similar thing.  

I had installed a new distro as well as a larger HD -- I put the old one in a USB shell.  After spending some days getting it set up to my satisfaction, and transfering the data off the old drive, which I had mounted at /mnt/usb, I decided to take one last look around the USB drive (which had the exact same directory structure as my new system, just "/mnt/usb" prepended), declared it clean and (as root mind you), typed "cd /" (intending to go to the bottom of the usb drive) and then "rm -rf *".  

I sat back but after a little while, I noticed that the HD sounds were coming from inside my computer and not the USB shell ..... yes, I swore.  It's hillarious now though.

---

### Post by xmastree on 2005-12-10
Applications > System Tools > New Login

or, on breezy (IIRC) if you lock your screen, then move the mouse, there's an option to log in as a different user.

---

### Post by amohanty on 2005-12-10
> I was wiping all the files out from a folder in my home directory that for some reason was owned by root. so i intended to delete them with "sudo -r ./*". Can you guess what went wrong? That's right in the command I actually typed i missed the period. The command wiped out the "/boot" folder and enough of "/bin", needless to say, that I was screwed.

:) Thats why my rm is aliased to 
```
echo Use del and purge you moron!
```

and I have a couple of bash scripts:
del - to move whatever I delete to ~/.Trash
purge - to remove everything from ~/.Trash
lt - to list everything on ~/.Trash

---

### Post by matthewv on 2005-12-10
Just wondering.. don't know if this is related, but it seems that on my system you can no longer switch between open sessions, console, etc. by pressing ctrl+alt+F7, or ctrl+alt+F*

---

### Post by bb002 on 2005-12-10
Your methods would work **xmastree** but isn't the one I'm searching for.

The second X session that I'm talking about requires that you edit a few config files then run "xinit" along with a few other commands to end up with a X session that terminates when the game does. The only program attached to that x session is the game.

So if i wanted to could drop to a terminal with ctrl+alt+f1 do "sudo /etc/init.d/gdm stop". then run xinit and what ever else it is that i have to run to end up with X session running only the game. No gnome, nautilus, gdm, and whatever else there is in a standard desktop enviornment to worry about.

Maybe getting some sleep would do me some good....Naaa. :)

---

### Post by bb002 on 2005-12-10
Hey Hey whadda know...Skipping out on a nights sleep helped me find the post I was after. [http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

It wasn't like it was on the 38th page or anything.....You'd think searching for "HOWTO" would have yielded better results. I'm just joking people, just joking. After typing the first sentence of my last post I suddenly remembered that the X session i was after contained xinit. So i finished my post and proceeded to search the forums for "xinit".

---

### Post by jeffus_il on 2007-12-25
Applications > System Tools > New Login
isn't on my menu,

what does work is the "user switcher" added to the panel,
logging in as the same user hangs for me, because one of the panel applets doesn't like to be opened twice,

Auto running can be done in the System->Preferences->Session

How does that sound?

---

