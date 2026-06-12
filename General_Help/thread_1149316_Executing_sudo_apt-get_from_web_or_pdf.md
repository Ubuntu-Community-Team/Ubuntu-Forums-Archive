---
title: "Executing sudo apt-get from web or pdf?"
date: 2009-05-05
forum: General Help
---

### Post by tommygunner on 2009-05-05
I'm wondering if it is possible when having instructions on a website or pdf file to invoke the terminal. For example, if I have instructions such as: 

> [QUOTE]sudo apt-get install xyz
[/QUOTE]

Can I have this text as a sort of link so that when the user clicks it, it opens the terminal and cuts and pastes it? If so, how is it done. Thank you.

---

### Post by kerry_s on 2009-05-05
it would have to something like this:
**gnome-terminal -x sudo apt-get install xyz **
or
**xterm -e sudo apt-get install xyz **

---

### Post by tommygunner on 2009-05-05
Thanks, interesting. I guess the next step is to look for some sort of plugin for Firefox to do this.

---

### Post by tommygunner on 2009-05-05
Well, I think I figured out a quick solution: apturl. It is a included in Firefox for Ubuntu and can be put in a hyperlink such as <a href="apt:xyz">installname</a> Then when the user clicks it, it trys to install the app.

---

