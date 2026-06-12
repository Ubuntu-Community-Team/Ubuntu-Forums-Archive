---
title: "Newbie network set-up - is this simple set-up secure?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by polarice on 2006-06-19
I now have several PCs with Ubuntu and Windows to network but I'm a newbie, especially to Linux, and I prefer to use the GUI rather than command line.

I found the various guides to networking complicated and eventually have managed to get a network running with bits of info from the guides and a lot of trail and error. I did it as follows but I'd be very grateful if others out there with more knowledge can tell me whether the set-up will be secure. The Windows PCs have ZoneAlarm firewall and the network is behind a broadband router.

I installed samba and smbfs using Synaptic. Then went to Share Folders and set SMB sharing for a specific folder and Allow browsing folders.

My PCs could see the shares on the other PCs but not write to them. So I opened Properties, Permissions for the folders and ticked Group and Other under "Write".

Now Ubuntu could write to Ubuntu shares but Windows could not write to Ubuntu. So (following guidance in Forum posts) I changed the smb.conf file as follows:

; security = user
to
security = share

Now the PCs can all write to the other shares - but is there any security risk or other danger in this set-up?

Thanks!

---

### Post by Luke771 on 2006-06-19
You don't need software firewalls (such as Zone Alarm) if you run your network behind a router.

I'm no network expert so I would need something easy: I would do it like this:
router => internet server => Hub => clients

the internet server can be an old PC with two network adapters, one to the router and one to the hub where all the PCs are connected.

On the internet server, I would run Linux off a LiveCD (even Ubuntu, why not) that way as soon as you have the slightest suspect that someone is trying something, all you have to do is reboot the server and all will be reset.

You want to store your server settings on a USB drive, launch the Live CD on the server, load your settings and disconnect the USB drive.


It's only an idea, I never actually built something like that because I only have one PC

Anyway, one thing is for sure, you dont need all those Zone alarm things (but that' a Windows topic, not Ubuntu, so I stop there)

---

### Post by polarice on 2006-06-19
Perhaps I wasn't clear about my set-up. It's based on what I used when I only had Windows PCs - the connection comes into the router/hub and then simply radiates out to several desktops (no separate server involved). Perhaps I should have titled this thread "Newbie files sharing set-up..." rather than "Newbie network set-up" because that's what I am more concerned about.

I had added Ubuntu Breezy and just got set up before Dapper appeared. On Breezy I found it very easy to set up file sharing using Nautilus-share. But when I tried to upgrade to Dapper the Nautilus-share seemed to cause a big problem and the upgrade was unsuccessful.

I installed Dapper instead of upgrading and didn't use Nautilus-share again because (a) it caused the upgrade problem and (b) there isn't (I think) a version for Dapper. So I tried to find a simple way to set up file sharing.

---

