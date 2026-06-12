---
title: "Can't change ownership/permissions of lampp folder"
date: 2009-03-27
forum: General Help
---

### Post by nmgarnett on 2009-03-27
Hi
I've installed lampp in my opt directory and is all working fine, downloded and untarred wordpress and have tried to drag and drop to /opt/lampp/htdocs but I get a message that I don't have permission to do this to any folders in the lampp directory. Permissions for lampp folder show as root. I am a recent convert and love linux but am not very technical so please answer gently?
Thanks
Nick Garnett

---

### Post by Ripose on 2009-03-27
Here is an example, just use your filenames.

In a TERMINAL Window:

 ```
sudo mv /home/Ripose/Downloads/Drupal/webfm /opt/lampp/htdocs/drupal-6.10/sites/all/modules
```Note the space between source & destination directories!

---

### Post by nmgarnett on 2009-03-29
Thanks for this Ripose, works a dream...
Nick Garnett

---

