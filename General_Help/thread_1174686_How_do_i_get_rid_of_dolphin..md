---
title: "How do i get rid of dolphin."
date: 2009-05-31
forum: General Help
---

### Post by sparky64 on 2009-05-31
I have tried for a while to use dolphin but still don't like it.
I have set konqueror in system settings/file manager and also in file associations/inode/directory.
But some files still open with dolphin when i click on them.
I have tried to delete it but it also removes kde base / konqueror. In fact just about everything needed for kde to run.
To be honest it's behavior on removal is as bad as Internet explorer.:(
Up till now if i didn't like something i could use something else and remove what i don't like, and having it forced on me is starting to get annoying.
I am using 9.04 64bit.
Thanks sparky64

---

### Post by kwd on 2009-06-16
I agree

This is more like the "New World Order's" definition of progress -- Do it my way or else.

Do note that this is a KDE issue thongh--not an Ubuntu issue, so you might want to post this on the KDE forum.

---

### Post by SuperSonic4 on 2009-06-16
> **kwd said:**
> I agree

This is more like the "New World Order's" definition of progress -- Do it my way or else.

Do note that this is a KDE issue thonguh not an Ubuntu issue so you might want to post this on the KDE forum.

I would say GNOME's is far closer to "New World Order" - "Use this and only this. There are no other file managers, shut up"

I'm not sure about the solution, have you tried changing it from the file itself? What kind of programs do this?

---

### Post by kwd on 2009-06-16
sparky64

Well sorry but I don't agree.  I think KDE is much further along the "do it my way" path, although Gnome is working on it.... ;)  So far the only thing I found in Gnome (that Gnome controls) is that you can't remove Evolution.  You can only remove part of it because many of the base elements are integrated with the window manager. Ubuntu does their best to convince you not to use the root account but you can chage that easily if you know how--so I'm not going to fuss about that...

I used Suse and KDE3 for the last 9 years in my job as webmaster (retired now).  I wanted to try Kubuntu because Suse was so slow about fixing things related to home use and I thought I would try KDE4 at the same time.  After 24 hours of Kubuntu and KDE4 I couldn't stand it anymore.  I decided to try Gnome and just load the KDE apps I wanted and so far I am much happier with that than either Suse or Kubuntu.  I am a Power user and spend a lot of time on the command line, a lot of time working as root and do a lot of working remotely on other computers. 


Enough of that, since the people making Linux software are not getting paid (by us) we have no way to insist they do things our way except by not using Linux and I don't want to do that....

***** There were problems with the first solution I posted.  I have re-done the instructions and tested them as best I could.  Everything seems to work now with the new instructions.  If you have problems and need to revert things back to the original you can do that in Settings >> Configure Konqueror >> File Associations >> inode >> directory. If there are problems the Super User version or standard version lanuched with --profile filemanagement either won't start or take forever.  If this happened then start up a version that starts in web browser mode and make the changes there.

On to the SOLUTION I just found:

Assuming that the "main thing" that SuperSonic4 wants to stop is Dolphin from automatically opening folders when you click on them (that's what I wanted), this worked for me:

In Gnome 9.04, start Konqueror, click on a directory while pressing the Ctrl key to highlight it.  Then click on Edit on the main menu and then click on "Edit File Type".  When the dialog opens click on Dolphin and click on the Move Down button untill it is at the bottom.

Then click on the "Embedding"  tab and do the same thing on that page.  

Then click the OK button and you are finished.

In Kubuntu there is a way to do the same thing but I don't know how. You would make changes in what KDE calls file associations, I think... i.e. remove all associations for Dolphin.

Hope this helps

I have a few other problems with Konqueror in KDE4 that I am going to post about on the KDE forums ( [http://forum.kde.org/](http://forum.kde.org/) ).  i.e.:

 1 - Change the "home" icon and the next time start Konqueor it goes away but the other icons on the taskbar work fine. 

 2 - Where are the default CSS files located for Konqueror

 3 - Why did they get rid of the "tree view" style that was used in KDE 3?  It was nice having a lot of different view choices in the old version.  UPDATE -- They didn't, the activation location was just hidden in Settings >> Configure Konqueror >> Views >> Details >> checkbox Expandable folders.

First I have to search for old post that cover the issues above...  User name is Keith there, in case you are interested

---

### Post by sparky64 on 2009-07-21
Sorry for the long delay for reply, Have been working away.
I have tried everything you said here (and what was suggested on the kde forums). and dolphin still occasionally opens up instead of konk.(usually when i click on a file in truecrypt.)
Quote.
"Well sorry but I don't agree. I think KDE is much further along the "do it my way" path, although Gnome is working on it.... " 

One of the reasons i keep going back to kde is the sheer amount of ways to customize it, It's just dolphin that annoys me "why can't i delete it."

At the moment i am using gnome on laptop -with konk as default file manager , Which works every-time, And several kde apps And kde4.3rc on my main desktop. I would have gnome with kde apps on my desktop but compiz interferes with the tv output for some reason whereas kwin effects on basic settings actually improve working.

One last note.
Enough of that, since the people making Linux software are not getting paid (by us) we have no way to insist they do things our way except by not using Linux and I don't want to do that....

All the profits from my isp go towards funding free software.
which is why i do my bit by buying a bigger package then i use.

Once agian thanks for the replys and sorry for the delay in posting.
sparky64

---

