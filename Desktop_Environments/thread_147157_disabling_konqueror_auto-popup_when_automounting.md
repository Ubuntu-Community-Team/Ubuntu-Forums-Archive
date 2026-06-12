---
title: "disabling konqueror auto-popup when automounting"
date: 2006-03-19
forum: Desktop Environments
---

### Post by vidak on 2006-03-19
I have just found this post on a forum, and maybe others are also frustrated by the windows-like appearing of konqueror when inserting a CD...
Here is the solution to our problem:
You have to comment out some lines in /etc/ivman/IvmConfigActions.xml  (or ~/.ivman/IvmConfigActions.xml) with <!-- --> to look like follows:

  	   <!-- open konqueror -->
  	   <!--
  	   <ivm:Match name="hal.info.category" value="volume">
  	           <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient o
  	   </ivm:Match>
  	   -->

This is the part for konqueror...

Good luck!

---

### Post by Jucato on 2006-03-19
Isn't there an option in the daemon (the one that appears when you put in a CD) at the bottom to "use this choice everytime" or something like that? Then you could choose to "To do nothing" and nothing will popup, right?

---

### Post by vidak on 2006-03-20
[QUOTE=Fenyx]Isn't there an option in the daemon (the one that appears when you put in a CD) at the bottom to "use this choice everytime" or something like that? Then you could choose to "To do nothing" and nothing will popup, right?[/QUOTE]

it is managed by KDED Media Manager, which can be found under System Settings/KDE components/Services, without any configuration options... you can just enable/disable it.. :(

---

