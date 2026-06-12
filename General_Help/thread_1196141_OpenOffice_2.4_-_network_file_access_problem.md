---
title: "OpenOffice 2.4 - network file access problem"
date: 2009-06-24
forum: General Help
---

### Post by icorbyn on 2009-06-24
Can OpenOffice open/save files on a server?

I'm running release Ubuntu 8.10, OpenOffice 2.4.1 and Samba 3.2.3.  I have files on a Ubuntu 8.10 desktop 'server' that I want to open/edit with OpenOffice from other machines.

When I double click a file on the server, I get the OpenOffice splash screen, then nothing.  
I tried starting OpenOffice Write first, then double-clicking the file to open it, but again nothing.
The network file share does not feature in the OpenOffice File/Open list  - it only presents local files for processing.

The server share is set up to force a user & group with read/write access.  Other applications, like Gimp, have no problem reading and updating files on the server.

Please don't suggest things like 
a.  mounting the share so that it looks like a local folder.
b.  installing software that's not in the standard 8.10 desktop distribution

I'm trying to persuade a local non-profit office to adopt Ubuntu & open source applications - if the OpenOffice suite can't handle networked files in a standard Ubuntu set-up, then please someone say so.

Perhaps this is an OpenOffice issue, not an Ubuntu one?

---

### Post by Arup on 2009-06-24
Why not install OO 3.1 from Scribbler PPA, it updates 2.4 in Itrepid to latest 3.1 seamlessly, it works fine with Intrepid or Jaunty and you have full access to networked files for read or write. [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by LowSky on 2009-06-24
Arup that is great advice, but if upgrading is not availible then try this

1)first launch OOo, then going file--> open, which should work 
or
2)if you mount the shared folder as a local folder this issue should go away aswell, and opening the files like befre should be possible

---

### Post by wsonar on 2009-06-24
I have the same issue kde suse 11 will investigate this

---

### Post by icorbyn on 2009-06-25
Thanks for the replies, but please read my original post - does the 8.10 Desktop/OpenOffice standard install work for file shares on a simple Samba network?  it seems the answer is NO.

I did try the OO 3.x version, but I think that had the same problem, the Open dialogue box didn't list Samba share folders.

"1)first launch OOo, then going file--> open, which should work "  
no, it doesn't - did you try this before posting?

I shouldn't have to mount a shared folder as local so that an application to see it - what's the point of Samba in this case?  Gimp lists shared folders quite happily in its Open dialogue, so it seems that it's not technically impossible.

UPDATE

I was mistaken about OO v3.  This has a different problem with files on a network Samba share.  It certainly displays the shared folder/files in the Open dialogue, but has a problem opening a file, as it thinks that someone else has it open for update (they don't).  You can open as a copy or read-only, but then cannot save, even under a new file name, as OO thinks the user has insufficient rights for this action (it is mistaken).  From the OpenOffice forums, it seems these problems revolve around OO's use of 'dot' temporary files for locking & file security.  The OO support forum entries don't indicate any great progress towards a fix.

---

### Post by technocp on 2009-06-26
as people are aware ubuntu uses nautilus file sharing option. I have experienced that all goes good like copying file from a network share or to a network share from nautilus. I have also experienced that we can open and save files from text editor but saving is not possible from openoffice. finally i have also seen that root user can save the file but not a normal user.
I don't know if any one have solution for this problem

---

