---
title: "OpenOffice with some Windows systems"
date: 2008-03-04
forum: Desktop Environments
---

### Post by ckollars on 2008-03-04
I'm trying to set up a Gutsy Gibbon system. It will go into a mongrel environment where some of the clients are Windows while all of the servers are some flavor of Linux. Users home directories are on the network; more specifically they're served by Samba configured with "unix extensions = no". 

With their single home directory users will sometomes use Ubuntu and other times use Windows.  So I need the OpenOffice config data (not the documents) usable both on Linux and on Windows. Most obviously, I can't have the Ubuntu systems create any "symlinks" because the same home directory will later be used on a Windows machine which wouldn't have any idea what to make of the symlink. (Note my question is _not_ about "document compatibility". It's about the non-document data in ~/.openoffice.org2.)

My Gutsy Gibbon system uses a "cifs" mount, simply because the Samba team is transitioning everyone away from smbfs and dropping support for it. Yet my mount is effectively still an old-style smbfs mount; "unix extensions" are turned off (I've tried turning them off on both client side and on server side, it makes no difference.)

How can I get OpenOffice to understand that "cifs" doesn't necessarily mean "unix extensions"? Is there some configuration parameter I can use to force OpenOffice to act as though it were running on a Windows system?

---

### Post by ckollars on 2008-03-13
After much frustrating asking and searching and grokking source code and "truss" tests, I eventually came up with what seems to be a solution. Here's what seems to work for me, interspersed with my theories as to why it works:

The only significant difference between an SMB file system and a *nix file system is the SMB file system's inability to handle symbolic links. Preventing OpenOffice from creating any symlinks will effectively allow it to run on an SMB-mounted home directory. 

The assumption that symlinks exist and the ability to create them are compiled right into the Linux version of OpenOffice.; the same compile-time options that turn on Linux compilation also turn on use of symlinks. Symlinks are so integral there appears to be no way to capture them or modify them. The only solution is to keep OpenOffice from thinking it needs to create a symlink in the first place. 

The main place OpenOffice creates symlinks is inside a new ~/.openoffice.org2. These configuration files are copied from a "template" (which exists in something like /usr/lib/openoffice/presets). If there are symlinks in the original template, OpenOffice will attempt to create similar symlinks in the per-user config copy. Conversely, if there are *not *symlinks in the original template, OpenOffice will *not *attempt to create symlinks in the per-user config. 

So to get the Linux OpenOffice to run without creating symlinks, what's needed is to legitimately get rid of all the symlinks in the template. Links are pretty easy to locate with `find` (there are twelve of them:-). They can't just be deleted though. Rather. they need to be replaced with the actual contents (and mtime) of what they used to point at. I constructed a small bash script to "unsymlink" a file, replacing a symlink by a copy of what it used to point at. (My script was pretty dumb and can be reconstructed easily. The only reason I used a script rather than doing the operations entirely manually was that manually replacing *12 *links would have taken too long and been too error prone.)

Once symlinks were legitimately removed from the OpenOffice configuration template in this way, OpenOffice came up and ran fine  ...even though the home directory was SMB-mounted.

---

