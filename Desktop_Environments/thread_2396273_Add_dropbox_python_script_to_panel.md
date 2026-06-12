---
title: "Add dropbox python script to panel?"
date: 2018-07-13
forum: Desktop Environments
---

### Post by tedthetrumpet on 2018-07-13
The panel indicator for Dropbox is currently broken. Dropbox provide a command line interface

[https://www.dropboxwiki.com/tips-and-tricks/using-the-official-dropbox-command-line-interface-cli](https://www.dropboxwiki.com/tips-and-tricks/using-the-official-dropbox-command-line-interface-cli)

that seems to come down to a python script that runs in a terminal.

This works fine. But, instead of having to launch a terminal and type

~/jsbin/dropbox.py status

every time (that's the location I have the script in), what I'd like to do would be to add an item to the panel that would execute this command in a terminal for me.

Is that possible? How would I do that?

(I'm not very skilled in linux, but should be able to follow basic instructions. GUI solutions preferred where possible!)

---

### Post by speartip on 2018-07-15
Before anyone can answer your question, it would help to give an indication of what flavour & version of 'Buntu you are using.

---

### Post by tedthetrumpet on 2018-07-15
Sorry; This is Ubuntu Studio 18.04

---

### Post by speartip on 2018-07-15
Then I would simply create a Menu Entry. I think Studio is XFCE based, so right clicking the menu icon - edit applications - then create a menu entry using the command in your 1st post, & tick "run in terminal". Then from your menu right click the entry you have made and "add to panel".

---

