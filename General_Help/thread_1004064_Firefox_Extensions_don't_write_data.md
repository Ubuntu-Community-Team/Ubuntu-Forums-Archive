---
title: "Firefox Extensions don't write data"
date: 2008-12-06
forum: General Help
---

### Post by Neovos on 2008-12-06
Hardy 8.04
Firefox 3.0.4

So I have an interesting problem with Firefox. None of my extensions want to save any changes I make in the tools>addons>extensions location or anywhere else for that matter. I make a change and it doesn't stick when I close and re-open the window. This also manifests itself in the Session Saver and Taboo extensions which I have buttons for. When I click on those buttons, the menu pops up but when I click on anything it just closes the menu and does nothing. Also, if anyone has Session manager, it changes the options on the buttons based on if your doing an "Auto-save" session or not. Well without ever clicking the "auto-save" session, that is what options appear to me and not the default ones. The "re-open tab" button supplied by the Session Manager extension does not update the list of close tabs nor does anything happen when I click in there.

The interesting thing is also that when I right click on my empty tab bar, the "undo close tab" button doesn't work either. So my hunch is that something in firefox regarding access to tab session info is locked or just not being updated. Maybe that and something wrong with extension config files, but I'm not sure where those would be.

A peculiar thing happens also when I start firefox, the session manager pops up that would normally let me choose previous sessions, I get the first pic below, I then resize it and just click cancel and it starts firefox. 

Now the really interesting thing is that the one time where all this stuff works and I can actually see closed tabs and saved sessions and all is great, is when I update an extension or install or uninstall an extension. When firefox opens after updating or installing, all works as normal until I close firefox and restart again, back to seeing nothing and having nothing work. This occured for me in firefox 3.0.2 and has persisted through some reinstalls and updates so I'm not quite sure what to try next. Any ideas?

---

### Post by dcstar on 2008-12-07
> **Neovos said:**
> 
.......
Now the really interesting thing is that the one time where all this stuff works and I can actually see closed tabs and saved sessions and all is great, is when I update an extension or install or uninstall an extension. When firefox opens after updating or installing, all works as normal until I close firefox and restart again, back to seeing nothing and having nothing work. This occured for me in firefox 3.0.2 and has persisted through some reinstalls and updates so I'm not quite sure what to try next. Any ideas?

Check the permissions on your .mozilla directory, something may now be root only R/W so your user account can no long write to it.

---

### Post by Neovos on 2008-12-07
I checked that already, even did a recursive user-rw group-r of that folder to make sure. Same problem still. Isn't there plugin info in a /var/usr or /usr folder somewhere?

---

### Post by Neovos on 2009-03-07
uninstalled the torbutton extension from my firefox and all started working again after MONTHS. Don't ask me how because I have NO clue.

---

