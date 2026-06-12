---
title: "Multiple entries in amaroK"
date: 2006-02-22
forum: Desktop Environments
---

### Post by f1dave on 2006-02-22
Hey everyone,

I chose to start this thread because searching didnt find me much. Basically, I have a situation where all my amaroK statistics have duplicate entries- for example the following:

(see attachment)

etc. You get the point.

Now the thing is, these are all the same file- there's no multiple copies of the same song or whatever. I'm using the latest SVN version of amaroK, and it's kind of an annoyance as opposed to a problem, but even so I hate annoyances :D

I have a feeling amaroK builds some kind of database somewhere, and it is possible this could have for some reason have duplication within it. However, I'm not sure and would like to know from others who may have had this problem, or even if they have managed to fix it!

---

### Post by dcer on 2006-02-22
You could try Tools -> Update library and then Playlist -> remove duplicate and missing entries

I hope the above are translated right, I don't have an english version.

I never had this problem, but I assume the file either changed or you moved it.

---

### Post by f1dave on 2006-02-22
I appreciate the suggestion, but believe me I've tried many such things. Afaik, the remove duplicates only applies to the playlist (which never has duplicates for me anyway) and not the statistics/recently played/etc. 

The files have not been moved or changed in any way that I am aware of- they sit on my windows ntfs partition, which means that of course no linux program can write any changes.

---

### Post by dcer on 2006-02-22
You could try to purge the statistics by reinstalling. Don't know if it would work though.

---

### Post by f1dave on 2006-02-22
Unfortunately, this is yet to work for me when I use the SVN version.

---

### Post by Kubureaucrat on 2007-11-08
I have this problem in a big way

it especially seems to happen w titles i have encoded myself, though the duplicates don't show up right away; they show up some time down the line.  meanwhile though there are no duplicate *files* just duplicate entries in the amarok context database.  and if i "delete file" one of the duplicate entries through right click context menu, both entries disappear.  clearly the database is somehow referring to the same file twice.

puzzling ---

(now in kubuntu i386 gutsy, but same was true in feisty.  i think also dapper though not sure)

---

### Post by agentaaron on 2007-11-14
I am having this same problem, Has anyone found a fix yet? 

P.S. Im using 7.10 Gutsy

---

### Post by b8sell on 2007-12-13
I've seen this behavior with Amarok many times and not just in Gutsy.  Usually whenever I do something a little creative with the library (move some files around, rename some files outside of the Amarok interface, allow Amarok to auto-detect new files, etc.) I get the dreaded "multiple entries" bug.

I've even seen quadruple entries when I've had double entries that doubled again.  Annoying.

The fix is pretty simple and almost always works, but it takes a while to resolve itself (depending on the size of your library).  Try:

Tools -> Rescan Collection

This holds true for almost every version of Amarok I've tried and it's been true across multiple flavors of linux.  Has anyone tried fixing this directly in the database?


> **agentaaron said:**
> I am having this same problem, Has anyone found a fix yet? 

P.S. Im using 7.10 Gutsy

---

### Post by Lostincyberspace on 2007-12-13
Have you checked (or double or triple checked) to make sure you don't have the extra on the computer. Also have you tried using mysql or postgre sql instead sqllite?

---

### Post by FrooziE on 2008-05-27
In my case the double entries are only added when I move or copy files to my collection. I've found that RESCAN COLLECTION solves the problem every time, however that's not really a solution when one has an expansive library. I am currently on:

Ubuntu 8.04 64bit GNOME
Amarok 1.4.9.1 w/ MySQL 5.0

The version of Amarok I'm using is the one from the Medibuntu repos, but I don't think it matters as the problem occurred before the update with the one from the Ubuntu repos as well.

I dragged the most recent album to fall victim to the bug into a new playlist and checked the file info for each file. It seems the only difference between the doubles was that the path pointing to the file in my library was uppercase in one and lowercase in the other for ARTIST INITIAL. There was ONLY ONE FILE. Aside from the ARTIST INITIAL the path was identical. Really weird.

---

### Post by svigeneris on 2008-06-05
Incidentally, I'm having exactly the same problem: one folder is listed in Caps, and the other in lowercase letters. It's only happening to a select number of albums, though.

Rescanning the collection seems to solve the problem (though it's quite time consuming), but chances are in a couple of days the same problem's going to surface. Any ideas if there's a quicker fix, or if this bug's been reported to the relevant developers?

---

### Post by thedaylights on 2008-06-08
An interesting quote from the mysql for amarok tutorial: 

> Older versions of Amarok may work best with MySQL versions < 5.0. One known problem as a result of this is Amarok's DB continually growing and adding multiple entries for every track on each rescan. 

If you are running MySQL as your database, you might want to look through that guide if you haven't already:
[http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)

---

### Post by FrooziE on 2008-06-12
After adding my USB hard drive to fstab the problem went away. Once the drive had a fixed mount location it stopped adding double entries. The only problem with that is if i turn off the drive, i then have to reboot to be able to mount it again. I moved all my music to my my internal drive and now i don't have to deal with it anymore.

---

