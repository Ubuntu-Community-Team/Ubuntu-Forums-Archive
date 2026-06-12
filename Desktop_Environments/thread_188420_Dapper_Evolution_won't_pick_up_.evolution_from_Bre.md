---
title: "Dapper Evolution won't pick up .evolution from Breezy"
date: 2006-06-04
forum: Desktop Environments
---

### Post by flabbah on 2006-06-04
I just completed a fresh install of Dapper. I backed up important directories from my previous Breezy installation ... like ".evolution" (in my home directory).

So now that everything is freshly installed and I am in my new environment, I just copied my old .evolution folder to my home dir ...

But that didn't seem to do anything at all. When I start Evolution, it want to set up new accounts - it completely ignores my newly restored .evolution folder.

Can anybody help? I just want to use my old settings / contacts / mail.

Thanks
-Flabbah

---

### Post by Rondonjin on 2006-06-04
[QUOTE=flabbah]I just completed a fresh install of Dapper. I backed up important directories from my previous Breezy installation ... like ".evolution" (in my home directory).

So now that everything is freshly installed and I am in my new environment, I just copied my old .evolution folder to my home dir ...

But that didn't seem to do anything at all. When I start Evolution, it want to set up new accounts - it completely ignores my newly restored .evolution folder.

Can anybody help? I just want to use my old settings / contacts / mail.

Thanks
-Flabbah[/QUOTE]

First off, I hope you have your /home on a seperate partition :-)

Secondly, you're out of luck. Yes, your mails are still there in the hidden  .evolution directory but sadly your accounts are not. They are kept under the hidden .gnome2_private and .gconf/apps/evolution directories :( 

I've been bitten by this in the past and made sure to save those two directories this time, along with .evolution which holds the actual mailboxes.

Once you setup your accounts again your mails will be visible.

Wayne

---

