---
title: "Problem with install Chinese Input on Ubuntu8.10"
date: 2009-01-20
forum: General Help
---

### Post by flylehe on 2009-01-20
Hi,
I am following the instructions on "http://ccat.sas.upenn.edu/~nsivin/chinp.html" but get the error in the final step. All the steps are as: 

1. change settings in the "System, Administration, Language Support" and the OS download and install various needed files; 

2. type in terminal "locale | grep LANG=" and get the proper abbreviation for my default language "LANG=en_US.UTF-8";

3. type in terminal "sudo apt-get install scim-qtimm im-switch scim-pinyin" and the OS will then download the file and install it; 

4. type in terminal "m-switch -z <en_US.UTF-8> -s scim" but now get error "bash: en_US.UTF-8: No such file or directory". 

What's wrong with Step4? Or other better ways to install the Chinese input method? Thanks for help!

---

