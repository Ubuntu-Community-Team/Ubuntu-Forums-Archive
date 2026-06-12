---
title: "Severe Firefox/Opera issues (mostly Firefox)"
date: 2009-01-21
forum: General Help
---

### Post by mrducky34 on 2009-01-21
Hi all, I have tried searching up on Google and the forums, and I have not seen anybody talk about this. Okay, here's the gist of it. I installed Ubuntu 8.10 a few months ago, and I'm not sure how long I've had this problem, but it is really annoying. Firefox is a little slow to start (5-10 seconds, not too bad but I've seen faster) but once the browser loads, it doesn't go to my homepage even though I had set one. If I try to go to a website, for example facebook.com, it leaves that in the address bar. Like the address bar doesn't change to "Http://facebook.com/home" or whatever. If I click a link inside facebook, the address bar doesn't change. It stays "facebook.com". This happens with any website, regardless of what's on it. Also, the menu buttons are disabled (Back, Forward, Refresh, Stop, Home, etc.) even with the F key shortcuts they don't work (I press F5, doesn't refresh). So I am unable to back a page, or forward. Web browsing is also very slow, I tried Opera too but web browsing is VERY slow (not sure if it has anything to do with firefox). I have tried disabling IVP6 in Firefox, does not fix anything. Firefox is usable, but very unproductive. Does anybody know any tips, like reinstalling firefox, or any lines to put into the terminal? It is very hard to get work done like this.

System Specs:
Dell Inspiron 1520
Nvidia Geforce 8400
Dual 2ghz. intel processors

If you need any more information, please ask!

---

### Post by mrducky34 on 2009-01-21
bump

---

### Post by gettinoriginal on 2009-01-21
Personally, I would purge the entire firefox installation and reinstall it. :p

---

### Post by mrducky34 on 2009-01-22
Sorry I'm still a noob at this, how would you go about purging it? I tried using the add/remove thing, but it told me that Firefox can only be removed by some other application

---

### Post by gettinoriginal on 2009-01-22
Go to System, Administration, Synaptic Package Manager, and in the search box type Firefox, when it comes up, check it, a box will come up with options, mark for complete removal.  Then you will have to open a terminal (applications, accessories, terminal and copy paste this:
```
sudo apt-get autoclean
```  I will ask for your password, then hit enter.
When that is done, go back to synaptic, enter Firefox 3.0, and check it for install.

---

