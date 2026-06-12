---
title: "Trouble using editors on mounted samba share"
date: 2005-12-13
forum: General Help
---

### Post by Falc on 2005-12-13
I have a server running Hoary. Among other things, it serves a Samba share which I mount on my Windows box and which works fine.

I also have this laptop I'm working with now, and ever since I did a clean install of Hoary on here, I've been having odd trouble whenever I want to edit files on that Samba share.

I use Emacs as my editor, and whenever I try to save a file to that Samba share, it's sort of like a crapshoot. Sometimes, it saves the file without a problem. As far as I remember, the first save always happens, even. But after that, there's always some point where the save fails for unknown reasons.

What actually happens is that my network card starts flashing it's LEDs like a disco, indicating activity. My cursor also turns into the active one. But the save action never finishes, apparently, and Emacs just hangs completely, requiring a kill -9.

As far as I can tell, Gedit just flat-out refuses to save any file to that Samba share, ever. I'm not 100% sure of this though, since I only ever tested that after Emacs had already failed on me.

I'm pretty sure I have the share mounted with the right permissions. I'm able to do all sorts of stuff to the files on the command line, even piping some output to make a new file on the share. I don't think it's the server's settings, since when I use the share on my Windows box, everything runs fine.

The one thing I do find is that, if I try to use the command line to affect the very file that caused the crash (rm it, for example), I get an error saying that the file is busy. If I ssh to the server though, I can rm it without a hitch.

Now, I'm no expert on the internals of Samba, but I'm starting to think the problem might be that Samba thinks the file is locked so it refuses Emacs' save. Of course, this wouldn't explain why Gedit seems to think the entire share is locked...

So, would anyone have any ideas as to how I might go about solving this?

---

### Post by zoiks on 2005-12-13
I dunno if this is any help but my WAG is that this is a samba bug.  Honestly, though, I have no idea.

Have you tried exporting the same share via NFS as well as samba?  I've found NFS to be smoother (and faster) than CIFS.  Might be a decent workaround, though not as elegant.

---

