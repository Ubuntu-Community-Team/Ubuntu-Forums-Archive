---
title: "Gnome panels missing"
date: 2007-05-26
forum: Desktop Environments
---

### Post by CarVac on 2007-05-26
Today, I logged on my Ubuntu Feisty computer, on Gnome, and the bottom panel (with the taskbar and desktop manager) was missing. I logged off, and in XFCE nothing was wrong. I checked some posts and they suggested running 'gnome-panel.' Doing this, it says "I've detected a panel already running, and will now exit."
What could be wrong?

---

### Post by CarVac on 2007-05-26
Whoops
I forgot to mention that now I'm back on Gnome, and unfortunately *both* panels are gone!

---

### Post by CarVac on 2007-05-26
I logged off and on again, and now the desktop icons are missing too. However, Alt-F2 still works, allowing me to launch my browser...

---

### Post by arijarot on 2007-05-26
try ```
sudo killall gnome-panel
```

then ```
 gnome-panel

```

---

### Post by CarVac on 2007-05-26
It was odd... I checked to see what Gnome packages were missing
and guess which was?
Gnome itself.
I wonder why it lost features one by one (and gained them back one by one once i installed the package)

---

### Post by arijarot on 2007-05-26
This is beyond me... at least it works now, right?

--
actually, just a thought, maybe you can try to reinstall your gnome display manager (gdm) or at least restart it...

---

### Post by robinl on 2007-05-27
I just had the same error, and gnome was removed for some reason after the last update...

---

### Post by robinl on 2007-05-27
Sorry for double-posting but after I sudo apt-get install gnome it still doesn't work. Gnome-panel is uninterruptable and I have no idea what to do now... ](*,)

---

### Post by blacksadness on 2007-05-27
I'm not sure how much it would help but try this:
go in gconf-editor (use alt +F2) go in apps/panel/general the last entry is called toplevel_id_list i'm not sure but i think this one sets the panel see if it has any entries, and add to it: bottom_panel_screen0 (by right click edit and then add) it should create a new panel..  then go in toplevels (a few entries under general) and edit this panel properties the way it suits you or just drag it visually
hope this helps

---

### Post by robinl on 2007-05-27
Sorry but it doesn't work, the setting in gconf-editor is exactly the same as you've described. The thing is, even alt+F2 doesn't work and I have to go into tty1 and run things like "gnome-terminal --display=:0". Seems like Gnome is still broken but I have no idea what part of it is broken.

---

### Post by blacksadness on 2007-05-27
i'm guessing you tried running gnome-panel the same way? (gnome-panel --display=:0) if for some reason that WORKS you could either delete your .gnome (but note that you will loose all your gnome customization) or add gnome-panel to your gnome-session-properties, but i actually doubt gnome-panel will start that way.. did you try an apt-get install -f?

---

### Post by robinl on 2007-05-27
No it doesn't work. sudo killall gnome-panel or killing it in system monitor doesn't do anything to the existing gnome-panel, which is interruptible and apparently have crashed.

---

### Post by blacksadness on 2007-05-27
sorry for the late reply
i think it should be killall -9 gnome-panel right?anyway try removing gnome-panel and reinstalling it again

---

### Post by robinl on 2007-05-27
killall -9 is the same, doesn't do anything to the gnome-terminal, and reinstalled gnome-panel with the same result. One interesting thing is, that when I run gnome-panel from fail-safe xterm this popped up in kern.log
```
May 27 23:13:13 ubuntu kernel: [   70.432000] CPU:    0
May 27 23:13:13 ubuntu kernel: [   70.432000] EIP:    0060:[<f8a46b51>]    Tainted: P      VLI
May 27 23:13:13 ubuntu kernel: [   70.432000] EFLAGS: 00010292   (2.6.20-15-generic #2)
May 27 23:13:13 ubuntu kernel: [   70.432000] EIP is at dx_probe+0x1e1/0x320 [ext3]
May 27 23:13:13 ubuntu kernel: [   70.432000] eax: 00000090   ebx: f6482000   ecx: 00000096   edx: 00000000
May 27 23:13:13 ubuntu kernel: [   70.432000] esi: f6482018   edi: f6ba0908   ebp: f7d4de50   esp: f688dca8
May 27 23:13:13 ubuntu kernel: [   70.432000] ds: 007b   es: 007b   ss: 0068
May 27 23:13:13 ubuntu kernel: [   70.432000] Process gnome-panel (pid: 5968, ti=f688c000 task=f7bd1560 task.ti=f688c000)
May 27 23:13:13 ubuntu kernel: [   70.432000] Stack: f8a52f28 f8a5226b f8a54d6d 00000180 f8a53078 f688dd94 00000000 00568039 
May 27 23:13:13 ubuntu kernel: [   70.432000]        6cccb7e8 f7829a00 f688dda4 f688dd7c f688de38 f8a4774b f688dd7c f688dda4 
May 27 23:13:13 ubuntu kernel: [   70.432000]        f89f8a24 00000050 00001000 f69bc358 f7865c00 00000000 f89f9037 00001000 
May 27 23:13:13 ubuntu kernel: [   70.432000] Call Trace:
May 27 23:13:13 ubuntu kernel: [   70.432000]  [<f8a4774b>] ext3_find_entry+0x28b/0x640 [ext3]
May 27 23:13:13 ubuntu kernel: [   70.432000]  [<f89f8a24>] find_revoke_record+0x54/0xa0 [jbd]
May 27 23:13:13 ubuntu kernel: [   70.432000]  [<f89f9037>] journal_cancel_revoke+0xc7/0xd0 [jbd]
May 27 23:13:13 ubuntu kernel: [   70.432000]  [__wake_up+56/80] __wake_up+0x38/0x50
May 27 23:13:13 ubuntu kernel: [   70.432000]  [<f8a4920c>] ext3_lookup+0x3c/0x100 [ext3]
May 27 23:13:13 ubuntu kernel: [   70.432000]  [d_alloc+263/400] d_alloc+0x107/0x190
May 27 23:13:13 ubuntu kernel: [   70.432000]  [do_lookup+328/400] do_lookup+0x148/0x190
May 27 23:13:13 ubuntu kernel: [   70.432000]  [__link_path_walk+2151/3696] __link_path_walk+0x867/0xe70
May 27 23:13:13 ubuntu kernel: [   70.432000]  [do_generic_mapping_read+1132/1392] do_generic_mapping_read+0x46c/0x570
May 27 23:13:13 ubuntu kernel: [   70.432000]  [link_path_walk+69/192] link_path_walk+0x45/0xc0
May 27 23:13:13 ubuntu kernel: [   70.432000]  [mutex_lock+8/32] mutex_lock+0x8/0x20
May 27 23:13:13 ubuntu kernel: [   70.432000]  [_atomic_dec_and_lock+61/112] _atomic_dec_and_lock+0x3d/0x70
May 27 23:13:13 ubuntu kernel: [   70.432000]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0
May 27 23:13:13 ubuntu kernel: [   70.432000]  [getname+167/208] getname+0xa7/0xd0
May 27 23:13:13 ubuntu kernel: [   70.432000]  [__user_walk_fd+59/96] __user_walk_fd+0x3b/0x60
May 27 23:13:13 ubuntu kernel: [   70.432000]  [vfs_lstat_fd+31/80] vfs_lstat_fd+0x1f/0x50
May 27 23:13:13 ubuntu kernel: [   70.432000]  [mutex_lock+8/32] mutex_lock+0x8/0x20
May 27 23:13:13 ubuntu kernel: [   70.432000]  [_atomic_dec_and_lock+61/112] _atomic_dec_and_lock+0x3d/0x70
May 27 23:13:13 ubuntu kernel: [   70.432000]  [sys_lstat64+15/48] sys_lstat64+0xf/0x30
May 27 23:13:13 ubuntu kernel: [   70.432000]  [do_page_fault+831/1520] do_page_fault+0x33f/0x5f0
May 27 23:13:13 ubuntu kernel: [   70.432000]  [do_page_fault+0/1520] do_page_fault+0x0/0x5f0
May 27 23:13:13 ubuntu kernel: [   70.432000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
May 27 23:13:13 ubuntu kernel: [   70.432000]  =======================
May 27 23:13:13 ubuntu kernel: [   70.432000] Code: 44 24 10 78 30 a5 f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 4d a5 f8 c7 44 24 04 6b 22 a5 f8 c7 04 24 28 2f a5 f8 e8 bf 00 6e c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 30 a5 f8 c7 44 24 04 6b 
May 27 23:13:13 ubuntu kernel: [   70.432000] EIP: [<f8a46b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:f688dca8
```
It looks like page fault but other than that I don't understand any of it.

---

### Post by robinl on 2007-05-27
With a bit more experimenting some GNOME applications also doesn't work, eg. Nautilus and Rhythmbox, which will also go into uninterruptible state after running. However things like gedit runs fine so probably not a GTK problem, but something within GNOME itself...

---

### Post by blacksadness on 2007-05-28
try another user, if it still fails on the other user then it's sth with the installation, if it works then delete your user's .gnome dir, also try removing gnome and doing an apt-get autoremove then reinstalling, i'm not sure but from the name it should remove all the dependencies, i don't' have experience in dpkg, but if anyone does what's the way to remove a complete pakage and its dependencies? 
last resort is reinstall, just back up your home directory if you don't have it separate, especially .mozilla .amsn .gaim and so on, and copy the archives from /var/cache/apt/archives to avoid downloading everything (that matters for my slow connection in here) then do a reinstall.. and separate your /home from the rest of the system, that way if sth ever happens you'll not really loose any work..

---

### Post by robinl on 2007-05-29
No another user doesn't work is well. Ah well I'll reinstall Ubuntu soon... Until then I'll just have to get on using the terminal.

---

### Post by robinl on 2007-05-30
Ok this is rather stupid but after discovering KDE having trouble opening one of my partitions I did a fsck -f in recover mode and now GNOME magically came back. It seems that EXT2IFS for Windows is rather dangerous in corrupting things...

---

