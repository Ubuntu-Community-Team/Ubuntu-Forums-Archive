---
title: "problems with OpenArena game."
date: 2007-10-16
forum: Gaming &amp; Leisure
---

### Post by dany_tab on 2007-10-16
I cant enter a server in multi player game.

I tried 4 servers:
first server: invalid game folder
2nd server: client/server game mismatch:
                    baseq3-1/defrag-5.
3rd server: client/server game mismatch:
                   baseq3-1/baseoa-1.
4th server: invalid game folder.

I tried to reinstall the game but it doesnt help.
there is a way to fix it??

---

### Post by chuckyp on 2007-10-16
I've experienced the same issues with the gam.  I think a lot of it has to do with different versions running on server / client.  Its really annoying being able to only play on approximately 3-4 servers.

---

### Post by dany_tab on 2007-10-16
i am playing with bots because i cant enter the servers

---

### Post by dany_tab on 2007-10-16
someone has a suggestion how to fix the problem?

---

### Post by linuxlizard on 2007-10-16
The packages in Ubuntu's repositories are often old and out of date (frozen at release dates I guess).

Try the package from this site. This is a great site and they keep their packages up to date:

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by disturbedite on 2007-10-16
you failed to mention which version you are using.  i was also gonna recommend installing the 0.7.1 packages from getdeb since they are the latest version, but as you can see linuxlizard beat me to it.

---

### Post by dany_tab on 2007-10-16
yes it works. i installed the newest version.

---

### Post by kinkdxm on 2007-10-27
> **linuxlizard said:**
> The packages in Ubuntu's repositories are often old and out of date (frozen at release dates I guess).

Try the package from this site. This is a great site and they keep their packages up to date:

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)


they don't seem to have open arena on there anymore
:(

---

### Post by Alex Carroll on 2007-10-27
> **kinkdxm said:**
> they don't seem to have open arena on there anymore
:(

They do, but currently there doesn't seem to be a Gutsy variant.

---

### Post by Anafiel on 2007-11-05
> **Alex Carroll said:**
> They do, but currently there doesn't seem to be a Gutsy variant.

I assume then that I shouldn't install the fiesty package on my gutsy machine??

(ubuntu newbie type question...please be kind)

Anafiel

---

### Post by mogi on 2007-11-06
Download any OpenArena 0.7.1 patch and extract pak7-patch.pk3 to /usr/share/games/openarena/baseoa/ directory. Check the file permission and make sure it can be read by ordinary user. Enjoy!

---

### Post by jsbarnes1002 on 2007-11-25
How can I tell which version I'm running?  I downloaded 0.7.0 plus the patch and put them in /usr/local.  But I also have openarena in /usr/shared.  Which is the version that is installed?

---

### Post by tarehart on 2007-12-30
I spent a long time confused with this problem because I assumed my package manager was at least fetching me 0.7.0. That wasn't true, though, it was giving me version 6, and the 0.7.1 patch does nothing to remedy that situation.

Here's a link to the proper getdeb page, which includes gutsy variants: [http://www.getdeb.net/app.php?name=OpenArena](http://www.getdeb.net/app.php?name=OpenArena)

Alternately, you can go here -
[http://www.moddb.com/downloads/7803/openarena-070-win32linux-i386-zip](http://www.moddb.com/downloads/7803/openarena-070-win32linux-i386-zip)
to get 0.7.0 and then follow mogi's instructions for the patch.

---

### Post by suitedaces on 2009-03-08
Might be an idiotic question, but how can my friend on windows see 121 servers, and I have only 12 complete;y different servers available to me on ubuntu? I installed mine using add/remove.

---

### Post by 5nak3 on 2009-03-11
Go to the open arena website, download the latest version, I think it is 0.8.1.

Extract the file into your home drive, and then double clicking on the openarena.i386 file should launch the game for you with access to the new arenas :)

You can also make a link of that file to your applications -> games menu list if it makes it easier.

And if you want to hide the openarena folder in your home folder just rename it to .openarenaxxx instead of openarenaxxx (where xxx stands for whatever is the latest version)

Hope that helps.

---

### Post by suitedaces on 2009-03-17
Perfect, thanks!

---

