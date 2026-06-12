---
title: "Cedega doesnt work after Ubuntu reboot"
date: 2006-03-17
forum: Gaming &amp; Leisure
---

### Post by chowyunpat on 2006-03-17
I was pretty impressed with Cedega, I am using the time demoversion  5.1 and I installed Vice City and I was playing it for a few minutes just to test it out and then I closed Cedega and restarted Ubuntu and tried Cedega and I cant get Vice City or install another game, when I hit play or install nothing happens.  I suspect its something to do with the CD permissions.  

How do I solve this problem?

---

### Post by Perfect Storm on 2006-03-18
Any error output in the terminal?

---

### Post by chowyunpat on 2006-03-18
Nothing at all happens, even though my cd0 and cd1 are both mounted.  nothing happens and I get no error message.

Im using Breezy Badger 5.10 btw.

---

### Post by chowyunpat on 2006-03-18
Duh.. I wasnt run the bin file from the terminal.   No wonder I couldnt find out the problem, I finally found located the cedega file and I ran it from the terminal and when I click on the icon for Play Vice City or click the Play button this is what I get in the terminal.


[I]Traceback (most recent call last):
  File "/usr/local/games/transgaming_cedega_timedemo/usr/lib/transgaming_cedega_timedemo/Point2Play_gui.py", line 1552, in play_cb
    self.play_game()
  File "/usr/local/games/transgaming_cedega_timedemo/usr/lib/transgaming_cedega_timedemo/Point2Play_gui.py", line 1539, in play_game
    retval = self.Point2Play.winex( 0, game_name, i["Path"], i["Workdir"], debug_channel=debug_channel, output_file=output_file, output_console=output_console, run_in_gdb=run_in_gdb, OverrideGameProfile=None)
  File "/usr/local/games/transgaming_cedega_timedemo/usr/lib/transgaming_cedega_timedemo/Point2Play.py", line 1044, in winex
    os.unlink ( path + "config" )
OSError: [Errno 13] Permission denied: '/usr/local/games/transgaming_cedega_timedemo/.cedega_timedemo/Grand Theft Auto Vice City/config'


[/I]
I hope that helps

---

### Post by chowyunpat on 2006-03-20
I found the problem, after I reinstalled Ubuntu and reinstalled Cedega, I found that sometimes I have to switch CD-ROMS and sometimes I have to reboot Ubuntu and the time demo will work fine and since I have done these things,  I have installed both Vice City and GTA III and I'm happy to report they are working fine.

---

