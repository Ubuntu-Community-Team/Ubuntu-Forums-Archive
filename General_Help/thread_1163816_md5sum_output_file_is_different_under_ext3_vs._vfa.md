---
title: "md5sum output file is different under ext3 vs. vfat filesystem?"
date: 2009-05-19
forum: General Help
---

### Post by djbarroso on 2009-05-19
Hello all,

     I was backing up some of my files from an ext3 partition to a vfat one. Wanting to make sure that the backup was done correctly, I created an md5sum hash file of the complete directory I was backing up, using the command:

find -exec md5sum "{}" \; > ../md5sum.txt

     I also calculated the md5sum hash file for the new copy in the destination directory (don't ask me why). Then, not wanting to wait some more for the regular check using <code: md5sum -c md5sum.txt>, I thought I might just md5sum the two output files *again*, and compare those. This is when I noticed the two md5sum.txt output files were "different".

     For example, let's assume I have 4 images called: 

          a.png, b.png, c.jpeg, D.JPG. 

     If I do an md5sum hash in an ext3 filesystem, the output will list the files as above. However, if I do the same md5sum hash in vfat, the order in the output listing is changed, like so:    

          c.jpeg, D.JPG, a.png, b.png

     The md5sum hash for each of the four individual files is the same; but, of course, listing them in different orders makes the two md5sum.txt files "different" when *they*, in turn, are hashed. 

     Does anyone know why the md5sum output files are different under different filesystems? Yeah, I know it's kind of trivial and I should just use the regular check (md5sum -c md5sum.txt), but I was just wondering, and hoping someone might know. It isn't logical to me! 

     Thanks!

---

### Post by Polygon on 2009-05-19
im not sure if metadata such as access time, modified/created time would effect a md5sum hash, but if they do, then that would be why.

---

