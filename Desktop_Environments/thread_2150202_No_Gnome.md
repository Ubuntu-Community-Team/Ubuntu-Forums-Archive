---
title: "No Gnome"
date: 2013-05-31
forum: Desktop Environments
---

### Post by oakridge on 2013-05-31
On Wednesday there were some updates, mainly KDE I think, which required a restart.  When I restarted only the blank purple screen appeared although files are available from other machines on the network.  What do I need to do to achieve a proper startup

Thank you.

Malcolm

---

### Post by dino99 on 2013-05-31
which DE is selected when you login ? (unity/gnome-shell/else)
boot in the recovery mode, activate the network, and select "dpkg" to fix the possible package(s) issue(s), and finally select "resume" to continue booting.

---

### Post by oakridge on 2013-06-01
Thank you for your reply dino99.  There will be a short delay in getting sorted because I am doing an extra backup of the data stored on the machine and it is quite slow from a network PC.

You have me a bit foxed with the meaning of 'DE', my old brain cannot get around that one.

Malcolm

---

### Post by oakridge on 2013-06-01
Right, I have done 'dpkg' and some tidying-up and upgrades were carried out, but Ubuntu does not start although files are still available over the network.

Malcolm

---

### Post by houseworkshy on 2013-06-02
"DE" is often used to mean Desktop Enviroment.  If the problem is not seeing one there are command line ways of starting them.  Those commands vary from DE to DE.   My last Ubuntu was 10.04 with gnome 2 so I'm out of date.  Might be worth trying "man gdm" just in case gdm is still there.

   If not or that's invalid advice you could find out from the manual pages even if you don't yet know exactly what command to look for.    

Try "apropos" followed by a word which is probably in the manual pages for the command you will need ( desktop, enviroment, graphic, would be the sort of words I'd guess at first )  and see what gets listed.    
Then try "man" followed by likely commands.   This will describe the commands and show you how to use them.   
When you have the info type in whatever the manual pages have suggested.  You'll need sudo to run whatever the command turns out to be.       

That should get you back to a desktop enviroment ( DE ) otherwise known as a Graphic User interphase ( GUI )  or sometimes less specifically called a user interphase ( UI ) which many don't like as even the command line ( CL ) a windows manager ( WM ) or file manager ( FM ) could be called UI's though they are not complete DE's.  I find acronyms can be more of a memory test than time saver too btw.  Especially irksome when one acromym serves several phrases ...FM ? ....What radio !??

 Easier to post the DE and wait for a specific answer I suppose but that's one, admitedly rather long way round, to get information locally, which is sometimes useful, especially if one has connection problems.

---

### Post by oakridge on 2013-06-03
Thank you 'housworkshy' (I like the name) for your reply.

I am getting depressed.  I have tried everything even 'strartx' which I used to use with Mandriva.  Fortunately the three of us who work from home can still a access the data, but I am in the middle of a very large scanning program which has proved to work best with Ubuntu.  Re-installation is a an absolute, total last resort unless it could be done without starting from factory settings again.

Malcolm

---

### Post by gordintoronto on 2013-06-03
Are you running Kubuntu, Malcolm? Or Ubuntu with Unity, Ubuntu with Gnome, Xubuntu, Lubuntu?

You can probably boot from DVD or a flash drive, and copy essential files to DVD or flash drive. Make sure you have backup! Two copies is a good idea.

---

### Post by oakridge on 2013-06-04
Thank you for your reply gordintoronto.

I am using Ubuntu 12.04 LTS.  The machine gets as far as the Cardinal's purple coloured screen and stops, fortunately the network is fully functioning. I have a rolling backup system using 2 1Tb external drives which hold 6 phased data backups.

Malcolm

---

### Post by houseworkshy on 2013-06-04
I've been browsing around for a solution what may be your problem.  As  you'd mentioned KDE updates I'm assuming your DE is KDE ( this ain't  nessesarilly so as things associated with one DE can go in another, plus  of course several DE's can be installed on one OS ).  It looks like KDE  may have had a bad update.  I searched with terms like "KDE hangs", and  found lots of recent posts here 
[http://www.kubuntuforums.net/forum.php](http://www.kubuntuforums.net/forum.php) 
about  similar sounding post update problems including referances to bug  reports.  Had I found a relevant one marked "solved" I'd have linked to  it, sadly I didn't. Which doesn't mean there isn't one; my search was  far from exhausive.  On a general search I found a few solved posts  about a similar isssue but they were from 2002 and 4 involving, mostly,  slackware users so probably invalid with respect to your machine.

So  the above advice about backing up before fiddling with your system, as  always, is good.  I'd also be inclined to let the big scaning job finish  first too because even though there are problems starting the GUI the  operating system underneath is probably running ok; you can access files  which is a good sign and run commands which is an even better one.

What  to do about it after that?  Well keep an eye on the forums here and at  the one I linked to above.  Once the job is finished you could try going  back to where it worked before via recovery mode.  If it is a bug the  next update may fix it.  

You could install another DE, such as lxde or  razor-qt ( which is a light version of kde with qt so would be quite  familliar ) as a stopgap which you may even wish to keep when all is  well anyway.  When running Kde I often had a light alternate to boot  into if I wanted to do something ram intensive as my machine is a bit  low ram.

You could also post a little more info in the hope of  getting more pertinant help.  So maybe install "sysinfo" and attach it's  report.  Browse around your log files ( with the editor in admin mode  so you can see all of them ) and post bits which may be valid, perhaps  the startup files too.
Good luck with it anyway.  Especially as this  is a working business machine finishing that back up is essential, no matter how slow it is, before doing any tweeking,  operating systems are easily replaceable tools, it's the data and  workflow which are crucial ( well, you know that ).  

Good luck.

---

### Post by oakridge on 2013-06-04
*I am sorry houseworkshy I missed the vital information that I use Gnome. I think you must have just missed my post immediately before yours.*

---

### Post by VMC on 2013-06-04
> **oakridge said:**
> *I am sorry houseworkshy I missed the vital information that I use Gnome. I think you must have just missed my post immediately before yours.*
I think what's confusing people is you mentioned that KDE updates failed, but your running GNOME. Did you add some KDE software to your GNOME os?

---

### Post by oakridge on 2013-06-04
Ah, I see.  The updates were largely related to KDE for some reason, but I use Gnome.  There must be some Gnome software requiring these updates..

Malcolm

---

