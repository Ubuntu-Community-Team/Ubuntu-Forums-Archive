---
title: "Cant find vimrc or gvimrc in your home directory?"
date: 2008-12-04
forum: General Help
---

### Post by Ascenti0n on 2008-12-04
I'm writing this post in the hope that it can help others that may be having the same (minor) difficulties I had finding the configuration files for vim or gvim modal editors.

**Background:**
I have a fresh (not upgrade) Ubuntu 8.10 installation on my machine. I am not a vim dark lord or a CLI (command line interface) guru, but I wanted to learn the basics of vim as a web development editor.

One of the first niggles I had with Gvim is that it always started up with its default theme and I wanted a darker one. The only way to have vim/gvim do this at startup, is to edit the editor's configuration files.

**Problem:**
Searching the forums and Google, you will come across posts which direct you to the .vimrc for Vim or .gvimrc file for Gvim. These files, most will instruct, are supposed to live in your home folder (~/), which was not the case for me, they were not there, not even hidden.

**The solution**
The files can be found at: /usr/share/vim/vimrc and /usr/share/vim/gvimrc

To edit the either of the files above, you would need to type:
```
cd /usr/share/vim/
``` into a terminal. then type ```
sudo gedit .vimrc
```
for example, EVERY TIME you wanted to edit the files.

or

this is what I did:
- open a terminal, type ```
sudo nautilus
```
This will bring up the Nautilus file browser, but with administrator privileges. 
- goto: /usr/share/vim. 
- right click on gvimrc (if you use gvim) or vimrc if you use vim and click 'make link'. This will create a 'symlink' file in the same directory
- Cut and paste it to your home (~/) directory
- select the moved file(s), right click and select permissions
- Select 'read and write' in the selection bar next to 'owner access'. Click the close button. 
- rename the file(s) and add a '.' at the begining of the file name to make it a hidden file. 

This last step is not necessary, but it will keep things consistent for whenever you want to follow any other tutorials/guides/howto's

---

