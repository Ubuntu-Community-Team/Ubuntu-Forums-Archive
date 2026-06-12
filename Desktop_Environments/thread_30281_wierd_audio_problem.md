---
title: "wierd audio problem"
date: 2005-04-28
forum: Desktop Environments
---

### Post by royg1234 on 2005-04-28
First post!  Anyway, when the login screen first pops up, that Flinstones running sound comes on, so audio is all ok just in the login, but after that it just poops out.

I've tested the sound in the Sound prefernces [System>Preferences>Sound Preferences].  None of the sound events will play when I hit "Play" int he Sound Events tab.

I also tested by trying to play an .ogg file (don't want to mess with mp3 yet), Totem and Music Player both error-msg me (verbatim including bold and whatnot):
[INDENT]
**"Totem could not play 'xxxxxxx'**.  Could not open resource for writing.[/INDENT]

When I open amarok, it messages me (w/ title "Informational - artsmessage"): 

[INDENT]Sound server informational message: <br><br>Error while initializing sound driver: <br><br>device /dev/dsp can't be opened (Permission denied) <br><br>The sound server will continue, using the null output device.[/INDENT]

Let me reiterate: the sound events at the login screen work.  What gives?

P.S.  I'm 100% n00b; lifelong Windows user, and haven't used DOS since the Windows 3.1 days.  And is the post icon I chose supposed to be screaming, or yawning?  I guess both apply right now.

---

### Post by accuser on 2005-04-28
It may be that the account you are using does not have the priveleges for using the audio devices. To check and/or change this, click the menu System->Administration->Users and Groups. Find your username in the list of users, click it and click the Properties button to the right of the list. A dialog box will appear, with three main tabs: Account, Advanced, and User privileges. Click the User priveleges tab. You will see a list of user priveleges - the one you are interested in it Use audio devices - make sure that this is ticked.

---

### Post by royg1234 on 2005-04-30
LOL.  Thanks.  That was pretty obvious.

---

