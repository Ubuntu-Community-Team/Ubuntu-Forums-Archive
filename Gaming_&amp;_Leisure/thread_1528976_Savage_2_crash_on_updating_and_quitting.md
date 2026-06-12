---
title: "Savage 2 crash on updating and quitting"
date: 2010-07-11
forum: Gaming &amp; Leisure
---

### Post by ucal on 2010-07-11
I can play the practice mode just fine, however, when I try and login, it crashes when it gets to the extracting update stage.  I've tried running the dedicated server (for several hours actually), and savage2_update.bin as well, but no luck.  Any ideas?

---

### Post by Zirts on 2011-03-24
Same problem here!

---

### Post by donkyhotay on 2011-03-24
Launch the client from the CLI (terminal) and try to connect. Copy/paste the crash dump here, maybe that will give us a better hint as to why it's not updating properly.

---

### Post by Zirts on 2011-03-25
Well,  update problem is fixed,   basicly I launched the game from CLI like you told,   and it updated the game in there after like 10 minutes lol.
so when I typed 'version' there,  it say's I'm on the latest one.

Now as for the exiting problem: It only crashes after I have played a match in Savage 2,  if I don't (just starting up the game and then exiting) it wont crash.

The crash happens in both if I close the game after a match, or in the main menu. The crash wont let me use keyboard combinations like Ctrl+Alt+Delete to shut down the computer, mouse won't move and so on but the music still keeps playing.

---

### Post by donkyhotay on 2011-03-26
ctrl-alt-del is more of a windows thing, try ctrl-alt-f1 and see if you get the terminal (though it won't be the same one you launched from. If you don't then it means the system has crashed hard and I'd start looking at your video drivers (got an ATI card? they've been having lots of issues lately). If you do get the terminal then you have me stumped as I'm not having any issues with savage2 myself. Don't play often these days but I did try it just now and was able to get into the game and out without crashing and I used to play all the time without problems.

---

### Post by Zirts on 2011-03-26
Ok,  so when the game crashed,   I was still able to go to the Terminal with ctrl alt f1,  so yeah I guess it's not the graphics problem but it's something else....

---

### Post by donkyhotay on 2011-03-26
Any chance you can launch savage2 from the CLI and then alt-tab to the terminal after it crashes to get the console dump?

---

### Post by Andrenap on 2011-03-26
I'm having the same problem here. Trying to update as Zirts did. Just to be sure, by run from terminal u mean like ~/.Games/Savage2/savage2.bin right? (i know, patch may change, i'm just trying to make a point). I'll reply again if I succeed/fail on it...
Edit: and also, without sudo, right?

---

### Post by Zirts on 2011-03-27
Doesen't matter if it's with it or not.

---

### Post by Andrenap on 2011-03-27
as  i thought. it didnt  work here... any other tips?

---

### Post by Ellume on 2011-04-08
I am having a similar issue with updating Savage2. When I try to login it checks for updates, finds there is one, downloads it, then restarts the game. The update is never applied. When running from the CLI I get the message:
```
warning: The VAD has been replaced by a hack pending a complete rewrite
```
My first reaction is that maybe it is a permissions problem, but the problem persists even when it seems I have full permissions to write files.

---

### Post by Ellume on 2011-04-08
Well found an answer to my problem somewhere on the Savage2 forum:
> start game, don't log in.

enter console: ctrl+f8
enter command: SetSave upd_checkforupdates "false"
exit console: ctrl+f8
Login.
You are done.

Don't worry, there won't be any updates for a LONG time. If there are, you will get an incompatible version error and you can change upd_checkforupdates back to true.

---

### Post by theOGRE on 2011-07-09
@Ellume [COLOR=Purple]enter command: SetSave upd_checkforupdates "false"

[COLOR=Black]Thank you very much! That got me playing... now to try and learn to not play like garbage. :P[/COLOR]
[/COLOR]

---

