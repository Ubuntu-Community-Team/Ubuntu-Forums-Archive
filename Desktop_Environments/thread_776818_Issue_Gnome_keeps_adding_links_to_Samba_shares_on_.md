---
title: "Issue: Gnome keeps adding links to Samba shares on my desktop!"
date: 2008-05-01
forum: Desktop Environments
---

### Post by softtower on 2008-05-01
In Gnome I use "Places -> Connect to Server" menu a lot. I access various documents on my Windows-powered server PC, they are samba shares.

Everything works great, but that server has quite a few of shares, and as I navigate through them, Gnome keeps adding endless links to those shares to my desktop. After 10 minutes half of my desktop is polluted  by those stupid links.

Why does it do that? How do I get rid of them forever? Right now I have to manually go through 10-20 of them, righ-click on each one and say "unmount".

How do I make Gnome stop adding them to my desktop?

---

### Post by betes on 2008-05-01
It shows them because for you to browse the samba shares you have to mount them on your local machine.  Here's how you can tell it to not show mounted drives on the desktop.  

alt+f2
gconf-editor
apps > nautilus > desktop
unchek volumes_visible

Some one else can confirm this, but I suppose that the shares will just remain mounted until you log out unless you unmount them from the command line.

---

### Post by Awalton on 2008-05-02
> **betes said:**
> Some one else can confirm this, but I suppose that the shares will just remain mounted until you log out unless you unmount them from the command line.

Or just right-click the share and select "unmount" after you're finished using it.

---

### Post by raziv on 2008-05-10
Hi all,
In my opinion, this is a feature (:-|) worth rethinking.
I am a simple user (means to say, I only go technical when pushed...), and ere are my thoughts reagarding this:

1. Usability: these icons are more of a nuisance than a help.
From my point of view, a shared folder is just another folder, which happens to be on a different box, and so I see no reason for it's and it's many friends' icons to crowd my desktop. They might be regarded as a nice-to-have shorcut, but since they appear only _after_ I got to my destination folder via aonother route, this point is missed.

2. Data integrity: If there is a need for orderly unoumting of such folders, these icons are helpful after all, but are not the best-designed solution.
True, I have already been conditioned, together with the rest of humanity, to unmount a USB removable drive before pulling it out of the plug, like good little children, under the threat (;)) of losing data, so an icon on the desktop for easy access to the unmounting option is actually helpful (as a matter of fact, the Windows "safely remove whatever" tray icon is an elegant solution for this, giving a coherent single access point to "plugging something out").
But,
is there such a need for orderly unmounting of shared folders? (I don't know the answer for this, so if anyone does, I'd be happy to hear it.) If so, then these icons are helpful, but since they are spread all over the place, finding the next free spot on the desktop, they are a poor solution for this need, IMHO. If there is no such need, data integrity is not a reaon for having these icons on the desktop.

Any remarks?
raziv

---

### Post by danlea on 2008-05-10
+1 on this.  In Feisty I could always browse unprotected windows file shares without having to 'authorise' with no password and without mounting the share (at least not to the desktop and nautilus sidebar).

---

### Post by softtower on 2008-05-12
If I were Gnome designer/engineer I'd rather have "Windows Shares" folder mounted somewhere with all samba shares (regardless of where they are) in it. This is what I always do from the command line.

I can imagine how terrible this auto-mounting feature looks in a corporate environment, where you constantly accessing various shares within your company's network.

Also I don't understand why don't they integrate with smbfs? They "mount" these shares onto my desktop, but only gnome sees those shares: ls -a ~/Desktop shows nothing.

---

### Post by Awalton on 2008-05-14
> **softtower said:**
> If I were Gnome designer/engineer I'd rather have "Windows Shares" folder mounted somewhere with all samba shares (regardless of where they are) in it. This is what I always do from the command line.

What's special about "Windows Shares" vs "Ftp Shares" vs "SFTP Shares" vs...? Just how many bins do we need? Maybe I should add some code to network:// to show mounted network shares, dunno? Nautilus doesn't treat mounts separately at all, though; all user-visible mounts are shown on the desktop for the lifespan of their existence unless you toggled the flag mentioned above. And if you have GVFS FUSE, all shares are accessible through ~/.gvfs/.

As to why "ls ~/Desktop" doesn't show them; they're virtual files, just like the trash icon, the home icon and any other drive mounts you may have on your desktop. And once again, we have the option to turn them off at will. 

I admit, we should add more granularity here (show all VFS mounts separate of show all hard disk mounts), but that's for GNOME 2.24; Nautilus is feature frozen and this is a **feature request** not a bug: it's working exactly as it's designed at the moment. 

And yes, there is a need for us to cleanly unmount shares; we do this so we don't keep around stale authentication information, so we don't have to keep-alive internet connections, so we don't crash by accidentally entering into a bad state, poorly emulated underneath of the stateless design (see 80% of GnomeVFS crashes in my experience), etc. We could probably add some code that automatically disconnects shares that are stale to keep desktop pollution down, and add code for automatically connecting to shares on startup, but again, that's 2.24 material.

Please remember: GVFS is stateful. A GVFS file system is either mounted or it is not mounted. When mounted, you will get an icon for the share on your desktop (at your preference), in your Places menu, and in the file chooser, just as you should. This is more consistent with UNIX in general (no flimsy "in-between" states, no guesswork involved, etc), and it's easier on us as support workers (we've had **zero** GVFS crashes reported to us since the release**!!!!!!**, whereas we get about 10 crash reports a day due to GnomeVFS SMB; yes, we still have some functionality to work on, but for most users the every-day work is in place... I know for a fact we have some SMB issues with ADS servers and Samba, and that we don't work on all (S)FTP servers yet, though).

But thanks for the feedback.

---

### Post by raziv on 2008-05-18
Thanks a lot Awalton for the detailed response! It brings me back to my techy question: Regarding what you said:
> **Awalton said:**
> And yes, there is a need for us to cleanly unmount shares; we do this so we don't keep around stale authentication information, so we don't have to keep-alive internet connections, so we don't crash by accidentally entering into a bad state, poorly emulated underneath of the stateless design (see 80% of GnomeVFS crashes in my experience), etc. 
Does this mean that it is recommended for me as a user to manually unmount all SMB shares before, say, I shut down, or log out? In case I don't, is there danger of data loss?

---

### Post by pelle.k on 2008-05-18
> We could probably add some code that automatically disconnects shares that are stale to keep desktop pollution down, and add code for automatically connecting to shares on startup, but again, that's 2.24 material.

Why not do on-demand mounting/unmounting like when i click a share it's mounted until i close the window, unless i explicitly right click "mount share" so that it becomes "persistent" (like now).
I'm so happy i'm not alone in this, i really did like the behaviour in gnome 2.20. Not that i'm not happy with gvfs in general though! :)

---

