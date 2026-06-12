---
title: "WYSWYG HTML Editor"
date: 2005-08-25
forum: Desktop Environments
---

### Post by alquimista on 2005-08-25
Hi,
I was happy migrating from WinXP to Kubuntu; the problem is that I got a new client project that requires a powerful visual document editor that allows me to save the document in HTML.
I know that OOffice 2 comes with these features, yet I see that is in Beta version and not recomended for production environments; that I know since playng with version 1.9.112  I lost a couple of Write files that OOffice could not recover.

My documents require lots of tables, autonumbering (indented), lots of links, diagrams with linked elements. MS Office provides me all that, the problem is that it generates wired HTML that can only be viewed in MS Explorer and not in Mozilla Firefox for example. I could go for CrossOver and MS Office 2000, yet I have 256 MB Ram and performance is not good. 

Do you recomend me any Open Source Linux software that provides me what I need? I don't want to go back to Win  :| 

Thanx!
Guillermo

---

### Post by SqdnGuns on 2005-08-25
This will do it...................it is in the repositories too.

[http://www.nvu.com/](http://www.nvu.com/)

---

### Post by xequence on 2005-08-25
Nvu is a simple one. I dont know if it has enough features for you but you can try it out. As for your RAM, I have 191 MB RAM and it works good in gnome but its a little slow in KDE.

EDIT: Opps, I went to the reply button before that post was made and didnt see it... Oh well :P

---

### Post by One Quick Question on 2005-08-25
Which repositories?
(I have universe and multiverse enabled, I don't see it)

---

### Post by SGC on 2005-08-25
[QUOTE=One Quick Question]Which repositories?
(I have universe and multiverse enabled, I don't see it)[/QUOTE]
 Backports repository

---

### Post by f1dave on 2005-08-26
Yeah... i've got a backports repo enabled, but I can't find it either. What repo are you using for backports?

---

### Post by Mishura on 2005-08-26
Quanta can do WYSIWYG.

Oh and my backports repo:

```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted bleeding
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted bleeding

```

---

### Post by f1dave on 2005-08-26
Yep thats mine, and no nvu :(

But yeah, i've got quanta so maybe i wont need to worry.

---

### Post by Kuolio on 2005-08-26
Inspired by this thread and a need for a easy&fast HTML/CSS editor, I aptitude installed NVU. It was installed just fine, but when i try to run it I get this:

/usr/lib/nvu-1.0PR/run-mozilla.sh: line 159:  4323 Muistialueen ylitys     "$prog" ${1+"$@"}

And then it stops. Nothing more happens, nvu wont start, no more error messages. Oh, btw, that "Muistialueen ylitys" is finnish, and says something like "memoryarea overflow" in english. 

If you have any suggestions, that would be great. I'm runing amd64 version, if that has anything to do with this.

---

### Post by Mishura on 2005-08-26
Hmm.. when I did a search for nvu in Synaptic (Just to see if it actually was there..) I saw that there was no information (No versioning, no nothing except description.).   When I right click and do "properties"... I see that its 0.99+1.0pre1... This may not be the backport version, but a alien-ized version or a Debian .deb that i used to run.. but I can't remember.

Aha!  Here you can get it:  [http://autopackage.org/packages/](http://autopackage.org/packages/)
As you can see from URL, its an autopackage.  If you have a problem with that* then I guess you can get the tarball from Nvu's site.  


*Some people seriously object to autopackages and prefer doing eveything "The debian/ubuntu way".  I personally don't care.   Use what you feel is right/works.

---

### Post by adriantry on 2005-08-26
[QUOTE=alquimista]Hi,
I was happy migrating from WinXP to Kubuntu; the problem is that I got a new client project that requires a powerful visual document editor that allows me to save the document in HTML.
I know that OOffice 2 comes with these features, yet I see that is in Beta version and not recomended for production environments; that I know since playng with version 1.9.112  I lost a couple of Write files that OOffice could not recover.[/QUOTE]

OpenOffice 1 can do that, too!

---

### Post by blackant on 2005-08-26
[QUOTE=f1dave]Yep thats mine, and no nvu :(

But yeah, i've got quanta so maybe i wont need to worry.[/QUOTE]
I am having the same problem.. couldn't find it. :(
I download nvu from the official site but don't know how install. :(

---

### Post by Mishura on 2005-08-26
Assuming you have KDE, open it up in Konqueror (The tarball).

Copy the NVU folder to your home directory.

Go to your NVU directory and right-click on "nvu".  Click properties and hit the permissions tab.  Click on exectuable.

Click on nvu and have fun.

---

### Post by blackant on 2005-08-27
[QUOTE=Mishura]Assuming you have KDE, open it up in Konqueror (The tarball).

Copy the NVU folder to your home directory.

Go to your NVU directory and right-click on "nvu".  Click properties and hit the permissions tab.  Click on exectuable.

Click on nvu and have fun.[/QUOTE]
hmm.. I am using gnome. :(
How do I install it?

Thanks.

---

### Post by Mishura on 2005-08-27
OK.  We'll do it the Terminal way (I am not too familar with Gnome).

Open up your favorite Terminal app.  (Eterm, Gnome Terminal, Xterm..)

* Make sure you get the tarball that was built on Linspire 5.0.  This package has the closest compatibility to Debian and Ubuntu.  The others are for Fedora and Suse, I believe.

```
cd /path/to/nvu-1.0-pc-linux2.6.10-gnu.tar.bz2
tar -jxvf nvu-1.0-pc-linux2.6.10-gnu.tar.bz2
mv nvu-1.0 ~/nvu
```

That above, extracts the tarball and copies the folder to your home directory.  Location: /home/username/nvu

To use Nvu.. just:
```
cd ~/nvu
./nvu
```

If you want to disregard the terminal every time you want to use it, I suggest making either an icon on your desktop, or a Menu entry (If possible in Gnome).  Just have the icon/menu entry point to ~/nvu/nvu.

Thats it.  Hope it helps.

*If not, click here: [http://ns2.syntomax.com/~hp/nvu-1.0.0.x86.package](http://ns2.syntomax.com/~hp/nvu-1.0.0.x86.package) and get the autopackage installer.

---

