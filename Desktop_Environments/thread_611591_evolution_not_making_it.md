---
title: "evolution not making it"
date: 2007-11-13
forum: Desktop Environments
---

### Post by kornelix on 2007-11-13
I switched from thunderbird to evolution because evolution comes by default with gnome. I am about to switch back. Before I do that, I wonder what others have to say about the issues I have with evolution?

Purging trash is all or nothing. Thunderbird let me auto purge trash mails older than 30 days or whatever.

Moving mails among folders is clumsy.

I cannot omit trash mails from my backup list. Trash mails are imbedded in the same files with other mails and are only flagged as trash in another file with metadata.

Mails are not single files that can be moved elsewhere if wanted. Every folder is a giant html file containing all the mails ever put into that folder, including the mails flagged as trash. This will become unwieldy over time (the files will grow to hundreds of megabytes).

Overall, this strikes me as a technically dumb way to manage mail. Or what am I missing here?

---

### Post by chimerazz on 2007-11-13
I Have the same problem with evolution i think it is not well developed to support imap to the whole extent

This is a bug i hope so and evolution developers are in the way to fixing it.
 Till then i guess we have to use thunderbird +lightning extension for the better PIM Management :( :-?

---

### Post by erginemr on 2007-11-13
> **kornelix said:**
> I switched from thunderbird to evolution because evolution comes by default with gnome. I am about to switch back. Before I do that, I wonder what others have to say about the issues I have with evolution?

Purging trash is all or nothing. Thunderbird let me auto purge trash mails older than 30 days or whatever.

Moving mails among folders is clumsy.

I cannot omit trash mails from my backup list. Trash mails are imbedded in the same files with other mails and are only flagged as trash in another file with metadata.

Mails are not single files that can be moved elsewhere if wanted. Every folder is a giant html file containing all the mails ever put into that folder, including the mails flagged as trash. This will become unwieldy over time (the files will grow to hundreds of megabytes).

Overall, this strikes me as a technically dumb way to manage mail. Or what am I missing here?

I agree with you. I also like Thunderbird better and am using it together with the Lightning extension under Windows at work. To me Evolution acts like a clumsy giant, while Thunderbird looks like an agile and slick bird. 

I am still reluctant to leave Evolution under Linux, because it is integrated well into the Gnome desktop and I do not want to break the bonds. Other than that, Thunderbird + Lightning (its scheduler add-on) is a mighty couple that can compete with Evolution's power on every ground.

Speaking of the huge mail box file sizes under Evolution, AFAIK, Thunderbird also uses one file for Inbox, one for Sent mails, etc. that hold all the mails in the corresponding mail folder. So, it has the same approach as Evolution. At least under Windows...

---

### Post by AlistairH on 2007-11-13
I'm the same here. I'd like to remove Evolution from my machine but when I tried to do so I was told ubuntu-desktop would also be removed. Any one have any ideas on how to remove evolution without breaking my desktop?

---

### Post by erginemr on 2007-11-13
> **AlistairH said:**
> I'm the same here. I'd like to remove Evolution from my machine but when I tried to do so I was told ubuntu-desktop would also be removed. Any one have any ideas on how to remove evolution without breaking my desktop?

Hello,

Actually, you can safely remove Evolution along with the ubuntu-desktop. Ubuntu-desktop is actually a meta-package, a virtual package that holds the names of the packages which forms the Ubuntu's selcetion of applications.

When I was using Edgy, I decided to ditch Ekiga Softphone because although Ekiga was a very good software in its own right, I was not planning to use my computer for phone calls. When I attempted to remove it, my computer protested with a serious-looking warning that "if I uninstall this, the ubuntu-desktop will also be gone".

I was petrified at the idea first (was still a newbie in Ubuntu those days), I thought my complete desktop would crash if I continue. But when I uninstalled Ekiga along with ubuntu-desktop, nothing happened. I could still use my computer, run the update manager, install, uninstall and update the packages.

To my knowledge, the only thing that ubuntu-desktop has a use for is that; it is needed when you upgrade from say Feisty to Gutsy. Even in that case, it is not recommended to upgrade, but is advised to do a fresh install instead.

So, you have nothing to lose. This way, you will have a more "free" desktop with your selection of applications rather than predetermined ones. If worse comes worst, or at the time of upgrade to Hardy when it is released, you can reinstall ubuntu-desktop from the repositories.

---

### Post by AlistairH on 2007-11-13
> **erginemr said:**
> Actually, you can safely remove Evolution along with the ubuntu-desktop.

So it seems... Thanks. Evolution will evolve no more.

---

