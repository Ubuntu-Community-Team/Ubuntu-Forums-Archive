---
title: "bad interpreter: no such file or directory"
date: 2009-06-12
forum: General Help
---

### Post by siyangqiu on 2009-06-12
I have been trying to get a form up for my server that sends an email to me when someone hits submit. I found a perl script online called form2email.pl. When i tried it, i get 500 internal server error. I decide to try the script directly from terminal. it says that /usr/bin/perl can't be found "bad interpreter: no such file or directory". I went there can checked. there is something called perl there. I also tried sudo apt-get install perl. It said mine is already installed and up to date. whereis perl comes up with that same location. does anyone know why this is happening?

---

### Post by blueridgedog on 2009-06-12
After you get the 500 error, tail (as in look at with the tail command to see the end of the file) the apache error log file on the server for more information on the error.

---

