---
title: "How do I get the .iso name from a mounted cd?"
date: 2009-06-03
forum: General Help
---

### Post by JCM3000 on 2009-06-03
I'm trying to mount a cd as an .iso image for a (wine) game to access the cd without it being in the cd drive.  However, to do this I need the **file_name**.iso.  How do I get the file name from the mounted cd?  Sorry if this is a proper newbie question, just in from a night shift and a bit jelly-brained!

---

### Post by col48 on 2009-06-03
A mounted physical cd does not have an iso name any more than the folders in your home directory have a single name.  I think I am right in saying any volume name [not sure if that is the right jargon] is like a sticky label and has no significance for the contents of the CD, although I suppose software might check it for its own ends.

If you have 'mounted' an  iso file as a virtual CD then look at the place in the file system where it is mounted.  In principle it could be anywhere but often it might be /mount or /media.  I think it should also be visible at Places > Computer.

Try a file search (Places > Search for files) for *.iso and hope you'll recognise the name.  For this the iso file does not need to be 'mounted'.

If you need the volume name, it should be visible in the left pane at Places > Computer.

---

