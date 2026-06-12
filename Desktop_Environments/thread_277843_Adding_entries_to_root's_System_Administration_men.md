---
title: "Adding entries to root's System Administration menu"
date: 2006-10-15
forum: Desktop Environments
---

### Post by mcriley on 2006-10-15
Hi, first off, I'm an "old school" root-is-admin Unix user so I'm working to configure my first use here of Ubuntu accordingly.

The System/Adminstration menu for the root account has only five entries, while regular users' Administration menu contains the whole set of 20 or so. I understand why it was set up that way and how it's intended to work, but like I said, I'm an old guy and want it to work my way :-)

I want to add the missing Admin actions to root's System/Admin menu but I can't seem to figure out how. The System menu's drop-down menu has the "Edit Menus" option, which brings up the ala carte menu, but it shows all the Admin functions enabled, which is _not_ what I see on the actual Admin menu. I tried toggling the Visible checkbox to off and then back on, then logged out of root and back on, but nothing changed.

I would appreciate some advice on this.

Oh, and by the way, I decided to try Ubuntu after spending days trying to get the latest SuSE Linux distribution to work right--Ubuntu absolutely blows SuSE out of the water.  Despite my little issue above, Ubuntu has been a pleasure setting up.

Thanks,

Marc

---

### Post by mcriley on 2006-10-18
I stumbled across what I needed to do here, so I'm posting it for future reference in case anyone else finds themselves in this situation.

It's very simple actually...

Since I've enabled 'root' as a full-up user, I simply needed to go into System/Administration/Users and Groups, make sure "Show all users and groups" is checked, then highlight the 'root' user and click Properties.

On the User Privileges tab, nothing was selected, so I simply needed to go through and select (enable) all the privileges. Voila, root's admin menu got completely filled out.

---

### Post by bburgin on 2006-12-15
Stumbled across your post and it was exactly what I needed.  Thanks

---

