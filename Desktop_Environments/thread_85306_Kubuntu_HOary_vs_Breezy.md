---
title: "Kubuntu HOary vs Breezy"
date: 2005-11-02
forum: Desktop Environments
---

### Post by escobar on 2005-11-02
Last night I downgraded from Breezy to Hoary because of some issues I was unable to resolve in Breezy. Most of them were manageable, just annoying. Also, since going back to Hoary it just felt faster. I thought it was a pretty good move. Doing some poking around for instructions on upgrading my favorite apps like Amarok, K3b etc it seems as though Breezy is required in order to use them. 

Is this really the case? If so that would really suck.

---

### Post by daller on 2005-11-08
[QUOTE=escobar]Last night I downgraded from Breezy to Hoary because of some issues I was unable to resolve in Breezy. Most of them were manageable, just annoying. Also, since going back to Hoary it just felt faster. I thought it was a pretty good move. Doing some poking around for instructions on upgrading my favorite apps like Amarok, K3b etc it seems as though Breezy is required in order to use them. 

Is this really the case? If so that would really suck.[/QUOTE]

What problems did you encounter?

The newest packages often depends on some newer libraries... In my opinion upgrading all the needed libraries would be as "bad" as upgrading everything to breezy, but if you insist, I think you can change the /etc/apt/sources.list (replace hoary with breezy)

run a "sudo apt-get update"

then run "sudo apt-get remove amarok" (amarok as the example)

then "sudo apt-get install amarok" (You should now have the breezy version of amarok)

Amarok 1.3.5 is ONLY available with breezy!

Good luck!

---

### Post by shakin on 2005-11-08
You can upgrade to KDE 3.5 beta 2 from kubuntu.org. That'll get you some of the new apps you want.

---

### Post by escobar on 2005-11-08
Thanks. I more or less found the answer to this a little while or go but appreciate the help nonetheless.

---

