---
title: "Compiz does not load after logoff/logon - revisiting"
date: 2009-07-01
forum: Desktop Environments
---

### Post by Crio on 2009-07-01
I have problem similar to the one described here: [http://ubuntuforums.org/showthread.php?t=869688](http://ubuntuforums.org/showthread.php?t=869688) and elsewhere. 
Namely: when I choose Normal/Enhanced Visual Effects in the Appearance config (Jaunty), compiz starts up fine and works without problems. But after logout/login cycle it is not running though it should, shouldn't it? 
I can work the problem around by adding compiz manually to startup list - that works - but it seems really weird to me and I'd like to root the problem out (since I'm not the only one affected by it).

I'm running AWN manager and during logout I can see its warning "Screen is not composited"; i.e. compiz have already been shut down and awn has not been yet. That makes me think - is it possible that during shutdown Visual effects are getting switched off somehow? Could someone enlighten me, please, where Visual Effect settings are stored and how compiz is supposed to be loaded on logon? Via saved-session? (what if user does not save his sessions?)  Are there any useful logs? Any suggestions for tests?

Thank you very much for your help.

P.S.: By the way, I think I did not have this problem in 8.04 and 8.10, but previous threads mention different versions.

---

### Post by AoSteve on 2009-07-01
Have you tried rebooting with it disabled, then re-enable it?   Maybe that will reset it to the end of the shutdown process?   As for starting up, I'd imagine that's in compizconfig-settings-manager somewhere, but I'd have to check...   I'll look around though.

---

### Post by Crio on 2009-07-02
Ok, I think, I've got that straightened up and it has actually little to do with compiz.

It seems that Appearance config does nothing to provide for starting compiz on next login relying instead on session management. So, if the session is not autosaved on exit (or saved otherwise) changes are not preserved. Could someone confirm that? Is this a bug or a feature? 

Worse, behavior of "Startup Applications" config is a bit unintuitive. When "Autosave applications on exit" checkbox is checked everything works as one can expect; but when it is unchecked, session manager loads last saved session (i.e. the last session when the checkbox was checked) instead of a clean session with applications from the "Startup Applications" tab.
This also looks very much like a bug in my opinion. Is it?

I remember that in previous versions there was a button "Save current applications" and I thought it was very handy (though it did not work in 8.10). Can we have it back, please?

---

### Post by bandofmercy on 2009-07-27
i'm having this problem too, right down to the "no compiz" message popping up on my awn on logout.  help with a permanent fix anyone?

---

