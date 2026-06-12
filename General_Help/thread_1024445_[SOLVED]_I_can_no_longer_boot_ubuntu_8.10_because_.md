---
title: "[SOLVED] I can no longer boot ubuntu 8.10 because of ccsm"
date: 2008-12-29
forum: General Help
---

### Post by eldonciv777 on 2008-12-29
I installed ccsm and was playing with the settings under the "ultimate" tab.  After clicking on one of the settings my desktop immediately freaked out.  It is super scrambled and indistinguishable.  When I boot it is fine at the user login page but after that it gets ugly.  It comes up all scrambled and flashes and eventually goes back to the login screen (after about 5-10 seconds).

I tried uninstalling and reinstalling ccsm via the safe boot terminal, but it doesn't help.  I also tried a method or two to restore the defaults via a terminal but that didn't work either.

Any suggestions on how to make it restore to default settings?

---

### Post by LordSmight on 2008-12-29
Try booting into Ubuntu via recovery mode and see what you can do from there. 
I would suggest going back to the CCSM setting you changed and try changing it back to it's default.

---

### Post by wmoore on 2008-12-29
When at the login screen login as normal, then immediately press ALT + F2 to go to a terminal logon. Logon as yourself, then type
```
ps ax | grep compiz
```You should get a response something like```
 5471 ?        S      0:00 /bin/sh /usr/bin/compiz
 5536 ?        S      2:30 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering core ccp
13956 pts/0    S+     0:00 grep compiz
```note the numbers in the first column. Now type the following line, replacing the numbers with those from your command output:
```
sudo kill 5471 5536
```This should kill Compiz and leave you with a standard desktop - press ALT + F7 to get back to it.

---

### Post by angrez on 2008-12-29
I had the same problem last week. I tried all methods until I had to create another temporary account from fail safe terminal and from there i switch to my default.

---

### Post by eldonciv777 on 2008-12-29
> **wmoore said:**
> When at the login screen login as normal, then immediately press ALT + F2 to go to a terminal logon. Logon as yourself, then type
```
ps ax | grep compiz
```You should get a response something like```
 5471 ?        S      0:00 /bin/sh /usr/bin/compiz
 5536 ?        S      2:30 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering core ccp
13956 pts/0    S+     0:00 grep compiz
```note the numbers in the first column. Now type the following line, replacing the numbers with those from your command output:
```
sudo kill 5471 5536
```This should kill Compiz and leave you with a standard desktop - press ALT + F7 to get back to it.

I tried this.  The output reads:
5374   tty2    S+      0:00 grep compiz

The 5374 isn't constant either because I checked it probably 5 times and it kept going up by one or two each time.  The last time I checked it it was at 5385.  I tried to kill it at that decimal but it gave me an error.

So I could would just create a new temporary account.  How did you fix it from there?  replace the settings files in the original users compiz directories?

---

### Post by wmoore on 2008-12-29
> **eldonciv777 said:**
> I tried this.  The output reads:
5374   tty2    S+      0:00 grep compiz

The 5374 isn't constant either because I checked it probably 5 times and it kept going up by one or two each time.  The last time I checked it it was at 5385.  I tried to kill it at that decimal but it gave me an error.

So I could would just create a new temporary account.  How did you fix it from there?  replace the settings files in the original users compiz directories?OK, have a read of [this post]("http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/?referer=sphere_related_content/") and see if that helps. Normally I would not remove the config files as suggested but most likely just rename the files.

So instead of```
rm -rf .gconf
```I would use ```
mv .gconf .gconf.old
```And similar for the other folders listed in the article.

---

### Post by ellalan on 2008-12-29
Try deactivating the "magnifier" plugin in ccsm.

---

### Post by eldonciv777 on 2008-12-29
> **wmoore said:**
> OK, have a read of [this post]("http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/?referer=sphere_related_content/") and see if that helps. Normally I would not remove the config files as suggested but most likely just rename the files.

So instead of```
rm -rf .gconf
```I would use ```
mv .gconf .gconf.old
```And similar for the other folders listed in the article.

Thanks......it worked like a charm.:D

---

