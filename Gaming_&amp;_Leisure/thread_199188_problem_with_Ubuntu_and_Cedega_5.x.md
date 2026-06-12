---
title: "problem with Ubuntu and Cedega 5.x"
date: 2006-06-18
forum: Gaming &amp; Leisure
---

### Post by phinn on 2006-06-18
I posted this on the Cedega forums too but I'm going to post here aswell incase other people have problems.

Cedega 5.2 in my case (I tried older versions too) load fine until you actually try and install something. When you enter in the Game Folder and Installer path and click Continue the whole thing just hangs and does nothing for me. ](*,) 

I saw an older post on the forums with someone with this same problem and he removed wine to fix it.  I don't have wine installed as right now I'm using the base install of 6.06 with whatever updates have been released.

Anyone have any insite?
Thanks

---

### Post by Perfect Storm on 2006-06-18
Sound strange? Which structure of Ubuntu do you run? Any output if you starts cedega through the terminal?

---

### Post by phinn on 2006-06-20
I'm really not sure what you mean by "structure" I am running the base install of Ubuntu Desktop 6.06 with all the updates.

Whenever I click continue on that install dialog box it just hangs for a while and does nothing.

If I kill it it says this however.  Any further help would be great:


Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 1751, in install_menu_cb
    retval = self.Point2Play.winex( 1, game, install, None, self.Point2Play.gamedir + game + "/" + "games.ini.new", winexver_touse, ( dos_cwd, big_exe, pthreads_option ), ModifiedInstallConfigs=custom_installer_config, debug_channel=debug_channel, output_file=output_file, output_console=output_console, run_in_gdb=run_in_gdb, MonitorCdromEject=cd_eject_monitoring, gddb_file=gddb_file  )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 1211, in winex
    while gtk.events_pending():
KeyboardInterrupt

---

### Post by Perfect Storm on 2006-06-21
Do you use i386, ppc, a64 etc.?

---

### Post by YuRaider on 2006-06-22
I have the same problem here. Cedega worked just fine before I have updated Dapper. Now, I have the same problem when I click continue.

---

### Post by handy on 2006-06-22
I have drive drawers, sounds funny eh!?

So, I slip my Ubuntu Breezy drive in & boot from it easily.  (yes it still requires a reboot, which IS actually a pain, because after booting with Breezy, to play Guild Wars, I often browse the web, & bookmark sites, that naturaly are then NOT on my Dapper drive!  Can't easily copy my Bookmarks because I don't have a fat32 partition anymore :)
)

Anyway, this post is just to add to the ***I can't use Cedega in Dapper*** lobby.  I only want to play GW in Cedega & I can't in Dapper.  Have I said it enough times yet! :KS

**[Edit:] I don't want to have a schizophrenic computer, that's one of the reasons why I left windoze, I can't quite remember the other reason just now... There must have been one though...** :KS

---

### Post by Paool on 2006-06-26
same problem here... :( did anyone found solution for this problem? :/

---

