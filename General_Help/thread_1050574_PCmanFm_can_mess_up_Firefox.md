---
title: "PCmanFm can mess up Firefox"
date: 2009-01-25
forum: General Help
---

### Post by Xamiga on 2009-01-25
Caution:  If you use 'open folder as root' from pcmanfm and then double click on a file with .html extension and it is opened in firefox your firefox file/directory permissions can get modified to root.  

Subsequently you will not have your old FF configuration availiable nor will you be able to save a new configuration.

your .mozilla directory/subdirectories need to have their permissions fixed.

I don't know what the original directory/file perms were, so from my home directory I did:

chmod -R 777 .mozilla

which got my FF back working:D

Could someone please post the correct chmod lines to get .mozilla and sub-directories back to original.

---

