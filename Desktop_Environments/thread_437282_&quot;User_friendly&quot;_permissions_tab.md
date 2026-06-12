---
title: "&quot;User friendly&quot; permissions tab"
date: 2007-05-08
forum: Desktop Environments
---

### Post by B-Con on 2007-05-08
I upgraded to Feisty just recently and my main complaint is... well... the user friendliness. Some aspects of it just seem too cute and user friendly for me.

The biggest thing I hate is the permissions tab for files/folders. Instead of having individual check boxes for the permissions of each group of users and each permission, there is now a stupid "read" or "read and write" access pulldown menu, and one generic "allow execution" checkbox at the bottom that applies to everything. (I don't know if this is new as of 7.04, I just upgraded from 6.06.)

Is this "feature" Gnome or Ubuntu's fault? And is it possible at all to revert it back to the previous way it was?

---

### Post by CameO73 on 2007-05-08
Ehrmm... the **chmod** command may be more to your liking. :D

I know, it's not an answer. But honestly I don't know. I usually set the permissions using the console, so it doesn't bother me that much.

I must admit I too am interested in a way to change Nautilus to a more 'advanced mode'. The [current information on Nautilus]("http://live.gnome.org/Nautilus") does suggest it is moving towards a more userfriendly approach. The 'Open In Terminal' option was also removed from the folder context menu (but can be restored by using the **nautilus-open-terminal** package).

---

### Post by mcduck on 2007-05-08
If you want the old style permissions in Nautilus, you can do that with Configuration Editor. Just hit Alt-F2 and tun 'gconf-editor', then browse to apps/nautilus/preferences and enable 'show_advanced_permissions'.

---

### Post by B-Con on 2007-05-09
Cool, thanks. ^

Yeah, Came, I use chmod usually too since I usually work via the command line, it's just that on occation when I use the GUI method it feels... I dunno, icky. And it also doesn't let me customize who can execute stuff, which I don't like. But mcduck fixed that, cheers. :)

---

### Post by CameO73 on 2007-05-09
That did the trick! Still, I think they should have added an 'Advanced' toggle button for the Permissions tab (instead of burying it in the Gnome Configuration Editor). Hmmm... let's see where I can file a feature request...

On a slightly unrelated note: I really like the apps -> Evince -> override_restrictions option!

---

### Post by TheTux on 2007-05-09
> **CameO73 said:**
> 
On a slightly unrelated note: I really like the apps -> Evince -> override_restrictions option!

thanks for the tip. Never though could do so.

I installed the nautilus-open-terminal package but it doesn't appear in the context menu. Anything i should do first?

---

### Post by mcduck on 2007-05-09
> **TheTux said:**
> thanks for the tip. Never though could do so.

I installed the nautilus-open-terminal package but it doesn't appear in the context menu. Anything i should do first?

Log out and back again, or run 'killall nautilus' to restart Nautilus.

---

### Post by B-Con on 2007-05-11
> **mcduck said:**
> Log out and back again, or run 'killall nautilus' to restart Nautilus.
I wouldn't recommend "killall nautilus". I remember back in Dapper doing so would  break the System -> Shutdown panel, removing the "Turn Off" and "Hibernate" options. I did this with (IIRC) three independent versions of Dapper, so I'm pretty sure it wasn't just a freak chance. Don't know if this'll also break the panel in Feisty, but probably not worth risking to avoid a reboot.

Wouldn't "/etc/init.d/gdm restart" work as well?

---

### Post by TheTux on 2007-05-11
It's working now. I just logged out and in back and then it appears in the menu.

---

### Post by mcduck on 2007-05-11
> **B-Con said:**
> I wouldn't recommend "killall nautilus". I remember back in Dapper doing so would  break the System -> Shutdown panel, removing the "Turn Off" and "Hibernate" options. I did this with (IIRC) three independent versions of Dapper, so I'm pretty sure it wasn't just a freak chance. Don't know if this'll also break the panel in Feisty, but probably not worth risking to avoid a reboot.

Wouldn't "/etc/init.d/gdm restart" work as well?

It's never done that for me, in any Ubuntu version. Not in any of the machines where I have installed Ubuntu.. It just restarts the desktop/file manager. It should have nothing to do with the shutdown panel.

---

### Post by B-Con on 2007-05-12
> **mcduck said:**
> It's never done that for me, in any Ubuntu version. Not in any of the machines where I have installed Ubuntu.. It just restarts the desktop/file manager. It should have nothing to do with the shutdown panel.
Oh, my bad. I'm thinking of "killall gdm" -- hence the last line of my post. Yeah, no problem for nautilus.

Carry on... :p

---

