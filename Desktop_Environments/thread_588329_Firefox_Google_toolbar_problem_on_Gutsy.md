---
title: "Firefox Google toolbar problem on Gutsy"
date: 2007-10-23
forum: Desktop Environments
---

### Post by przyswa on 2007-10-23
Hi

On my new installed machine with Ubuntu Gnome Gutsy the Google toolbar on Firefox doesn't display my bookmarks any more !?

I tested on other machine with the live CD but it's the same.

Any ideas ?

Sam.

---

### Post by dilney on 2007-10-24
That happened to me too.

The funny thing is that Google Bookmarks work perfectly in Swiftweasel (which is a different build of firefox optimised for each processor).  I just switched to Swiftweasel and everything works fine.

You can find Swiftweasel here: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

Dilney

---

### Post by przyswa on 2007-10-24
Thanks for the info, but what graphic card did you use ?

Did you use any effect, me no, my graphic card do not permit it.

I think the bug come around the graphic setup...

Sam.

---

### Post by przyswa on 2007-10-24
> **dilney said:**
> That happened to me too.

The funny thing is that Google Bookmarks work perfectly in Swiftweasel (which is a different build of firefox optimised for each processor).  I just switched to Swiftweasel and everything works fine.

You can find Swiftweasel here: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

Dilney

I tried Swiftweasel compiled for my processor (Pentium 4) but I have the same problem :( and the french Firefox language is not applied on this browser.

Sam.

---

### Post by cube3x3 on 2007-10-24
Hi Sam,
Is ur machine 64 bit? if it is then google bookmarks in toolbar wont work.
Same problem with me at now, all the machines i m working on are 64 bits.. :(
So there are two solutions for this:
1. Install a 32bit firefox - there is some trick to do that, i never tried it though.
2. Use the GBookmarks extension on firefox. check it here: [https://addons.mozilla.org/en-US/firefox/addon/2448](https://addons.mozilla.org/en-US/firefox/addon/2448)

I am using 2'nd one, and its working very nicely for me.
Let me know if u have any problems...

---

### Post by anarion on 2007-10-24
Same problem here.
I'm using Ubuntu 7.10 totally updated on a Dell Pentium M 1.73Ghz laptop.

---

### Post by rened on 2007-10-26
Swiftweasel firefox solved problem for me , I am working on 32bit pc , thank's for tip .

---

### Post by Lang on 2007-10-27
I have had the same problems. I installed Gutsy, firefox and Google toolbar.Now the bookmarks just hangs saying downloading bookmarks. Plus firefox turns grey and freezes quite often. Is it the toolbar, firefox or Gutsy? What should I do?

---

### Post by chang47 on 2007-11-05
Here's another with the same saying downloading, but nothing happens.  I've since gone back to Feisty as language support is also not working for me.  Scim is broken too.

---

### Post by uconvert on 2007-11-07
I had the same problem with the Gusty/Google Bookmarks. I found the the solution:)

On  the Google toolbar click on Settings-Options-Restore Defaults.

It worked for me

Good luck

I love the Gusty  Gibbon on my ASUS Z62FM Notebook! Ubuntu Rocks:guitar:

---

### Post by tlayton_at_work on 2007-11-07
Not sure if I had the bookmarks issue, but the Google Toolbar would cause Firefox to freeze whenever more than 2 windows were open.  I uninstalled it, and now Firefox is fine.

Regarding the bookmarks, I've been using the Google Browser Sync extension.  Been working fine so far.

---

### Post by sandorf on 2007-12-10
Same problem here on Gusty
'restore defaults' doesn't work for me
looking for a simple solution...

---

### Post by maartends on 2007-12-20
Same here, 'restore defaults' doesn't solve the problem for me!

---

### Post by flauros on 2007-12-23
As cube3x3 said, bookmarks don't work. You should use this ([https://addons.mozilla.org/en-US/firefox/addon/2448](https://addons.mozilla.org/en-US/firefox/addon/2448)) addon for firefox which adds a menu with google bookmarks. At least that's what I read: I'm on 32bit.

If you have a 32bit just like me, I found the solution in this forum (this thread to be exact: [http://ubuntuforums.org/showthread.php?t=581048](http://ubuntuforums.org/showthread.php?t=581048)).
You just have to download and install the standard C++ library.
You can use Synaptic: look for libstdc++5 and install it.

Anway, if you have already installed Google Toolbar it won't work.
You have to uninstall it (it should be on "Settings -> Help -> Uninstall" or something like that: mine is in Italian) and re-install it.
Uninstalling the toolbar before or after installing the C++ library won't make an difference.

Unfortunately this doesn't fix the spelling check in other languages. It looks like it works in English only. **

Bye!

** EDIT: It works: you have just to disable Firefox's spell check. If both of them are enabled it looks like only Firefox's one can work.

---

### Post by penchantforevil on 2007-12-27
Flauros,
This worked perfectly for me...using Hardy Heron alpha 2.
Thanks!

---

### Post by flauros on 2007-12-27
> **penchantforevil said:**
> Flauros,
This worked perfectly for me...using Hardy Heron alpha 2.
Thanks!

You're welcome and glad to see that it will work on Hardy Heron too...
oops... did I spoke too early?:lolflag:
Bye!

---

### Post by Crazy Jesus on 2008-01-08
> **cube3x3 said:**
> 
[B]2. Use the GBookmarks extension on firefox. check it here: [https://addons.mozilla.org/en-US/firefox/addon/2448](https://addons.mozilla.org/en-US/firefox/addon/2448)
[/B]

Just chiming in to say thanks for that link, I was having the same problem until I installed that. :)

---

### Post by SamHane on 2008-01-08
I had same problem with Firefox and Google toolbar. Only reason i actually needed toolbar was those bookmarks. Then i found this addon 

[https://addons.mozilla.org/en-US/firefox/addon/2888]("https://addons.mozilla.org/en-US/firefox/addon/2888")

I've been using it few days on my 64bit Ubuntu machine and pretty happy with it.

---

### Post by bmk789 on 2008-02-11
I had tried the restore defaults in the toolbar settings and even tried installing swiftweasel but neither would work.  The only way I have gotten it to work is with flock.  Can't wait for a fix, I'd much rather use Swiftweasel

---

### Post by rajeshgautam on 2008-03-03
I am using 64 Bit Gutsy and I had same problem with Firefox and Google toolbar.

Both GMARKS and GBookmarks fix the problem. However GMARKS is better as it allows you to add your notes while adding bookmark. 

A HINT:  GMARKS does not show the existing labels as pulldown menu in its ADD-BOOKMARK  Window. In order to add a bookmark in an existing tag DO NOT use Add/Edit entry in GMARKS's pulldown menu. Rather, from the pulldown menu of GMARKS, right click on the desired (existing) tag, you will see an "add bookmark here" option.

GMARKS    [https://addons.mozilla.org/en-US/firefox/addon/2888](https://addons.mozilla.org/en-US/firefox/addon/2888)

GBookmarks [https://addons.mozilla.org/en-US/firefox/addon/2448](https://addons.mozilla.org/en-US/firefox/addon/2448)

---

