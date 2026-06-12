---
title: "filesystems: wha....?"
date: 2009-06-14
forum: General Help
---

### Post by adpads on 2009-06-14
Hi all,

Here's a curious little philosophy problem for you.

I have a 40 gigabyte truecrypt volume (formatted as ext2) which I created a couple years ago with truecrypt 4.3 under ubuntu gutsy. I have recently moved up to a larger hard drive, and upgraded to jaunty from intrepid. While I was moving all my data around, I decided it was high time to upgrade truecrypt to the current version (6.2), and to make a new truecrypt 6.2 volume to hold my data.

Here's where it gets strange. My old 40.0 GB truecrypt volume claims to contain 38.0 GB of data - but when I copy it off, it occupies 45 GB of hard drive space on my external drive.
To hold precisely the same data, I had to create a new truecrypt volume of 50 GB, formatted as ext3. I copied precisely the same data onto this new volume directly from the old volume, and now it claims to occupy 48.5 GB of space. That's a difference of more than 10GB - fully 27% - for precisely the same data!

Why? Is ext3 really more than a quarter less efficient than ext2?

---

