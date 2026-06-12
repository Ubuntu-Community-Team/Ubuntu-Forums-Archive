---
title: "Problem after running Synaptic Package Manager..."
date: 2009-06-24
forum: General Help
---

### Post by Bill Zimmerly on 2009-06-24
Using the Synaptic Package Manager, I installed a bunch of applications in alphabetical order from "c2hs" to "chronicle" and when finished, something in the list seemed to have broken my "System, Preferences, Network Connections" script (nm-connection-editor).

Before, it would run just fine, but now it fails to run from the (above) Menu sequence in Gnome.

I tried running it from the gnome terminal as follows...

bzimmerly@Quad:~$ sudo nm-connection-editor

And although the dialog pops up, I can't make any edits that will "stick". Every time I make a change to my eth0 connection and then try to save it (no matter what the change is, by the way) I get this error message dialog...

/-------------------------
| **Could not update connection**
| **PolicyKit authorization could not be created; invalid action ID.**
\-------------------------

And this is the text displayed in the Gnome terminal...

[B]bzimmerly@Quad:~$ sudo nm-connection-editor

(nm-connection-editor:15972): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed

** (nm-connection-editor:15972): WARNING **: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /etc/NetworkManager/VPN.
[WARN 15972] polkit-action.c:211: polkit_action_set_action_id(): polkit_action_validate_id (action_id)
 Not built with -rdynamic so unable to print a backtrace
bzimmerly@Quad:~$ [/B]

Does anyone have any idea what might have happened? (Thanks!)

---

### Post by quixote on 2009-06-25
No idea, unfortunately, but maybe it's worth trying just a generic terminal-based "fix all packages":```
sudo dpkg --configure -a
```

(Don't get confused, like I did once, and type --reconfigure.  I wound up having to reinstall my whole system.)

Hope this helps.

---

### Post by Bill Zimmerly on 2009-06-27
Thanks Quixote. I tried your suggestion and it didn't fix the problem.

By the way, is it normal for the command you suggested to be done in less than a second?

I'll keep trying to solve this problem and if I do find a solution, I'll post it.

[URL="http://ubuntuforums.org/member.php?u=133668"]
[/URL]

---

### Post by quixote on 2009-06-27
If it finds anything to fix, it takes longer than a second.  Otherwise, it is normal, except in your case you do want it to find the problem, and it's obviously not doing that.

I don't know any useful tips for this situation.  dpkg is powerful tool with lengthy man pages.  It might be helpful to plow through them ("man dpkg", no quotes, in a terminal, but you probably know that).

I had a look at the list in synaptic you mention.  I don't know which repositories you use, but at least in my list I see a few things that could be network / authentication related: cdm, ccrypt, cfengine, checksecurity, cheops.  It might be worth looking through the ones you installed, and either uninstalling the lot, or the ones that look like they might be relevant.  That's a long shot, though.  

Have you tried purging nm-connection-editor and reinstalling it?

When this sort of thing happens to me, I usually just flail around and get frustrated, so I'm not the best person to be answering this!

---

### Post by Bill Zimmerly on 2009-06-29
I'm not sure why this bug manifested itself when it did, but here is a complete report on it...

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214)

I think by using the Synaptic Package Manager AND installing the Edubuntu set, I may have introduced this problem into my system. (Just a guess though.) ](*,)

quixote, thanks for your help - it is greatly appreciated. =D>

---

